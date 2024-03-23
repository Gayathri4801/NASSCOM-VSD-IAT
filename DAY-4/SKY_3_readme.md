#  SKY130_D4_SK3 ---> Clock tree synthesis TritoncTS and signal Integrity
##  Topics to be covered
**--> Clock tree routing and buffering using H-Tree alogorithm**   
**--> Crosstalk and clock net sheilding**  
**--> Lab steps to run CTS using TritonCTS**    
**--> Lab steps to verify CTS runs**    



## Clock tree routing and buffering using H-Tree alogorithm   

CTS is used to connect the External Clock to the all internal clock pins of a flipflop. And also inserting a buffer or inverters to all the clock paths in a design to balance the skew.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/594e48be-cdd3-4ceb-bc95-3f45e7432d71)
These paths, we can make the physical connections which have resistance and capacitance.  These connections are done based on the connectivity information.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/da53827a-9c7b-45a1-a257-72f4befc03f2)
t1 & t2 are the time taken to reach their respective destinations. Due to physical reasons the t2>t1. 
t2-t1 = skew. Typically we will expect the skew as close to zero.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/982178d9-b355-472e-baa3-2021764231e6)

To achieve a skew which is close to 0 , this tree may not help. To achieve that we will go for H-tree mechanism also called mid point strategy.  
**H-tree algorithm**
1.Divide the equal no.of clock points.  
2.Subsections also divide the equal no.of clock points and further so on..   
3.Connect the centre of main clock to the whole set.   
4.By using routing guidelines connect the horizontal & vertical routing connections.   
5.Insert clock buffers to balance the skew.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/84495f28-2100-40e5-95c9-23921c00b30a)

From this mid point strategy we have concluded that, the time required from the particular clock to flipflops which is connected to that partiular clock is almost same. So that we can minimize the skew as close to zero.   
We will expect whatevre the input we fed that should be there at the output.But,because of this physical wires which are having resistance and capacitances, the signal may not reach the output properly. To acheive that we will insert repeaters / buffers.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7567d073-f744-459b-90f4-57b9f7028e50)

We saw how does the repeaters reproduce the signal. here also same thing but only the difference between the repeaters that we used for clock path and repeaters that we used for datapath are clock buffers have same rise time and fall time and data buffers have different rise time and fall time.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f78de9a3-14eb-4cd4-8233-4e00446d9916)

## Crosstalk and clock net sheilding

Clock nets are considered to be the critical nets in the design. Because we have build the clock tree in such a fashion that we have 0 skew.  But accidentaly if cross talk happens in these clcok lines , then whatever we bulid all gets wated/detoriated.  
By sheilding we will protect these nets from the outside world.Sheilding is one of the technique to protect the signals from crosstalk.  
The idea is creating sheiding only for critical nets which are mainly clock nets.If there are data nets which are are critical we can sheild the data nets also. It's not possible always to sheild all the nets in the design. If we sheilded all nets in the design then that will increase the area.   
**CROSSTALK** Switching of one signal in one net can interfere with neighboring net that leads to the cross coupling capacitance known as crosstalk.  
The net which is effecting the other net is called the Aggressor.    
The net which is effecting by the other net is called the Victim.     
To avoid that cross coupling capacitance and interference between two signal we will do sheilding for every signal.   
Because of this cross coupling capacitance, there will be two problems glitch and delta delay. 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0c454362-ed41-4640-917d-9f1ee41c06be)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/4e458a56-3c7f-4d4e-889b-6f8f472e8429)
 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a9338258-50a0-468d-bfee-b36ae12cc95f)


