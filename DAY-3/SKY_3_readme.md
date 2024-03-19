#  SKY130_D3_SK3 - Sky130 Tech file labs
##  Topics to be covered
**--> Lab steps to create final SPICE deck using Sky130 tech**   
**--> Lab steps to characterize inverter using Sky130 model files**  
**--> Lab introduction to Magic tool options and DRC rules**    
**--> Lab introduction to Sky130 pdk's and steps to download labs**    
**--> Lab introduction to Magic steps to load Sky130 tech-rules**    
**--> Lab exercise to fix poly.9 error in Sky130 tech-file.**    
**--> Lab exercise to implement poly resistor spacing to diff and tap**   
**--> Lab challenge exercise to describe DRC error as geometrical construct** 
**--> Lab challenge to find missing incorrect rules and fix them**


### Spice deck for the CMOS Inverter

Commands for spice extraction of the custom inverter layout in magic tool(tkcon window).

**Check current directory in console window of magic**
pwd

# Extraction command to extract the design into sky130_inv.ext file.
extract all

# Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

# Converting to ext to spice
ext2spice





![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/597e0aa5-335c-4429-bb65-fcb0931e0553)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ccd1a8e1-897e-4b1e-811d-9c1ac5a8251b)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/19be848a-276c-4b2d-8f63-5010d24db2eb)

### characterization of CMOS inverter

![Screenshot 2024-03-18 010002](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/eff93521-dfde-410a-bbb4-d8bf0881cdc2)

![Screenshot 2024-03-18 013529](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/cdf88e88-8480-42a0-9a90-384014b1910f)

![Screenshot 2024-03-18 011207](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b4764917-28c1-42e9-ab29-5f3c27a00af0)


##  Lab introduction to Magic steps to load Sky130 tech-rules
![Screenshot 2024-03-18 152247](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/52726029-5838-419f-86fa-2284177ea4d7)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/81ab0e19-4805-4f92-8e8e-7fce56790d5c)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e75aac88-632f-47b7-82e9-4c3ed5095ee8)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/bbb20f94-f6a4-4992-9771-326fc3134da8)
![Screenshot 2024-03-18 191224](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d1c64d75-cd12-4212-88a7-6c03442735ee)
![Screenshot 2024-03-18 152549](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b81d7902-c3e4-472a-896d-6deb85b14061)
We can see here the metal layer informations--->      https://skywater-pdk.readthedocs.io/en/main/     

![Screenshot 2024-03-18 193317](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d1bc7c98-7493-4f89-8a34-ba01c28be3c0)



## Lab introduction to Magic steps to load Sky130 tech-rules
## Lab exercise to fix poly.9 error in Sky130 tech-file.

There are so many errors in the unfinished implementation of tech files.  
Type load poly in console window. It will show available poly's.  Some incorrect poly are there.   
Check the description of that poly in the below website.  
   https://skywater-pdk.readthedocs.io/en/main/     

![Screenshot 2024-03-18 200148](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/9f218105-8412-4f12-be33-646f6d5006ea)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ee5ee82f-1b81-4d55-bd6f-4d484924431b)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/55b88e34-c950-442a-89e5-aed0b75a8b99)
![Screenshot 2024-03-18 213850](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c436c4a5-0f6d-44ac-87c8-56d36b965a9a)
Is all DRC is Fixed ? No  We fixed just poly to polyres spacing.  
Here you can see again two metal have errors. Which is  diffusion error.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b845966a-337b-4121-83a3-2f5904b0c6f3)



![Screenshot 2024-03-18 205441](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a8042f16-d12f-4ad0-8ee2-2152ebd9b39a)
![Screenshot 2024-03-18 205555](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5a912a45-09f7-4622-95c4-6ceb3a240545)

![Screenshot 2024-03-18 213127](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/47499a78-a21c-4ae3-8a45-f7569686f1df)

![Screenshot 2024-03-18 213342](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1432df61-87f4-458d-b398-61b6726cff63)
