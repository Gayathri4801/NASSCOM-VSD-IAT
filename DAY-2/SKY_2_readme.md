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

