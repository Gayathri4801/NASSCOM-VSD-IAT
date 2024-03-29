#  SKY130_D2_SK2 - Library Binding and placement
##  Topics to be covered
**--> Netlist binding and initial place design**   
**--> Optimize placing using estimate wirelength and capacitance**  
**--> Final placement optimization**    
**--> Need for libraries and characterization**    
**--> Congestion aware placement using RePLAce**    


## Netlist binding and initial place design

We have a netlist , Netlist contains so many gates,Flops. Each gate shape represent it's functionality.  
But in reality the gates don't have shapes.What we have done is we have taken the view of cell and given them physical dimension (width & height),Now we have something shape like box. we can see here,

![Screenshot 2024-03-16 231340](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2ce856ce-f9be-43b4-9712-8e6a70ae5214)

![Screenshot 2024-03-16 231526](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a4c44805-f772-4d62-8133-1da8840a5354)

Once we have given proper shapes & size to each and every net, The Next step is to take all the cells and place it in floorplan.   


## Optimize placing using estimate wirelength and capacitance
## Final placement optimization

In the placement stage we have to place the cells according to the input and output of the cells. we can see below,

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/bb24a4b7-f44f-4ffc-84f7-4a560fe239e2)

After placing the cells, we will face some issues like criss cross connections or congestion etc..  
The solution for all these problems in the placement stage is optimization.  
This is the stage where we estimate the wirelength and capacitance, based on that we will insert repeaters.  
If the cells are placed so far , the transition of signal won't proper.      
The transition or slew is dependent on the value of capacitance. Both are directly proportional. first we will estimate the capacitance, If the amount of charge required to charge the will be high,then the transition will be high. Based on this we will confirm whether the signal will be able to reproduce correctly in the receiver stage. If the transition goes beyond the certain limit It is very difficult to reach the signal from input to output.This we called as **Signal Integrity**.   
**Signal Integrity** : It defined as carry the signal from source to destination without any distortion.
To maintain the Signal Integrity , we need something in the intermediate step to reproduce the input to the output between two far placed cells.   
For this the repeaters comes into picture, Repeaters are basically Buffers. These Buffers will recondition the input signal and make a new signal that replicates the original input signal and send it to the output.   
We will solve the signal integrity issue by adding some buffers, But one disadvantage is we will loss the area.   

Here we can see how we place cells and inserting buffers and how we connect the input to the output.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/4179a237-bd5c-468e-ba71-2b236c8ef627)


## Need for libraries and characterization

For every stage of physical design the common thing is across all stages is Gates or cells. we can see here types of cells or gates.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a2261635-64d7-4784-ae73-e888d696f91b)

The first doubt is Where we will get theses cells information?   

The answer is **Library.**  It contains,  

1.All cells information are available in the library.   
2.Shapes & Size of cells.    
3.Timing and delay information of the cells.    
4. Various flavours of the same cells it means we can see below,
![Screenshot 2024-03-17 110531](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/80963aad-4f61-44f7-aa7f-edcaaad222c7)

  

Our design is congestiion related placement, we are not considering the timing right now.  
Placement in openlane occurs in two stages--> Global & detailed placement, There are different tools to do both.  
Global placement is coarse placement.  
**Coarse Placement** --> During coarse placement the tool determines the approximate locations of each cell according to the timing, congestion and multi voltage constraints. Placed cells don't placed on the placement grid, there might be overlap with each other. Here there is no leagaliztion happening.   
Global placement main goal is reduce wirelength, In openlane we use HPWL (Half parameter wirelenth), reduction of HPWL is main goal in openlane.  
**Leagalization** ---> The tool moves the cells to legal locations on the placement grid. Means standard cells are placed in standard cell rows, they should be abutted with each other.There should be no over laps. Leagalization happens in during detailed placement. Leagalization is more required from the Timing point of view.
Placement run analysis   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/310e255a-5b63-442d-a95b-daaf3149684d)

Placement.def    
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/581f3804-9313-46a2-ac67-c1fc71998c10)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3ac6842c-79f5-4343-baa3-14a844273501)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d6f2fccc-b46b-498b-86cc-4c3b9ae82af1)

placement ensures that standard cells are properly placed on standard cells rows.
