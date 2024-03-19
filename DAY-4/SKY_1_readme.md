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
