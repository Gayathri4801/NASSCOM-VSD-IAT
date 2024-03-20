#  SKY130_D4_SK1 -Timing modelling using delay tables
##  Topics to be covered
**--> Lab steps to convert grid info to track info**   
**--> Lab steps to convert magic layout to std cell LEF**  
**--> Introduction to timing libs and steps to include new cell in synthesis**    
**--> Introduction to delay tables**    
**--> delay table usage part 1**    
**--> delay table usage part 2**    
**--> Lab steps to configure synthesis settings to fix slack and include vsdinv**   


We know mag file contains all information includes power & GND connections , metal connections to say in one word everything it contains to make inverter.     
OpenLANE tool for only place & route. How we are connecting ngspice and how we are doing this all things.    
place and route don't require this much info whatever the mag file contains. Only require is power and ground rails and input and output info no need logic part.   
Here the lef file comes into picture. That means lef file contains all stadard cell physical information.      

Till now we worked with standard cells that came along with the openlane. Now our goal is to extract this lef file and plugged into picorv32a design. How it will work?   

Till now we did experiment on sky130a_inv.mag file. Now we have to extract lef file.     
Before we can check some info in this standard cell  (Inverter).  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8697dde7-7ff4-4eb5-8236-d394cc15a13f)

From pnr we need to follow some certain guidelines to place standard cells.  
#### 1. The input and the output must line on the instersection of the vertival and the horigontal tracks.   
#### 2. The width of the standard cells should be odd multiples of the track pitch. Height should be odd multiples of the tracks vertical pitch.    

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


Now we can extract the lef file.  Before that give the cell custom name.  

















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


