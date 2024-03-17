#  SKY130_D2_SK3 - Cell design and characterization Flows
##  Topics to be covered
**--> Inputs for cell design flow**   
**--> Circuit design step**  
**--> Layout design step**    
**--> Typical characterization flow**    


Here we are designing the Inverter.

Cell Design flow is being divided into 3 parts,   
Inputs --->  These are the inputs that you need to design our Inverter.   
Design steps ---> Then finally we will design the Inverter.    
Output --->  Outputs of the inverter are the one that we actually use by the EDA tools.   

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a27383b0-6263-407a-addb-2bf6f958f922)

By looking the Inverter, It is very simple. But the steps involved in designing the inverter is very critical. After designing the inverter we have to characterize whether it is functioning proper or not.   
The characterization flow that is being followed by the Industry,    
1.Reading the Model files....
2.Read the extracted Spice netlist
3.Recognize the behaviour of the Inverter
4.Read the sub circuits of the Inverter
5.Attach the necessary power source.
6.Apply the stimulus.
7.we have to provide necessary output capacitance.   
8.we have to provide necessary simulation command.  
9. To fed these all inputs from 1-8 steps in the form of configuration file to the characterization software GUNA.  
This software will generate Timing, noise and power models.

The information we get from the GUNA software is Timing, Noise, Power.libs, Function.   
These outputs brings very important classification of characterization types , we have Timing Characterization, noise Characterization, power Characterization.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3b650ee8-5280-427d-b99f-403ca88677cd)

From this types of characterization we will understand various syntax and what it represents. This syntax is very important to understand the GUNA software. 
GUNA software works on variables. These variables are available with us in order to fed into the software.  
