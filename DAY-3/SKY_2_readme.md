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

## Fabrication steps for CMOS

**Substrate** --> On which we fabricate entire layout/design.   
Here we are selecting the p-type silicon substrate with high resistivity, low doping level compared to well doping.   
**Doping** --> It is a process of adding a impurity to a p-type substrate.  

1. select the p-type substrate.   
2. create the buckets called as active regions.   
   1. Deposit a Sio2 on top of p substrate.(Insulator)  
   2. Deposit a Sio3 on top of p substrate.(Metal)     
   3. Deposit the layer of photo resist.     
   4. Deposit Mask-1 on top of the photo resist.   
   5. Apply the UV light to remove unwanted portions. now we have only protected portions where we have the P-well & N-well.   
   6. Now remove the Mask-1 on photo resist layer.   
   7. Next remove the photo resist layer using chemical reaction called as etching. Because Si03 will acts as very good protection layer itself. here now sio3 is protecting sio2 from the growing mode. Which is on top of the active regions.    
   8. Place the whole thing in furnace means it is a place which works at very high temp upto 1000degrees. That helps grow the oxide in the other areas.   
   9. Remove the Sio3 using hot phosphoric acid. Now we will have only p sub & growing Sio2.    
   10. deposit layer of photo resist to define the areas which we have to protect.    
   11. Next cover the region which we are not preparing the well region with mask-2.    
   12. Expose the UV light  which we don't have mask-2, Photo resist will be removed.    
   13. Next Boron which is p type material is diffused into p substrate using ion implantation. P-well will be created.    
   14. Similarly do for creating for n-well using mask-3.      
   15. Again keep this in the high temp furnace to diffuse borob and phosphorous(n type) into p-sub to form clear wells.  This process is called Twintub process.    3. Formation of Gate terminal, where we control the threshold voltage (turning on voltage).  If we control the doping concentration & oxide capacitance then we will get the required threshold.  
    1. Implant low energy boron to be just at the surface of p-well using mask-4 to control the threshold.  
    2. Similarly for n-well using mask-5 & arsenic(n-type).
    3. Fix the oxide which is damaged by implantation steps.
       1. Remove/ etch of the extra si02 using the hydroflouric acid.
       2. Regrown the high quality sio2 on p sub to contol the oxide thickness.
    4. deposit poly silicon on sio2 layer.
    5. Gate area supposed to be low resistance. For that implant n-type material (Phosphorous or arsenic).
    6. After using photo resist and mask-6, Make poly silicon  Gate terminal.
4. Lightly doped region formation in p-well & n-well.
    1.Using the photolithography step that includes photo resist, masking(mask-7 & 8), etching  and doping, implant the P-,P+, n-, n+.  
    2. To protect the lightly doped regions (P-,P+, n-, n+) create spacer by adding the sio2 and remove that in unwanted regions using plasma anisotropic etching which direct etching.    
5. Source and Drain formation.
    1. Using the photolithography step that includes photo resist, masking(mask-9 & 10), etching  and doping, implant the drain and source as mentioned in above.
    2. Deposi the screen oxide to avoid channel effect.  
6. Formation of contacts and interconnects.
    1. Remove thin screen oxide to open up the source , drain and gate for building up the contacts.
    2.  deposit titanium metal which is having low resistance.
    3.  create contact between titanium metal and source, drain and gate.
7. High level metal formation

   


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/4ea14975-3de5-4e08-b532-5039de0e2e68)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c894aab0-f649-4ec3-8153-520ba16040ca)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0ed288f8-db12-453f-8b18-94acb153405b)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1c117ada-7611-475c-9497-89cafb3e581b)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0f75892b-06bf-41e6-b428-2d51f99b4f61)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/39d592f3-041f-4b03-bdf9-3831128ccb2b)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2bb614ce-4b09-484b-a871-06783c5210fb)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0f5a2289-40c8-4bc6-8abb-d5acaf2c6b6e)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a3ac3ec4-fa4d-4979-b016-ef9a8714d731)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/4dd72462-766a-4fa2-aee3-d6c0227080d1)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5b35c701-fe5a-4c23-a2e1-bd66171d88d7)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e0cbd04c-a92f-4289-9d60-653921a1b1a0)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1fa4561e-c0c4-4b8f-84f5-24023f80e23f)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/73f875df-d1b8-421f-a389-653f0ba6ac56)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/dda68bfa-7058-4bb0-91d6-79a5915863d8)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/af66edfa-55d5-4685-82a7-1503d3064450)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c5672670-14c4-4bf0-9f49-bb82a8c11ac8)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ad755d7c-22b6-4e3f-bf98-1640dfa2f22d)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/84c42506-3e18-4ea5-86a1-1d3ffe6fc887)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d9ff83dc-292e-4f62-81a5-cb872c896329)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0be2f3b7-c223-4044-acd9-b5b5d32d470d)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/30062efc-042b-49cf-bd2e-148cb9be9275)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/effee27e-b02a-4478-952c-aa11710380b2)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7c6aae52-e8b3-4f7d-a10a-0b1a882cfe58)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d47c5568-c3c9-4f05-b1d4-4a13b3da7f91)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ca2d09fa-3b7c-4d79-a9ff-2d02fed385df)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/244b2546-cbfb-4fdb-91a6-0a209585d98c)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a9f9bbc8-0484-45f0-928d-b95fd35bb7eb)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a8dbe546-2d92-4b35-9f55-6c1dba3ba1c4)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/9db1465f-1b2c-4ff3-bf8e-0d88ff9cab4b)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b4d7cef1-5c6e-4906-9203-4ec279b8e724)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/19fcefe5-2a12-4793-8512-9fcc961ecc02)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f372a64a-97de-40ae-a450-d2ae678a1838)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/41a30873-cda2-4d7a-8d93-8f8cb5f91cb1)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b8fe144e-b3a0-4c7f-b517-6c8a8fc476e4)

### The Inverter layout in magic
We got the Inverter layout using gitclone. Here we can see How the mask will appear on either nmos or pmos. The parts of inverter and how that parts will be visible in magic console vindow.       
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5aaca5ed-06b6-447f-bd7d-90586fd5588c)
![Screenshot 2024-03-17 231222](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1f71b934-5d87-4388-8b47-fa8fc84a6867)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/53edd419-ed7e-4806-b8e7-9b01db70f346)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ff310968-2d4f-429e-b1f8-ebf3d36b058a)








