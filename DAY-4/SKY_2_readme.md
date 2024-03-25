#  SKY130_D4_SK2 -Timing analysis with ideal clocks using openSTA
##  Topics to be covered
**--> Setup timing analysis and introduction to flip-flop setup time**   
**--> Introduction to clock jitter and uncertainity**  
**--> Lab steps to configure openSTA for post-synth timing analysis**    
**--> Lab steps to optimize synthesis to reduce setup violations**    
**--> Lab steps to do basic timing ECO**    

## Setup timing analysis and introduction to flip-flop setup time

Typical Ideal clock scenario to identify setup time.   
**Setup Time -->** Setup time is the minimum amount of time before the clock edge that the data input
must be stable and not change to ensure correct data is latched by the clock edge.   
**Hold Time -->** Hold time is the minimum amount of time after the clock edge during which the data
input must remain stable after the clock edge has occurred.   

Ideal clock network : the clock tree is not yet build.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/63308581-2598-47bc-bad5-f81afa1e04cf)
The data should reach capture flop within the time period.   
This below picture says it will operate at 1Ghz frequency.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f42f9007-358b-496e-8680-6ad178bc30df)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3b32c2a9-a0d1-49dc-9d36-79be4ceb733f)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3a41ded1-cf58-477a-901c-d5945f00a1b7)

## Introduction to clock jitter and uncertainity   

Clock is being prepared by phase-locked loop (PLL).   These circuits might not provide exact clock source. some variations will be there.  Ideally the clock change at exactly particular time period. But because of some in built variation in clock circuit it will change before or after.   
**Jitter** --> Clock jitter refers to the variation in the timing of a clock signal's pulses.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/64f82c17-5fe0-4141-a663-e85935eb57b1)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5eeb1cd1-b8d2-4d2e-9573-fe3e4e060459)

Here teta = Combinational delay. It should be less than 0.9ns.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/477c754a-665c-4761-a3a0-161f94ba1c67)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/dadbb188-c03a-4e3e-9901-378d2019e0e3)



## Lab steps to configure openSTA for post-synth timing analysis  

Now, we have to ensure the slack is reduced.   
In the industry tools if we face any timing violation we will carryout the analysis in the seperate tool for synopsys it is primetime.  
In this case for pnr --> openlane    
For timing analysis --->openSTA   

to check verilog after synthesis.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/19dccfd9-a4cc-4d84-aff7-2c2cbf63edd1)

Create the new file using this command vim pre_sta.conf     
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8b3beeda-12b9-4a77-842f-8eb1c93193d6)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/dfcb68cc-eb62-4ad0-ad5a-f86712a6c873)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/9723a543-0f84-4fe5-8988-b5f7ac6207e7)

What are all settings in base.sdc , I follwed the same in my_base_sdc   

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/98a1921c-aae2-44f5-ab4a-916d442cbc99)

The main file used for openSTA anlysis is pre_sta.conf   
This is the configuration file on which we will do pre-layout analysis.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d63c2f20-789d-4164-9537-34488ed2891b)

STA can either be single corner which only uses the LIB_TYPICAL library which is the one used in pre-layout(pos-synthesis) STA or multicorner which uses LIB_SLOWEST(setup analysis, high temp low voltage),LIB_FASTEST(hold analysis, low temp high voltage), and LIB_TYPICAL libraries.

Run STA engine using OpenROAD (which in turn calls OpenSTA): run OpenROAD first then source /openlane/scripts/openroad/sta.tcl which contains the OpenROAD commands for single corner STA. This file also contains the path to the SDC file which specifies the actual timing constraints of the design.   

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d1b8ec8f-2ae6-4d28-b095-91f84f6559ff)
The result of running STA in OpenROAD will be exactly the same as the log result of STA after running run_synthesis inside OpenLane. Observe the delay:   

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/dc2405e4-bd56-4236-a83a-40c6b8f7b86e)
To reduce negative slack, focus on large delays. Notice how net _02682_ has big fanout of 5. Use report_net -connections _02682_ to display connections. First thing we can do is to go back to OpenLane and reduce fanouts by set ::env(SYNTH_MAX_FANOUT) 4 then run_synthesis again. As shown below, wns is reduced from -1.35ns to -0.82ns.   

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5f585f28-8cdd-4d05-8b50-9fc1fcf33178)

To further reduce the negative slack, we can also try upsizing the cell with high fanout so bigger driver will be used. High fanout results in high load cap which then results in high delay. But since we cannot change the load cap, we can just change the cell size to better drive that large cap load for less delay. As shown below, cell _41882_ has a high cap load of 0.04nF and this causes a large delay due to buf_1 not having enough drive strength to drive that high cap load. We can try upsizing the buf_1 to buf_4 (listed on the used liberty files are all cells which you can choose) inside OpenSTA: replace_cell _41882_ sky130_fd_sc_hd__buf_4   

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/daeeb8be-5793-4ad8-aa06-7925d66a1e15)

This can be done iteratively until desired slack is reached, this is called timing ECO (Engineering Change Order). To extract the modified verilog netlist: write_verilog designs/picorv32a/runs/22-03_07-07/results/synthesis/picorv32.v. Beware that upsizing the cell will naturally increase core size.

### Summary of OpenSTA Commands:  
report_net -connections _02682_        
replace_cell _41882_ sky130_fd_sc_hd__buf_4`          
report_checks -fields {cap slew nets} -digits 4          
report_checks -from _18671_ -to _18739_ -fields {cap slew nets} -digits 4            
report_wns             
report_tns             
report_worst_slack -max             
write_verilog designs/picorv32a/runs/22-03_07-07/results/synthesis/picorv32.v





