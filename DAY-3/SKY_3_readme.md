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

## Lab steps to git clone vsdstdcelldesign

To clone the gitlink the command used here is,  
/Desktop/work/tools/openlane_working_dir/openlane$ git clone https://github.com/nickson-jose/vsdstdcelldesign.git   

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/20659235-0170-42cf-adb0-10535788ec92)

### The Exploration for Inverter layout in magic    

By using this command we got the vsdstdcelldesign directory.  
/Desktop/work/tools/openlane_working_dir/openlane$ git clone https://github.com/nickson-jose/vsdstdcelldesign.git   

Now change the directory to the vsdstdcelldesign using cd vsdstdcelldesign.
Then the terminal will show the path ---> /Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign$.     
Then check the list of contents using ls command. 
using sky130A.tech file we can see the inverter layout in magic.   
**Command to open custom inverter layout in magic**
magic -T sky130A.tech sky130_inv.mag &

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ef0e6b12-00da-43a9-80d8-c0202163a7dc)

We got the Inverter layout using gitclone. Here we can see How the mask will appear on either nmos or pmos. The parts of inverter and how that parts will be visible in magic console vindow.       
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5aaca5ed-06b6-447f-bd7d-90586fd5588c)
![Screenshot 2024-03-17 231222](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1f71b934-5d87-4388-8b47-fa8fc84a6867)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/53edd419-ed7e-4806-b8e7-9b01db70f346)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ff310968-2d4f-429e-b1f8-ebf3d36b058a)


## Spice extraction of CMOS inverter in magic tool.  
### Commands for spice extraction of the custom inverter layout in magic tool(tkcon window).

**Check current directory in console window of magic**   
pwd

**Extraction command to extract the design into sky130_inv.ext file**   
extract all   

**Before this ,We will use sky130_inv.ext file to create the spice file to be used with our ngspice tool.**   
ext2spice cthresh 0 rthresh 0   

**Converting to ext to spice**   
ext2spice


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3911b87e-8846-447e-82b1-f6d89bdc45d4)


## creating final SPICE deck using Sky130 tech   

The default file of SPICE deck using Sky130 tech we can see below,

![Screenshot 2024-03-17 233834](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/533e809c-242d-46f4-9c86-7e74fb521fe6)

The final file of SPICE deck using Sky130 tech we can see below,
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/597e0aa5-335c-4429-bb65-fcb0931e0553)

## Commands for ngspice simulation

### Command to directly load spice file for simulation to ngspice
ngspice sky130_inv.spice  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ccd1a8e1-897e-4b1e-811d-9c1ac5a8251b)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/19be848a-276c-4b2d-8f63-5010d24db2eb)

## Characterization of CMOS inverter

**Here we will calculate Rise time delay, Fall time delay and Propogation delay for the CMOS inverter output.**  

![Screenshot 2024-03-18 010002](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/eff93521-dfde-410a-bbb4-d8bf0881cdc2)

![Screenshot 2024-03-18 013529](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/cdf88e88-8480-42a0-9a90-384014b1910f)

![Screenshot 2024-03-18 011207](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b4764917-28c1-42e9-ab29-5f3c27a00af0)


##  Lab introduction to Magic steps to load Sky130 tech-rules

Here, we will see more about Sky130 tech-rules mainly DRC. 
First we have to download drc_tests.tgz file. Iused below command to get that zip file.  

wget -P /tmp http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz && chmod +x /tmp/drc_tests.tgz   
cd /tmp
tar xfz drc_tests.tgz

vsduser@vsdsquadron:~$ cd /tmp
vsduser@vsdsquadron:/tmp$ cd drc_tests
vsduser@vsdsquadron:/tmp/drc_tests$ ls -ltr
vsduser@vsdsquadron:/tmp/drc_tests$ magic -d XR

It will launch the magic tool , we can see below how the console window will appear,  

![Screenshot 2024-03-18 152247](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/52726029-5838-419f-86fa-2284177ea4d7)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/81ab0e19-4805-4f92-8e8e-7fce56790d5c)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e75aac88-632f-47b7-82e9-4c3ed5095ee8)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/bbb20f94-f6a4-4992-9771-326fc3134da8)
![Screenshot 2024-03-18 191224](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d1c64d75-cd12-4212-88a7-6c03442735ee)
![Screenshot 2024-03-18 152549](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b81d7902-c3e4-472a-896d-6deb85b14061)
We can see here the metal layer informations--->      https://skywater-pdk.readthedocs.io/en/main/     

![Screenshot 2024-03-18 193317](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d1bc7c98-7493-4f89-8a34-ba01c28be3c0)


## Lab exercise to fix poly.9 error in Sky130 tech-file.

There are so many errors in the unfinished implementation of tech files.  
Type load poly in console window. It will show available poly's.  Some incorrect poly's are there.   
Check the description of that poly in the below website.  
   https://skywater-pdk.readthedocs.io/en/main/     

![Screenshot 2024-03-18 200148](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/9f218105-8412-4f12-be33-646f6d5006ea)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ee5ee82f-1b81-4d55-bd6f-4d484924431b)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/55b88e34-c950-442a-89e5-aed0b75a8b99)
![Screenshot 2024-03-18 213127](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/47499a78-a21c-4ae3-8a45-f7569686f1df)

![Screenshot 2024-03-18 213342](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1432df61-87f4-458d-b398-61b6726cff63)

![Screenshot 2024-03-18 213850](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c436c4a5-0f6d-44ac-87c8-56d36b965a9a)
Is all DRC is Fixed ? No  We fixed just poly to polyres spacing.  
Here we can see again two metal have errors. Which is  diffusion error.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b845966a-337b-4121-83a3-2f5904b0c6f3)



