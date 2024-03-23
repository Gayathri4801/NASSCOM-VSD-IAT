CTS  
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
