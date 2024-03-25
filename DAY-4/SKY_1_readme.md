#  SKY130_D4_SK1 -Timing modelling using delay tables
##  Topics to be covered
**--> Lab steps to convert grid info to track info**   
**--> Lab steps to convert magic layout to std cell LEF**  
**--> Introduction to timing libs and steps to include new cell in synthesis**    
**--> Introduction to delay tables**    
**--> delay table usage part 1**    
**--> delay table usage part 2**    
**--> Lab steps to configure synthesis settings to fix slack and include vsdinv**   


## Lab steps to convert grid info to track info
We know mag file contains all information includes power & GND connections , metal connections to say in one word everything it contains to make inverter.     
OpenLANE tool for only place & route. How we are connecting ngspice and how we are doing this all things.    
place and route don't require this much info whatever the mag file contains. Only require is power and ground rails and input and output info no need logic part.   
Here the lef file comes into picture. That means lef file contains all stadard cell physical information.      

Till now we worked with standard cells that came along with the openlane. Now our goal is to extract this lef file and plugged into picorv32a design. How it will work?   
## Lab steps to convert magic layout to std cell LEF
Till now we did experiment on sky130a_inv.mag file. Now we have to extract lef file.     
Before we can check some info in this standard cell  (Inverter).  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8697dde7-7ff4-4eb5-8236-d394cc15a13f)

From pnr we need to follow some certain guidelines to place standard cells.  
### 1. The input and the output must line on the instersection of the vertival and the horigontal tracks.   
### 2. The width of the standard cells should be odd multiples of the track pitch. Height should be odd multiples of the tracks vertical pitch.    

**Tracks** These are using in the routing stage. These are nothing but metal layers.    
Go to this path We will get tracks info.     
vsduser@vsdsquadron:~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd$ less tracks.info

![Screenshot 2024-03-19 230400](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/cbf39579-2e1a-4e5e-90e4-96711e136995)


Pnr stage is automated. we have to specify where all our routes(traces) can go.    
 
As per guideline 1, The input and output ports should be on the instersection of the vertical and the horigontal tracks.  

Now we have to check that?  
For our reference the ports are in li1 metal layer.  How do we see them ?
1. Go to magic press g, the grids get activated. These grids are references for the layout. we can see below,    
2. Converge the grid definition to tracks definition. For that go to tkcon, type help grid, we will get grid info.  
3. check/compare with the openlane tracks info using console window, We can in below image.  
4. We can see the grid boxes take this dimensions(whatever we mwntioned in the console window).
5. These are we called tracks.
6. We can observe the first guideline the below image.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0c87bae0-84dc-4e9a-b813-959c693add92)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/12ee244b-2fa6-4ab6-a05a-34a46b3f754d)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/989f5b93-301e-468a-a8b1-eee1386c72c0)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/dd35e70b-b4a0-4250-9ef9-242ed896ee6e)
![Screenshot 2024-03-19 234408](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/13ad3d07-4601-4a3c-9651-b9ea3e7e84a4)
![Screenshot 2024-03-20 000354](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e94e6030-a52b-476c-bc74-d5b8fec4230f)

Now layout is done as per the pnr tool.   
Whenever we make the layout we just define the layers and contacts. we don't define the ports.  Ports doesn't mean anything to the magic.  Ports are required while we want to extract the lef file. When we extract the lef file these ports are defined as pins.   

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8471896d-bc93-4bb6-ac7f-a9f73286ed5e)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f3504306-f199-4fdb-88a9-4808bede93f8)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d07615b0-8c24-48d6-9a8d-7e949378a1f3)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/96fe1767-d81d-44af-b2f7-43eaf88e2065)

## Introduction to timing libs and steps to include new cell in synthesis

Now we can extract the lef file.  Before that give the cell custom name.  
Next save the design into some another file. If we face any permission issue. use this command to get permission.      
vsduser@vsdsquadron:~/Desktop/work/tools/openlane_working_dir/openlane$ chmod -R 777 vsdstdcelldesign    
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c8272f33-7cb2-4ac4-b2ed-f90ae1ba0a9b)

We will see the file in vsdstdcelldesign folder.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/08f36d62-b294-4279-a38c-1d8275b57068)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/9a2c2c14-4fa0-41a2-b539-310ab47ce8af)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a8079636-815b-4389-8b83-a374eea8a2b4)

In this we can see the changes, which we did in magic, 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/326e05a0-ddeb-4d7b-be1f-1e4109f96393)

Now the lef file is ready, Now we have to plug this cell into picorv32a, 
We have to move this lef into source files.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5c34a6fa-f98b-489c-8ae7-15a162310e5e)

Now the lef file has moved into picorv32a design files.  

Now the idea is, we have to include our custom cell into openlane flow.  The first stage in the openlane is synthesis.  In synthesis stage ABC step maps the netlist to the cells in the library. Now we need to have alibrary which has our custom cell definition for synthesis.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/de562a1b-ee2c-4172-a95f-e69a8767b7e0)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/62ab5f23-725a-4899-aeff-47d714d8ccc1)

The above library file contains every cell information.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e30d45cd-8fc9-45a2-98da-270a77df56ea)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0c45af6d-8f75-47da-8ab3-be2345fe8ffb)

These library files are giving three different conditions slow slow, Fast Fast, Typical Typical.  This Typical file also we have to move into src files.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a7a72d20-f404-4293-8c6e-32960f1d4886)

Before going to run synthesis, we have modify config file.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/67c2b0ac-9a15-450a-b4d9-4413227c1464)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5366f413-4ba1-41b2-8993-4166b3aa1187)

It will clear previous run file, and it is taking new,  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7ceddb7a-ceb8-46db-bc28-a9f80590d6c7)


Now, we have to see whether the synthesis part maps our custom Inverter cell into this flow or not. 

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d1229988-cfa0-4281-b4d9-0d1e417c381b)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/56540899-1538-4da6-a2d6-8b7175b49398)

The synthesis is successful.



## Introduction to delay tables  

**AND Gate**    
Whenever the enable is 1 then only clk will propogate to the output.   

**OR Gate**   
Whenever the enable is 0 then only clk will propogate to the output.   When the enable is 1 the clk won't propogate so there won't be any short circuit power consumption and switching power consumption that will be consumed by clock tree. During that period of time we can lot of dynamic power consumption.  This is the main advantage by using and & or gates in the clock tree.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/13663f3d-3d9d-4d55-91ea-1ef98bd429b3)

How do we use this in Clock tree?    
Here, we made some observations using this small clock tree.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/191fca59-a5ee-4ece-925a-bbb2065aff3e)
Now we will see what will happen if we don't use/ follow those observations.  Why we need this type of observations?  

Some important observations from the above picture:-    
The cap of the load at the output node of each and every buffer of complete clock tree in the chip/design is varying. We can't maintain constant.   
The output of one level is connected to input to the nextlevel.So if o/p of cap changes then the transition time also changes.   
We have varying input transition at the input of the buffer, We have varying output load at the out of any buffer.  

What is clock tree synthesis?  
CTS is used to connect the External Clock to the all internal clock pins of a flipflop. And also inserting a buffer or inverters to all the clock paths in a design to balance the skew.   
So the clock should reach all the sequential circuits at the same time to maintain the skew.  Because of above observations(transition , capacitance) we can see lot of delays & timing variations.   
How we will capture that delays?  
Our engineers found something called as delay tables. How the delay table is prepared?    
We will take one buffer out from the complete circuit, For example if the input transition is varied from 10ps to 100ps and if the output capacitance is varied from 10Ff to 100Ff. With this parameters the particular cell delay will be calculated in a tabular format.  Eventually this delay table became the timing model of this particular buffer.  For every cell it can be buffer/logic gates, will have the seperate delay table.  Every cell will characterize by particular change.  

![Screenshot 2024-03-20 183852](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7bbb2030-ae71-420c-b9b2-3ed599bf98a5)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2b67129b-648b-4ca6-9749-39c70281c6c9)

The dalay values will vary for every cell and (same for same level of cells) because it is dependent on PMOS & NMOS size(W/Lration)(Buffer will made up of PMOS & NMOS).   If we change the area or increase the area the resistance will reduce, then the delay also reduces. 
![Screenshot 2024-03-20 190554](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f27152f4-a55c-47d2-aa57-d883e3bc4f60)

In the above image we delay value is not available. We will get that value using equations used to make this table.   
Now We will calculate the latency?  
**Latency** --> The time taken to reach the clock from external clock/main clock to the internal fliflop clock pins.  
Here we will calculate each cell delay in the path and add them to get the latency.  
![Screenshot 2024-03-20 192949](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ef428212-e644-40ee-af66-528a9e2151b0)

Here at level2 the delay of both buffers are same why because the transition time and load capacitance and size of the buffer are same.  
And the skew is 0.  
Here we can observe that if we don't maintain the observations mentioned in the image,  we can't get skew as 0. If skew is negative/ non zero we will face timing violations because the transition and capacitance of the cell vary so that the delay of the cell may vary, then the skew also will vary.  If the size of the cell changes at the same level and the input transition and capacitance is same for the cells which is at the same level, while calculating the delay we have to check the delay at two different delay tables so we will get different delays. Because of this again we will face timing violations . Here we are calculating only two buffers the delay changes don't make sense. If we imagine millions of cells in the design, If we don't maintain this rules when creating Clock tree we will face so many Timing related issues.  
**Skew** -->Clock skew refers to the variation in timing when a clock signal reaches different parts of a circuit.    

## Lab steps to configure synthesis settings to fix slack and include vsdinv

1. Go to README.md. to see any stratergies to overcome timing violations.  
  **-->wns Worst neagative slack
  -->tns total negative slack.**    
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2c26020c-572d-4f41-afea-4e6601ad7a05)


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ba07104a-c76c-47a4-9ed3-d3233c7f724b)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e32580fb-bd65-4752-8b07-d1d00fd41176)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/bee17e5b-cbdd-4f31-b061-d9af13b375aa)
![Screenshot 2024-03-20 232726](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2c65eef4-9b6f-4cc0-82e3-873f685c7000)


After set the SYNTH_STRATEGY & SYNTH_SIZING As we expected the area increased.  
The steps I followed is 
1. Go to openlane directory type docker.
2. pwd   
3. ls-ltr
4. ./flow.tcl -interactive
5. package require openlane 0.9
6. prep -design picorv32a -tag 22-03_17-07 -overwrite    
7. set lefs [glob $::env(DESIGN_DIR)/src/*.lef]    
8. add_lefs -src $lefs
9. run_synthesis    ---> Here I got some tns & wns values and some area. By using area and sizing strategy i increased area and decreased the dealy (tns &wns values)    
10. prep -design picorv32a -tag 22-03_17-07 -overwrite
11. set lefs [glob $::env(DESIGN_DRV)/src/*.lef]
12. add_lefs -src $lefs
13. set ::env(SYNTH_STRATEGY) "DELAY 1"
14. set ::env(SYNTH_SIZING)
15. run_synthesis   

**Area increased to --> Chip area for module '\picorv32a': 209181.872000    
tns &wns became 0**   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/816482a7-c415-4528-a9d7-965c7e3b3d68)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/22d3211c-3544-4d70-a54b-1bff545d2ecd)


## Locating the Custom Inverter Cell in Layout   
