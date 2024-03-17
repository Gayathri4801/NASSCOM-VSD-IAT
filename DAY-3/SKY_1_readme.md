#  SKY130_D3_SK1 - Labs for CMOS inverter ngspice simulations
##  Topics to be covered
**--> IO placer revision**   
**--> SPICE deck creation for CMOS**  
**--> SPICE simulation lab for CMOS inverter**    
**--> Switching threshold Vm**    
**--> Static and dynamic simulation of CMOS inverter**    
**--> Lab steps to git clone vsdstdcelldesign**    

## IO placer revision
There are 4 stratergies that supported by IO placer to change the IO ports placement. IO placer is one of te opensource EDA tool to place the IO's around the core area.

## SPICE deck creation for CMOS
To create SPICE deck, we have to identify somethings thoose are,  we can see in below image,

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a1725e0a-9194-452d-92f2-fcd0abed8d2b)

We can write SPICE deck like below for Inverter,
The syntax for connectivity information MOSFET is --> MOSFET name (like M1 or M2), DRAIN, GATE, Source, Substrate, type of MOSFET (PMOS or NMOS), width, length.   THis line will descrite complete MOSFET. We can see connectivity information for PMOS & NMOS seperately and all other components below ,
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/cbd1a45c-c2b5-4f89-a84c-e016b4d42750)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/efed2c7c-adcf-4c1c-80aa-7a5bdd79e21b)

Simulation command for input tells , we will sweep the voltage at the input from 0 -2.5V with the step size of 0.05.
Final step is describe the model file.  Below description says the complete description for PMOS & NMOS means all technological parameters. we can see that in below image,  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5a699046-b3ea-4127-9e14-2a75b6d9d653)

## SPICE simulation lab for CMOS inverter
The steps to follow for SPICE simulation   
1. Go to ngspice.   
2. change the directory (where the related files kept).  
3. Source the circuit file. it says the now the circuit is present in the ngspice simulator.  
4. To execute the circuit, the command is run.  
5. Give command setplot --> it will show which plots are currently available in the simulator.   
6. Select the plot. Give command name as that plot name.    
7. Give display command to see which nodes are available.     
8. To plot the graph give command plot out vs in.   
9. We can see the plot for above inputs. In this the width of both PMOS &NMOS is same.  
![Screenshot 2024-03-17 165941](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d5dc9daf-6fad-4b5f-8d00-d19e2e774de8)

If we keep the width of pmos is 2.5 times of NMOS, The whole procedure will be same, only the width of PMOS will vary, we can see in below graph,
![Screenshot 2024-03-17 170517](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a34d3ba2-a653-4bd5-a4d4-af9b9fb2efdd)

## Switching threshold Vm

The difference between both graphs are,   
1. The shapes are almost same. This tells CMOS is robust device.   
Switching Thrshold, Noise margin will define the Robustness of the CMOS. So that it will prove CMOS is widely logic used to build any logic gates.

1. Switching threshold , it is the point where the Vin = Vout. and also both (PMOS & NMOS) are in sat region, they will be turned on there is high chances to high leakage. There is a high possibility that the current flow directly from VDD to GND. In remaining areas one of the device turned off.so that there will not be direct path. Because of this conditions this is kind of short circuit device. 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8d871374-ab1c-465e-b9ae-8db7ef674a2d)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b117f8d1-2329-4529-a37d-877bc0f9a1bc)


