#  SKY130_D3_SK2 - Inception of Layout CMOS fabrication process
##  Topics to be covered
**--> Create Active regions**   
**--> Formation of N-well and P-well**  
**--> Formation of Gate terminal**    
**--> Lightly doped drain (LDD) formation**    
**--> Source-Drain formation**    
**--> Local interconnect formation**    
**--> Higher level metal formation**   
**--> Lab introduction to Sky130 basic layers layout and LEF using inverter** 
**--> Lab steps to create std cell layout and extract spice netlist**

## Create Active regions
#### 1.Selecting the Substrate  

1. select the p-type substrate.   
2. create the buckets called as active regions.   
   1. Deposit a Sio2 on top of p substrate.(Insulator)  
   2. Deposit a Sio3 on top of p substrate.(Metal)     
   3. Deposit the layer of photo resist.     
   4. Deposit Mask-1 on top of the photo resist.   
   5. Apply the UV light to remove unwanted portions. now we have only protected portions where we have the P-well & N-well.   
   6. Now remove the Mask-1 on photo resist layer.   
   7. Next remove the photo resist layer. Because Si03 will acts as very good protection layer itself. here now sio3 is protecting sio2 from the growing mode. Which is on top of the active regions.    
   8. Place the whole thing in furnace means it is a place which works at very high temp upto 1000degrees. That helps grow the oxide in the other areas.   
   9. Remove the Sio3 using hot phosphoric acid. Now we will have only p sub & growing Sio2.    
   10. deposit layer of photo resist to define the areas which we have to protect.    
   11. Next cover the region which we are not preparing the well region with mask-2.    
   12. Expose the UV light  which we don't have mask-2, Photo resist will be removed.    
   13. Next Boron which is p type material is diffused into p substrate using ion implantation. P-well will be created.    
   14. Similarly do for creating for n-well.    
   15. Again keep this in the high temp furnace to diffuse borob and phosphorous(n type) into p-sub to form clear wells.  This process is called Twintub process.    
   


**Substrate** --> On which we fabricate entire layout/design.   
Here we are selecting the p-type silicon substrate with high resistivity, low doping level compared to well doping.   
**Doping** --> It is a process of adding a impurity to a p-type substrate.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/4ea14975-3de5-4e08-b532-5039de0e2e68)

#### 2. Create active regions

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c894aab0-f649-4ec3-8153-520ba16040ca)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0ed288f8-db12-453f-8b18-94acb153405b)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1c117ada-7611-475c-9497-89cafb3e581b)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0f75892b-06bf-41e6-b428-2d51f99b4f61)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/39d592f3-041f-4b03-bdf9-3831128ccb2b)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2bb614ce-4b09-484b-a871-06783c5210fb)




![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5aaca5ed-06b6-447f-bd7d-90586fd5588c)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b4d7cef1-5c6e-4906-9203-4ec279b8e724)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/19fcefe5-2a12-4793-8512-9fcc961ecc02)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f372a64a-97de-40ae-a450-d2ae678a1838)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/41a30873-cda2-4d7a-8d93-8f8cb5f91cb1)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b8fe144e-b3a0-4c7f-b517-6c8a8fc476e4)
