## SKY130_D1_SK3 - Get familiar to open-source EDA tools
###  --> OpenLANE Directory structure in detail.
###  -->Design preparation step.
###  -->Review files after design prep and run synthesis.
###  -->OpenLANE project Git link description.
###  -->Steps to characterize synthesis results.

The tool which we will be working is OpenLANE,  OpenLane is a not a tool, it is basically flow  which compraises of many open-source EDA tools.
OpenLANE is used to produce RTL2GDS.

Open Terminal and change directory to Desktop.  
To go to openlane_working_directory run the below commands. Oprnlane_directory has following 3 folders. 

![g14](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/dbf3e5e4-fd67-43f7-9868-47c23effc689)

To see what is inside the PDKS folder, run the below commands.  
Many PDKs are very compatible, and they are made to work with commercial EDA tools, not for open EDA tools. The given open_PDKs are found to mitigate this issue. These PDKS having set of scripts to convert these foundries to be compatible with the open-source EDA tools.  
The given Sky130A is a PDK which is made to be compatible with the open-source EDA tools.

![g13](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/33b1052e-f567-4573-8f41-8a30e46d6a1f)

If we go to inside the Sky130A folder , two files will be there.  
libs.ref -- It is specific to Technology/Process  
libs.tech -- It is specific to tools,It shows what are the tools are available, we can see below  

libs.ref contains many technology files but we will be working with **sky130_fd_sc_hd**

![Screenshot 2024-03-15 180620](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a0120398-c610-40fd-ad82-036eb59a495b)

If we go inside this **sky130_fd_sc_hd** , It will show all design related files. we can see below and also each individual file what it contains  

techlef file will mainly provide metals information.   
lib file will mainly provide timing and PVT corners information.

![Screenshot 2024-03-15 182826](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d50e1d4d-a25c-442f-9639-7eae227b779b)

![Screenshot 2024-03-15 182914](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/616310f9-4003-4c92-8458-1db38d697c56)

![Screenshot 2024-03-15 182925](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/77de9d61-dafa-4cc2-a5b5-ca12e1fea12a)

![Screenshot 2024-03-15 183105](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1368b2b1-3080-42db-abc9-c3540058d59e)

Till now we see the design related files and it's information.

Now we will go to actual platform OpenLANE.  

To go to openlane run below commands.  

Here flow.tcl will tell how the flow has to go.  
Interactive session means it will execute step by step. To know at which step what is going on and to compare the results from each step we will provide this interactive. If we miss this interactive command It will run complete flow

![Screenshot 2024-03-15 185247](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/23f500dd-2725-4eb2-8f27-9c87f6a6dd1c)

After this we would require to input all the packages that are required to run this flow.
      

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c0240f74-e73b-416d-84db-b4a813fad52e)

## Designs folder  
Now the question is what design we have to run?

All the designs that are being run by openlane that are extracted from the design folder. openlane has close to around 30-40 designs. we can see some of the designs below 
Here we will be working with the design **picorv32a**

![g9](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0f59a1eb-6f4f-47c2-aa4c-6c615abef745)

Now lets see the contents in the design **picorv32a**, there will be mainly 3 folders. we can see here.

![g10](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1dbcec3e-33e4-4385-b12f-c30a067c8e89)

**src** - It is a source file. It provide the verilog file it represents the RTL. and also SDC file.  
**sky130A_sky130_fd_sc_hd_config.tcl value**  even if we don't have this file the flow doesn't affect.  

![g8](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e64cff61-796e-48ad-9367-a54f7c786438)

**config.tcl** - It bypasses any configuration that has been already done in openlane means many switches use a default value that is already there in openlane.  
If we open this config.tcl file , it will show some information like default clock period. 

![g7](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b1a73894-bdbb-448d-8c57-0d229a2e6c4f)

The precedence of how the the openlane takes the values.  
**1. default value which is already set in openlane**  
**2. config.tcl value**  
**3. sky130A_sky130_fd_sc_hd_config.tcl value**  
config.tcl value will overwrite the default value and then sky130A_sky130_fd_sc_hd_config.tcl value will overwrite the config.tcl value.

Lets go back to openlane prompt, The first step is **Synthesis**, but before going to the synthesis stage we need to prepare file system or design setup which will be setting up the data for our design.

-- Go to picorv32a ----> In this for the time being we just have 3 files.  We need to setup the file system to the each and every step of the flow. we will be fetching files for particular location . That location needs to be created. This is called the design setup stage.    

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a0d9e4db-b958-4635-9853-558a70a7c7ca)

Here we can see somewhere merging files is complete that means it will merge the lef and tlef files and will provide only one file that is merged.lef.  
Why it is merging these files? Because when we run openlane it need to go to two different location to fetch the lef information and layer information.

**With this, the design setup is completed**

Next, Before we run the Synthesis step we need to chek if anything new was created in our design directory. For this run below commands. **runs** folder was created. go inside that and follow the commands shown below.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2b376c26-1c76-4493-a5c9-1543d0bed107)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e4424973-6276-4e96-b764-99c1e25c16c0)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8bb4d5f5-db65-40ad-8c3d-dcf5634fcfd1)

merged.lef contains all cells and layers information. 
If we go inside each folder in the date folder contains, we can see below  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5aaf75ac-4e26-4cee-a6e3-ee6971bd592e)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/95413507-ec99-476b-a57f-7eb7b400b087)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2c9a93ef-bc72-497f-abbf-cd303777875d)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7904fa52-d83b-4bad-810c-fb59eb9c6b0b)

Here one more config.tcl is present. it can be little bit confusing when we see a multiple of config.tcl files one is in design folder and one is in runs folder.
In this config.tcl file - It shows which all default parameters is being taken by the run. some of the information in this config.tcl is ,

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/eba109dc-2bd0-4500-bab6-f87ce35a7866)

one good thing about openlane is we can make changes on fly. when we make the change and run the step.. EX:- If we made a change belongs to core utilization in the floorplanning inside the original config.tcl and after that we run floorplan. Then that number would be updated here in this config.tcl. So thay way we can check whether the modifications we have done in flow is being correctly reflected in the execution or not.


Now lets go to the openlane prompt , run the command **run_synthesis**  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2523939c-f093-4ac4-940b-0f546efafce8)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/623ef1df-251a-466e-afc9-2c53fc343b82)


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/436e1e14-bb16-4cc1-a5fd-1070e95d7fd7)


### Calculation of the Flop Ratio  =  No.of D flipflops/ Total no. of cells

![g19](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/92c2117e-8fba-442a-bea8-13ac5de6d00f)

we can see report also
**1-yosys_4.stat_rpt** this gives actual synthesis report.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/887aad27-3a6f-4f49-b05d-2b6bd7126664)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/71389f65-095c-4198-9c7d-5a5f80ab17cc)

How the results are populated in the runs folder? If we go inside the results we will see synthesis folder. if we open that it should have synthesized netlist. **synthesis.v**
we can check inside this netlist .all the mappings have been done.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/6adca104-3e7b-4d67-87f1-5f41f43ec6ce)



