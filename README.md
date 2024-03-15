# Advanced- Physical design using openLANE - Sky130

This repository is dedicated to showcasing the projects completed during a 5-day workshop on Advanced Physical Design using OpenLANE/SkyWater130. 
## About the Workshop

The workshop is focused on providing hands-on experience with OpenLANE, a VLSI (Very Large Scale Integration) design flow tool, and the Skywater 130nm Process Design Kit (PDK). OpenLANE automates the process of designing integrated circuits, aiming to produce clean GDSII output without needing much human intervention. Throughout the workshop, participants work with PicoRV32 it is a CPU core that follows the RISC-V RV32IMC Instruction Set Architecture, to understand the design flow concepts.
###  Topics to be covered in this workshop

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/9a052919-c3eb-4a8c-948d-2980010238ff)
		
# DAY1 -   Inception of open-source EDA, OpenLANE and Sky130PDK
##  SKY130_D1_SK1 - How to talk to computers
###  SKY_L1 - Introduction to QFN-48 Package, Chip, pads, core, die and Ips
#### 	• Fundamental Terminologies:-
1. **Wire bonds** 

     wire bonds are thin wires that connect the semiconductor die (chip) to the leads of the package, enabling electrical signals to travel between the chip and the external world. So that we will be able to transfer the signals between chip and outside the world.
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1976bcec-4565-4315-aaf0-2849ad1aaf35)

2.	**Pads**

    Pads are the metal areas on the surface of an integrated circuit (IC) where external connections, such as wires or solder balls, are attached. These pads serve as contact points for connecting the IC to other components or circuitry, facilitating the transfer of electrical signals or power.By using this pads we can send the signals through the pads inside the chip.

3.	**Foundry IP's**
   
    Foundry - It is a place with set of machines, where the actual chips get manufactured.
    Generally we will give the whole design layout (Tapeout or GDS file) to the foundry, Foundry will manufacture the chip for us.

  	Foundry IPs (Intellectual Properties) are pre-designed and pre-verified components provided by semiconductor foundries to their customers. These components are essential building blocks for designing integrated circuits (ICs) and include standard functions such as memory blocks, input/output interfaces, and various analog and digital circuitry. Foundry IPs help designers by providing a a set of building blocks that can use to create Digital circuit designs without having to design every logic function from scratch.
  	
      **Examples** :-	Memory blocks (e.g., SRAM, ROM), interface IPs (e.g., USB, PCIe, HDMI), and analog IPs (e.g., PLLs, ADCs, DACs).

    Companies will take these foundry IP's and design their own design with some extra things and then they will send it to foundry , foundry will manufacture the IC.

4.  **Macro**
   
    A pre-designed and pre-verified functional block that performs a specific task within an integrated circuit (IC). Macros are typically larger than standard cells and can include complex functions such as arithmetic units, memory blocks, or interface controllers. Integrating macros into a chip design allows designers to save time and effort by using pre-designed and thoroughly tested functional blocks, rather than designing these functions from scratch.
    
    Examples :- Graphics Processing Unit (GPU), Digital Signal Processor (DSP), Image Signal Processor (ISP) .. etc.
				
    #### The key difference is that a macro is a specific function within a chip design, while foundry IP encompasses pre-designed components provided by semiconductor foundries for general use in various chip designs.

5. **Die**

     A die, is a small, rectangular piece of semiconductor material (usually silicon) on which the integrated circuit (IC) is fabricated. A die can contain any number of cores.

  ![Screenshot 2024-03-13 231000](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c493209b-b323-4b7e-b66a-80204a523b36)

  #### A Typical chip consists below parts as shown in fig.
  
  ![Screenshot 2024-03-13 233620](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/98a68a35-53bb-4554-ae04-9756d4e01277)


## SKY_L2 - Introduction to RISC - V

  If the user is giving the specifications or instructions to the computer in the C language , the computer will not be able to understand the c language. we have to make this c program needs to be run on particular layout (Hardware). For this we need to pass this c program to particular hardware in certain terms.

  The steps that follow is :-
  
  C program is first compiled in it's assembly language which is nothing but RISC-V assembly language.  
  Then it is converted into machine language also known as binary language(1's & 0's) which is understood by the hardware of the computer (Layout).  
  Finally this 1's & 0's gets executed in the particular layout. We will get the required output.

  ![Screenshot 2024-03-13 235648](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f1322479-71f8-478d-a1a8-3e0cc868cb9b)


  There will be another interface required that needs to be present between RISC-V and Layout That is known as Hardware description language.
  This means we need to create or implement this RISC-V specifications in terms of RTL. This RTL output will fed to the Hardware(Layout).

  ![Screenshot 2024-03-13 235711](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5ee873fa-3b2a-48bc-b38b-fd4587ffaa12)


  ### SKY_L3 - From Software applications to Hardware

  Applications(Apps) which we are used in day do day life. These apps are actually run in Mobile or Laptop.  
  How these applications are working?

  Example :- Suppose we are using the stopwatch. Whenever we click on start button it will start working and if we click stop button it will stop. How is it possible? 
  
  The steps that follow to give requird output is :-

  First The application software enters into a system software. This system software will convert into machine language.  
  The flow of system software works as 

**OS (Operating System)**'  
**Compiler**  
**Assembler**  

  The output of OS is small functions in the C, C++, JAVA.  
  These will taken by the respective compiler and converted into instructions.  
  The syntax of this instructions will depend upon the Hardware we used. This Hardware belongs to anything like Intelx86,  RISC-V, MIPS.  
  If the hardware belong to RISC-V then the instructions format also belongs to RISC-V.  
  Then the Assembler will take the instructions and converted into binary or machine language.  
  That machine language will fed into the hardware (Layout) ,then It will give the required output.  

  ![Screenshot 2024-03-14 174728](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c9d64257-6b2b-4d26-b5f5-5aa402a6c095)

  ![Screenshot 2024-03-14 174832](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/6d73a8d9-59b5-4a53-8f3b-7d862410a28c)

  ![Screenshot 2024-03-14 175052](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/4b3f18a0-8b3c-4420-a2be-d574988ed17d)

    

  ## SKY130_D1_SK2 - SOC Design and OpenLANE
  ###  SKY_L1 -  Introduction to all components of open-source digital ASIC design


  Desigining the ASIC design in automated way requires several things.  
  
  **Hardware description languages**  
  **CAD Tools**  
  **PDK Data (Process design kits)**    
	

 ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1f1fbbb4-6add-4fa0-85dd-973c94ef3ad7)

 There are 100's of RTL designs over the internet. Here are the some sites.

 ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/39bdbfda-b220-463a-bfde-1d88a4dadda9)

 #### Hardware description languages  
 
 It is a specialized computer language used to describe the structure and behavior of electronic circuits.  
 #### PDK

 The interface between the designers and Foundries becomes the set of data files or documents.
 This set of files is called Process Design Kit.
 This PDK includes collection of files used to model a fabrication process for the EDA tools used to Design and also
 Process design rules , Device Models, Digital Standard cell libraries, I/O libraries etc..
 
 June30, 2020 Google released the first ever open source PDK.
 This PDK has its own information to design succesful ASIC using open source.
 
 #### CAD Tools
 
 CAD tools came as a powerful technology that empowers engineers to create highly complex and efficient integrated chip designs.  
 Mianly Used to automate the design.  
 
 What kind of performance can we get in 130nm?  
 is 130nm fast?
 **Yes**
 
 ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/27ee2a21-11df-47cc-9603-6499e6aae009)
   




##  SKY_L2 - Simplified RTL2GDS Flow.

   ASIC Design is very tough process that involves many steps. A Methodology is needed to make a succesfull ASIC design. The methodology is implemented using the certain flow.

   ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/69d89be5-c382-4524-86c7-5f88dacb3e44)

   ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3903a4cd-d696-467c-82f0-c1372ed5be3b)


### Synthesis

Synthesis is a process of converting RTL code into gate level netlist.

Synthesis flow
1.Read the inputs
2.Elaborate -Translate the RTL code into gtech cells that are technology independent.
3.Compile- Generate a netlist mapped to a specific library using command compile_ultra. During the compile ,we add the ICG(integrated clock gating)cells whose information is already provided in the RTL.
4.Optimization-optimize the design such that it meets the area, power and timing specifications. Synthesis tool give high priority to timing over area and power constraints.
5.DFT(Design for testability) - perform scan insertion in the optimized design.
6.Generate output.

Library building blocks of cells have regular layouts.

Typically the standard cell height is fixed rectangular shape but the width is variable for discrete.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c8cb686a-a817-4aad-a56e-4e1f3ff44575)

### Chip Floor Plan

Floor planning is the art of any physical design. A well and perfect floorplan leads to an ASIC design with higher performance and optimum area.

Floor planning can be challenging in that, it deals with the placement of I/O pads and macros, the rows on the routing track will define as well as power and ground structure.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/81a5b214-fa92-49e1-a125-566ad32a57ab)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/efa71a6f-128e-4441-9d04-13c3d65c74e0)

### Power Plan

power planning is done to provide uniform supply voltages to all the cells in design the primary objective of power planning is to ensure that all on chip components like blocks, memory, IO cells etc have adequate power and ground connections. there are three levels of power distribution that
Rings carries VDD and VSS around the chip 
Straps carries VDD and VSS  from rings across the chip 
Rails carries VDD and VSS to the standard cell of VDD and VSS

Such parallel structures of power straps mean to reduce the resistance and IR drop and  to address the Electro migration.
Typically the power distribution network uses the upper metal layers because these metal width's are high compare to lower metal layers.
If width will be more the resistance will be less.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b3007865-135b-418b-acc2-80662ee392c9)


### Placement

placement is the process of placing the standard cells in the design and also Optimizes the design and determines the routability of the design.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2b487d21-16e0-4dcc-8a51-36738ffd6255)

Typically placement is done in two steps

Global placement followed by detailed placement.

Global placement tries to find the optimal positions for cells, such positions are not necessarily legal. so cells may overlap or they may avoid rules.
Detailed the positions obtained from global placement are minimally altered to be legal.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7a68c82e-2614-44c7-acb0-f779ad2ef4ac)

### CTS Clock Tree Synthesis

CTS is used to connect the External Clock to the all internal clock pins of a flipflop. And also inserting a buffer or inverters to all the clock paths in a design to balance the skew.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1601839d-a5b5-4faa-a8d6-10cb7c4b111a)

### Routing

Signal routing

Routing is the process of creating physical connections based on logical connectivity in the netlist file.

The router uses the available metal layers as defined in the PDK. The PDK defines thickness, pitch , and min width of each metal layers and also defines vias.
The SKYwater PDK defines its routing layers , lowest layers are titanium nitrate layers, the following 5 layers are aluminium layers.

Most Routers are Grid based routers.
They first construct the routing grids out of the metal layer tracks.
if the routing Grid is Huge then they will follow Divide and conquer method to route the metal laers.


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/58e56410-4a53-46c8-a81e-b747e1db4368)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/59785594-1230-46ee-ba29-a17e2c5b5f92)

### Sign off

DRC LVS STA

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1b2e4cd3-98f6-49a6-9b58-5e1d93b7d0f4)




###  SKY_L3 - Introduction to OpenLANE and Strive chipsets

About OpenLANE Asic flow
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2e3e3299-fb60-4c67-8f49-b3f3029e041d)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a824bc59-85de-4451-9675-7b3a3a0f188f)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/37fcc522-474a-41eb-9faa-3c1072ffd859)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c05fc1ec-b87e-4638-8643-a2c2511eee56)



###  SKY_L4 - Introduction to OpenLANE detailed ASIC Design flow




![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8a173daa-5151-4b35-a28d-70cfb654fde5)

OpenLANE is based on several open source projects. such as below

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/baf9654f-d0fe-4c39-8b81-4866bae0be15)

RTL synthesis
RTL is fed to yosys with the design constraints yosys translates the RTL into logic circuits using engineering components this ckt cna be optimized and mapped into

cells in standard cell library using ABC, this ABC has to be guidedduring the optimization.

The different designs can use different stratergies to achieve the design targets , for that we have synthesis exploration that can be used to generate the report, that shows how the design delay on the area

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a9e295dd-437c-4d4c-9c32-80c0e51ca8f2)

also OpenLANE has design exploration utility which can be used to sweep design configurations.
we have 16 configs , the report is like below

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/dd412617-aef6-4e18-8cea-49513dab7998)

This report is very useful to find the best config for OpenLANE.

Also design exploration can be used to OpenLANE regression testing.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e1313290-aeaf-4fbb-bfa4-5e5f8972aefc)

DFT
After fab we can enable this to test the device. This step add extra logic to the original.
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3171c4e5-0cef-4936-8a69-fc33d091bacf)

Physical implementation

Several steps all of them are doing by openroad

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f1fc9411-aba4-47c6-93c1-ef68f87d9418)

LEC
 if they are not equivalent, eventually the optimization is something wrong.
 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/21304e08-bb10-4692-bab7-78268e540d7e)

During physical implementatio wehave a special step that is Fake antenna diodes insertion.

This is required to address the antenna diode violations.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/759add7f-f611-40e2-bcb3-5ac5ca0635d9)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f230c2e3-d799-4b41-9459-791b45158daf)


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/91066508-bec3-4c79-9215-032d23f678a6)


STA


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2375b7a8-576d-4b2c-baa2-5ad4be6e1207)

Signoff

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/91b8b267-a303-4875-86e9-8d4c2f90b387)


## SKY130_D1_SK3 - Get familiar to open-source EDA tools
###  SKY_L1 -  OpenLANE Directory structure in detail

the tool which we will wrok is OpenLANE,  OpenLane is a not a tool, it is basically flow  which compraises of many open-source EDA tools.
OpenLANE is used to produce RTL2GDS

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d8c225c2-16fe-470d-9283-c2ad450ad0b3)

![Uploading image.png…]()



