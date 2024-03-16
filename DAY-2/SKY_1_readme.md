#  SKY130_D2_SK1 - Chip Floor Planning considerations
##  Topics to be covered
**--> Utilization factor and aspect ratio**   
**--> Concept of Pre-placed cells**    
**--> Power Planning**    
**--> Pin Placement and logical cell placement blockage**    
**--> Steps to run Floorplan using OpenLANE**    
**--> Review Floorplan files and steps to view floorplan**   
**--> Review Floorplan layout in magic**   



**Floorplan Steps**   
1. Decide width and height of Core and Die.  
2. IO pad sites are created for placement of IO pad .  
3. Placement of macros.   
4. The standard cell rows created for standard cell placement.      
5. Power planning (pre routing).    
6. Adding physical only cells.    
7. Placement of Blockages.    

##  Decide width and height of Core and Die.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b081bd4b-6cfb-4c42-9ada-a2213b38ac33)

We will begin with the basic Netlist.  
Netlist --> It is a combination of sequential elements and its logical connectivity.  
Here we will start with 2 Flipflops that is launch flop and Capture flop and some combinational logic in between them.
This is an example to identitify width & Height of Core and Die. And then this can be extrapoleted to millions of gates.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e8f4a6fc-bb59-4e6a-bd58-71c7c22f98cc)
While defining the dimensions of the chip we will mostly dependent on the dimensions of the logic gates / standard cells not the wires.  Wires will play important role in further stages.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/6f0ef562-fb05-4f93-93cc-97db2496ef38)

Now let's give rough dimensions of each standard cell.  and calculate area occupied by the below netlist on a silicon wafer.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/78c13616-0172-4d7d-b9b0-f46d950bea94)

Before this lets remove all wires and place like below,
