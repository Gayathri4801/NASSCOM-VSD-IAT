# TritonRoute Features 
##  Topics to be covered
**--> TritonRoute feature 1- Honors pre-processed route guides**   
**--> TritonRoute Feature2&3 - Inter-guide connectivity and intra- & inter-layer routing**    
**--> TritonRoute method to handle connectivity**     
**--> Routing topology algorithm and final files list post-route**

**TritonRoute is a engine/opensource tool which is used for detailed routing**  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8ae3eb9b-cd03-4b2a-aa02-42e54fa8f143)
Via connection won't happen  when lower layers routing taken place. Only it will happen when upper layers routing taken place.   

**pre-processed route guides**

1. M1 preferred direction is vertical. Whenever the tool determines/encountered the non preferred direction, then the tool divides into unit width.
2. This is called as splitting.   
3. Merging (reducing the grids).   
4. Bridging :-Edges which are parallel to the preferred routing direction are bridged with the additional upper layer.
5. Non preffered routing guides has now been converted into Preffered routing guides of metal 2.  Metal 1 has been converted into metal
     
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5944079e-e9a8-43c9-b5ca-24822cb8b749)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2b17c150-d562-40b4-b4e6-397ed5878ab0)

Metal 1 & 2 connected at the purple colour areas. The tool will understand there is nonzero overlap area, then it will try to put via to connect Metal1 & 2.   As we seen above the black dots are need to overlapped with the route guides/vias.  

Intra layer --> Within the layer.   
Inter layer --> Between the layers.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d9c7705a-b84a-4841-be47-a81904c3338f)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a28caf18-574e-49a5-b756-f55b11f2c2d8)

M1 layer preffered direction is verical. So the lines are in vertical direction. These dash lines are called as panels.  each routing guide is assigned to one panel.  

If the routing is happening in the even indexes that is called as intra layer parallel panel routing.  First routing will happen in parallel in all the even index pannel. next it will happen all the odd index pannel.  
But It is happening in parallel in partivular layer, but the routing is within the layer.  
Routing will happen from loyer to upper layers.  


The input files required for the TritonRoute is   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e19b2164-f774-4a65-a792-ad47a597afc7)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/068cb389-315b-4bf7-beb6-ce312fa24530)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/9d57e82c-8d38-48b1-a31a-63a1380afcd0)
Where we can connect in these 5 intersection points?  
We can see in the above image, the possible ways to connect vias. These possible 5 points are called as access points.  
This is the handling connectivity between the layers.     
In the above image 3 scenarios are there.     
1. connecting lower layer to upper layer.   
2. connecting to the pins within the same layer.   
3. connecting to the upper layer.     

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/4ef41196-d213-47fb-b526-a608cd17f691)

In this we can see 15 access points.  Collection of such points comes under access point cluster.   

The Goal of MILP is to find the optimal solution to connect two Access point cluster.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8e12e9b3-852c-4b39-a9d1-5d26fc76e6d6)
If violations are depend upon hoosing the traitonRoute value.  
Here I selected TraitonRoute as 0. so i got 3 violations.  
If i will select TraitonRoute strategy as 14. Then we would see 0 violations. At the same time run time & memory utilization also high. 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/64804c78-e37c-44b0-bf5b-af1e5791b1cc)  
We will find thw violation in the given path.  
/home/vsduser/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-03_17-05/results/routing/tritonroute.drc   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/df016178-77a9-40d4-9467-0fa2f8fb9d35)

We need to fix these violations manually.  

If we go to this path
/home/vsduser/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-03_17-05/tmp/routing    
ls   
We can see fastroute.guide file which is having all rectangles/routing guides info.  
If we open that using less fastroute.guide   
The syntax is lowerx lowery upperx uppery matalname

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/08b208c7-6f25-48e2-b149-f0d32fdef511)

The detailed routing will ensure that the routing actually happens in these routing guides.   

**Parasitic Extraction**

1. Go to Desktop/work/tools           
2. ls -ltr   
3. cd spef_extraction      
4. ls -ltr     (Python files will be there. To generate the spef we need to include lef & def files using the below command.)     
5. Desktop/work/tools/spef_extraction python3 main.py /home/vsduser/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-03_17-05/tmp/merged.lef  /home/vsduser/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-03_17 05/tmp/routing/picorv32a.def     --> this will create the spef file.    
6. spef will be saved in the same location as def file.       
/home/vsduser/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-03_17-05/tmp/routing    
7. The new def file will create in the above location picorv32a_new.def   
8. this def file will be replaced by spef file **picorv32a.spef**    
     
9. If we go this path we can see 4 verilog(.v) files.    
         1. picorv32a_synthesis.v   After Synthesis one netlist file.  (during floorplan and placement we don't have netlist file because no modifications are done in netlist file)    
         2. picorv32a_synthesis_cts.v   After CTS stage one netlist file.  During CTS stage the clock connected to all the cells the  modified netlist we will get)    
         3. picorv32a_synthesis_diodes.v & picorv32a_synthesis_preroute.v    
         These netlists are happening before the routing. pre routing - The antenna diode inserton happening.     
The final verilog which will used for routing & post STA anlysis is picorv32a_synthesis_preroute.v  & sdc & read spef      


