#  SKY130_D2_SK1 - Chip Floor Planning considerations
##  Topics to be covered
**--> Utilization factor and aspect ratio**   
**--> Concept of Pre-placed cells**  
**--> De-coupling Capacitors**    
**--> Power Planning**    
**--> Pin Placement and logical cell placement blockage**    
**--> Steps to run Floorplan using OpenLANE**    
**--> Review Floorplan files and steps to view floorplan**   
**--> Review Floorplan layout in magic**   



**Floorplan Steps**   
1. Decide width and height of Core and Die.  
2. IO pad sites are created for placement of IO pad .  
3. Placement of macros.   
4. The standard cell rows created for standard cell placement.      
5. Power planning (pre routing).    
6. Adding physical only cells.    
7. Placement of Blockages.    

##  Decide width and height of Core and Die.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b081bd4b-6cfb-4c42-9ada-a2213b38ac33)

We will begin with the basic Netlist.  
Netlist --> It is a combination of sequential elements and its logical connectivity.  
Here we will start with 2 Flipflops that is launch flop and Capture flop and some combinational logic in between them.
This is an example to identitify width & Height of Core and Die. And then this can be extrapoleted to millions of gates.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e8f4a6fc-bb59-4e6a-bd58-71c7c22f98cc)
While defining the dimensions of the chip we will mostly dependent on the dimensions of the logic gates / standard cells not the wires.  Wires will play important role in further stages.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/6f0ef562-fb05-4f93-93cc-97db2496ef38)

Now let's give rough dimensions for each standard cell,  and calculate area occupied by the below netlist on a silicon wafer.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/78c13616-0172-4d7d-b9b0-f46d950bea94)

Before this lets remove all wires, and place all in one plate. Now calculate the total area.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/53867dff-37e4-4e2d-8674-9c39f2a7714d)

Now we have rough calculation of the area for this netlist. Here, The min area occupied by the netlist wherever it is placed is **4 sq.unit**.  

#### Now what is Core & Die section of a chip?   

We can see here,
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/27241ff1-e5d1-4cfb-a6a1-73b99a0b24ee)

Our circuit should build inside this piece of area. Our circuit should not exceed this area.  
If the logic is completely fit in the core area, there is no space is left to place the other cells , then the Utilization factor is 100%. If there is some place then this utilization factor will change. 

### Utilization Factor

It will define the area occupied for placement of Standard cells, Macros and other cells.   
If U.F = 0.8    80% is used for placing the cells   
							  20% is used for routing   
Core Utilization = (macros area + std cell area +other cells area)/ total core area   
Die Utilization = (Core area+ IO area)/ total Die area.

![Screenshot 2024-03-16 123404](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/983b5131-eb23-4621-bfda-f32d71f14c59)

If we say U.F is 1 that means the core is completely filled, no space to place other cells.   

Ideally we don't go for 100% Utilization , we go for 50% or 60%. U.F is 0.5 or 0.6.   


### Aspect Ratio

It decides the size and shape of a chip or block.  
It is the ratio of height and width or Number of horizontal routing resources/ Number of Vertical routing resources.   
A.R >1   Height will be more   
A.R <1   Width will be more   
A.R =1   Square shape.   

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/61aafbce-63b1-4a5e-a0a1-e8bdb136c2aa)

![Screenshot 2024-03-16 124715](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/bcad2a39-cad8-4a4f-ac40-2ede5130380d)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/6285fc85-8a1f-45c7-a2db-6c8fd3dc206a)

It says that out of complete area of chip, 25% of our chip is occupied with the initial netlist which is completely connected by idle wires which don't have any shape or sze. Remaining 75% is available for all placing additional cells only.

## Pre-Placed Cells

These will be implemented once and can be instantiated multiple times. These are part of netlist they receive some inputs and they deliver output, but the functionality of this cells implemented only once. That's we called as **Pre-Placed cells**,because this cells are being place only once in a chip. We have to define location and the arrangements of particular cells, this has to be done before actual placement and routing.These cells placement on a top level chip will be fix. PNR tools not touch this locations of these cells, once their locations are fixed on floorplanning, they are fixed. They are not moved by any automated tools and also Further steps will not touch locatons of these cells.  
These cells can be Macros or IP's which have complex logic.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f9e735f6-18f7-4253-a2bb-7004cc357ba9)

Lets take an example of combinational logic, The assumption of this comb logic is it does some amount of function like mux, clock divider, memory, multiplier..  
Here, the output of comb ckt is a huge ckt (50K gates or many more).

![Screenshot 2024-03-16 144459](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/13a499bc-0b75-49c6-a2d8-9b49c097fe18)

![Screenshot 2024-03-16 145149](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/252ee79f-7083-48c5-ad94-d12719752b51)

Blockbox the boxes means it is invisible for one who is looking into top.   

![Screenshot 2024-03-16 145524](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5ce403d3-6554-4b59-9c75-ef3a5b9d6c4d)

we didn't implement this multiple times, we just implemented once and the we reused the. This is the concept of reused models, where we have this small models that can be used reuse seperately in the Top netlist.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2c7d84da-f84a-486d-9de8-927f1087c624)

![Screenshot 2024-03-16 152612](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/44033088-9f3e-425f-ab9a-b5bffb741dc7)

With this Defining the locations of Pre-placed cells are finished.

## De-coupling Capacitors

We have to surround the pre-placed cells with the de-coupling capacitors.

It is a part of ckt belongs to Block A, Block B or Block C. The o/p of cells in this circuit switches from 0 to 1,for that there is an amount of current demand that it needs What happens here is there is small capcitor is setting at the o/p, whenever transition happen from 0 to 1 the capacitor has to completely charge to represent logic 1. The amount of charge to this cap will be send by supply voltage. So it is a responsibility of supply voltage to send necessary supply current to this logic and all the other logics wherever the transition is happening from 0 to 1. Also whenever any piece of ckt switches the logic 1 to 0,it is a responsibility of GND to take that amount of charge.  
Transition 0 to 1 caps which are present in ckt will charge up
Transition 1 to 0 caps which are present in ckt will discharge , this discharging current should be well handled by supply and GND.  

In reality when the power supply flow from a piece of ckt there will be a some amount drop due to wire resistance. why because these wires are physical wire and got physical dimensions. Anything that has got physical dimensions will have resistance, capacitance and inductance that is associated with it.  

![Screenshot 2024-03-16 154953](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7b436aff-9806-4d5b-9989-43d62c712bf4)

![Screenshot 2024-03-16 155609](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/443aa785-1d76-41df-90ed-b25b06b70501)

![Screenshot 2024-03-16 155620](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/454746cc-a39c-42c5-97d6-3e21ab57e6fc)

If Expected logic is 1. We can't guarantee whether we will be getting 1 or not. That is the problem of having long physical distance from the power supply to this piece of ckt.  

we can avoid this issue with the help of **De-coupling capacitors**.

De-coupling capacitors is huge cap which is filled with the charge. The voltage stored in this De-cap is equivalent to the supply voltage. If the power supply is 1V the De-cap has been charge till 1V.  
Whenver the piece of the ckt switches the ckt gets the current from the De-cap that's why we will place De-caps close to the ckt.
This De-cap decouples the ckt from the main supply. Whenever the charge is discharged in the De-cap it will charge up by the power supply.

![Screenshot 2024-03-16 161135](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5a8c57c2-31ae-486a-8e04-6a67238d31c0)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5295bad7-8f8c-4b65-b095-285aceaf0ad1)
Now these blocks will behave there will be no switching activity that will get missed, there won't be any crosstalk issues.  

With this we have done with the local communication.  

## Power Planning  

![Screenshot 2024-03-16 163500](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/57921819-0c7a-44ab-a509-3e29d3f9626f)

![Screenshot 2024-03-16 164410](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d2d03d1a-d34a-4927-beb2-03fc3d62d3a0)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/cb994969-cf33-4bae-a3ab-d102426eeb7d)

![Screenshot 2024-03-16 165244](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/483058eb-8956-4c13-bf0c-41f80de3ff5f)

![Screenshot 2024-03-16 170535](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/40d8e45b-303f-43d8-ac54-138bf2f9be09)

If we see here, the problems we are discussing here, these are coming due to one reason. The reason is the power supply is being provided from only one point. If there is multiple power supplies each cap will look into nearest supply and get the supply from it. It is the exact solution for this. We can see her how we can provide multiple power domains.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/be770c0a-a383-4316-8631-28d0888e123e)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f8a0ac8f-d10f-449b-a12d-562a4b2b3688)


##  Pin Placement and logical cell placement blockage

Generally the trend of pin placement is all input pins at the right side, All output pins are at the left side. But it might vary from design to design. We can place at the bottom and top also.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a5984281-0b62-4cbd-a1b7-97babed8bc9c)

Here two things to observe,   
1. ordering of the inputs ports are random similarly for o/p ports also. The reason is , it is depend upon where we place the cells.
Make sure all I/O ports are placed in IO region. A complete knowledge of the design is necessary/important to understand the pin placement. this basically creates the hand checking between frontend and backend. Frontend people one who defines the netlist connectivity and backend team has to decide the pin placement.  
2. Here we can see clock ports are bigger compare to data ports because clock ports are the ports which is driving all the cells continuously.
So we need less resistance path for clock paths. bigger the sixe lower the resistance. Make sure least resistance for clock paths.  Next make sure no other cells can be placed in the IO area.

![Screenshot 2024-03-16 174452](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/953c1715-e47b-41eb-9c32-7f6972836167)

## Steps to run Floorplan using OpenLANE

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/258fa66a-2dd5-49a0-aef1-eb05050d2465)

Floorplan.def file

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7242019d-3da3-494e-a757-a2c4250e837c)

![Screenshot 2024-03-16 204405](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d76c0e47-339e-4f65-ad83-03570de944b7)


If we want change anything in floorplan, we need to make changes in design related config file.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d3ad54f3-b96d-465f-9ad0-f7d6306b08d3)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ae9e2ce9-05a5-4990-b53c-0b08a385b28f)

The metal layer information, we can see here  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/02ac76da-e05a-4be9-8d40-4aa5febb6525)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/80ad671a-2216-410c-b2ec-5c7d7bf37da4)

