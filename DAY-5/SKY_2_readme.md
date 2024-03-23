# Power Distribution Network and Routing  
##  Topics to be covered
**--> Lab steps to build Power Distribution Network**   
**--> Lab steps from power straps to std cell power**    
**--> Basics of Global and detail routing and configure TritonRoute**

1. Go to openlane directory
2. docker   
3. pwd
4. ls -ltr
5. ./flow.tcl -interactive
6. package require openlane 0.9
7. prep -design picorv32a -tag 22-03_17-07







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

