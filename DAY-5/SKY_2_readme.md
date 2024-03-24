# SKY130_D5_SKY2 - Power Distribution Network and Routing  
##  Topics to be covered
**--> Lab steps to build Power Distribution Network**   
**--> Lab steps from power straps to std cell power**    
**--> Basics of Global and detail routing and configure TritonRoute**



## Lab steps to build Power Distribution Network*

1. Go to openlane directory
2. docker     
3. pwd   
4. ls -ltr   
5. ./flow.tcl -interactive    
6. % package require openlane 0.9    
7. % prep -design picorv32a -tag 22-03_17-07  ( If we want the configuration from the last run without overwriting)    
8. % echo ::$env(CURRENT_DEF)   it will give the last stage happened.  
     /openLANE_flow/deisgns/picorv32a/runs/22-03_17-07/results/cts/picorv32a_cts.def 
9. % gen_pdn     ---> It will generate the Power Distribution Network. It will read the merged.lef & cts.def --> Then it will create the grids and straps for the power and Ground.   

## Power straps to std cell power

Power planning is done to provide uniform supply voltages to all the cells in design the primary objective of power planning is to ensure that all on chip components like blocks, memory, IO cells etc have adequate power and ground connections. there are three levels of power distribution that,     
**Power Rings**--> carries VDD and VSS around the chip   
**Power Strips**--> carries VDD and VSS  from rings across the chip    
**Power Rails** --> carries VDD and VSS to the standard cell of VDD and VSS  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/518f7c66-70a7-413a-811a-9d71a6e371c8)

We can see here which metal is connected which power rings, straps, rails information.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/4e663633-a3aa-4137-8509-f6c9469a2175)

% echo ::$env(CURRENT_DEF)   it will give the last stage happened.
/openLANE_flow/deisgns/picorv32a/runs/22-03_17-07/tmp/floorplan/pdn.def 

## Basics of Global and detail routing and configure TritonRoute  

In VLSI flow The routing phase very critical that can be using opensource tools or commercial tools.  
The Routing phase is divided into 2 types.  
Global Route / Fast Route :- It is being done by fast route. The area to be routed is divided into tiles/rectangles.  
Detail Route :- It is being done by tracking route.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/64622aad-8671-48c2-a38e-69ae89dd70b6)

Fast route is followed by the Detail route.  
Detail route should ensure that it needs to realize the segments and via in accordance with the global route solution.  
We can see the 4 dots in the above image, these 4 dots are called as pins of a standard cells.  
In detailed routing stage we will make the actual connections using physical wires.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/14940b12-4e98-426e-9e9d-40d4419944ea)

