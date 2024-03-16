# SKY130_D1_SK2 - SOC Design and OpenLANE
  ## Introduction to all components of open-source digital ASIC design


  Desigining the ASIC design in automated way requires several things.  
  
  **Hardware description languages**  
  **CAD Tools**  
  **PDK Data (Process design kits)**    
 	
 #### * Hardware description languages  
 
 It is a specialized computer language used to describe the structure and behavior of electronic circuits.  
 There are 100's of RTL designs over the internet. Here are the some sites.
 #### * PDK

 The interface between the designers and Foundries becomes the set of data files or documents.
 This set of files is called Process Design Kit.
 This PDK includes collection of files used to model a fabrication process for the EDA tools used to Design and also
 Process design rules , Device Models, Digital Standard cell libraries, I/O libraries etc..
 
 June30, 2020 Google released the first ever open source PDK.
 This PDK has its own information to design succesful ASIC using open source.
 
 #### * CAD Tools
 
 CAD tools came as a powerful technology that empowers engineers to create highly complex and efficient integrated chip designs.  
 Mianly Used to automate the design.
 
 ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1f1fbbb4-6add-4fa0-85dd-973c94ef3ad7)


 ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/39bdbfda-b220-463a-bfde-1d88a4dadda9)

   

 
 **---->** What kind of performance can we get in 130nm?     
 **-->** is 130nm fast?  
 **Yes**
 
 ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/27ee2a21-11df-47cc-9603-6499e6aae009)
   




##  Simplified RTL2GDS Flow.

   ASIC Design is very tough process that involves many steps. A Methodology is needed to make a succesfull ASIC design. The methodology is implemented using the certain flow.

   ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/69d89be5-c382-4524-86c7-5f88dacb3e44)

   ![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3903a4cd-d696-467c-82f0-c1372ed5be3b)


### --> Synthesis

Synthesis is a process of converting RTL code into gate level netlist.

**Synthesis flow**

1.Read the inputs    
2.Elaborate -Translate the RTL code into gtech cells that are technology independent.    
3.Compile- Generate a netlist mapped to a specific library using command compile_ultra. During the compile ,we add the ICG(integrated clock gating)cells whose information is already provided in the RTL.     
4.Optimization-optimize the design such that it meets the area, power and timing specifications. Synthesis tool give high priority to timing over area and power constraints.     
5.DFT(Design for testability) - perform scan insertion in the optimized design.    
6.Generate output.    

Library building blocks of cells have regular layouts.

Typically the standard cell height is fixed rectangular shape but the width is variable for discrete.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c8cb686a-a817-4aad-a56e-4e1f3ff44575)

### --> Chip Floor Plan

**Floor planning is the art of any physical design. A well and perfect floorplan leads to an ASIC design with higher performance and optimum area.  
Floor planning can be challenging in that, it deals with the placement of I/O pads and macros, the rows on the routing track will define as well as power and ground structure.**

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/81a5b214-fa92-49e1-a125-566ad32a57ab)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/efa71a6f-128e-4441-9d04-13c3d65c74e0)

### --> Power Plan

**Power planning is done to provide uniform supply voltages to all the cells in design the primary objective of power planning is to ensure that all on chip components like blocks, memory, IO cells etc have adequate power and ground connections. there are three levels of power distribution that,   
Rings carries VDD and VSS around the chip.      
Straps carries VDD and VSS  from rings across the chip.     
Rails carries VDD and VSS to the standard cell of VDD and VSS.**    

Such parallel structures of power straps mean to reduce the resistance and IR drop and  to address the Electro migration.
Typically the power distribution network uses the upper metal layers because these metal width's are high compare to lower metal layers.
If width will be more the resistance will be less.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b3007865-135b-418b-acc2-80662ee392c9)


### --> Placement

**Placement is the process of placing the standard cells in the design and also Optimizes the design and determines the routability of the design.**

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2b487d21-16e0-4dcc-8a51-36738ffd6255)

Typically placement is done in two steps

**Global placement followed by detailed placement.**

Global placement tries to find the optimal positions for cells, such positions are not necessarily legal. so cells may overlap or they may avoid rules.  
Detailed the positions obtained from global placement are minimally altered to be legal.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7a68c82e-2614-44c7-acb0-f779ad2ef4ac)

### --> CTS Clock Tree Synthesis

**CTS is used to connect the External Clock to the all internal clock pins of a flipflop. And also inserting a buffer or inverters to all the clock paths in a design to balance the skew.**

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/1601839d-a5b5-4faa-a8d6-10cb7c4b111a)

### --> Routing

Signal routing

**Routing is the process of creating physical connections based on logical connectivity in the netlist file.**

The router uses the available metal layers as defined in the PDK. The PDK defines thickness, pitch , and min width of each metal layers and also defines vias.
The SKYwater PDK defines its routing layers , lowest layers are Titron nitrate layers, and the following 5 layers are aluminium layers.

Most Routers are Grid based routers.
They first construct the routing grids out of the metal layer tracks.
if the routing Grid is Huge then they will follow Divide and conquer method to route the metal laers.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/58e56410-4a53-46c8-a81e-b747e1db4368)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/59785594-1230-46ee-ba29-a17e2c5b5f92)

### --> Sign off

#### * DRC (Design Rule Checking (DRC):

DRC involves verifying that the layout design conforms to the geometric design rules specified by the semiconductor fabrication process. These rules define minimum widths, spacing, overlaps, and other layout parameters necessary for successful manufacturing. DRC ensures that the design does not violate these rules, which could lead to defects during fabrication.

#### * LVS (Layout vs. Schematic Checking) :

LVS compares the layout design (physical representation) of the circuit with its schematic (logical representation). It verifies that the physical layout matches the intended circuit connectivity specified in the schematic. LVS ensures that there are no errors such as missing connections, shorts, or open circuits that could affect the functionality of the IC.


#### * STA (Static timing analysis)

It is a method of validating the timing performance of a design by checking all possible paths for timing violations.
The main goal of static timing analysis is to verify that despite these possible variations, all signals will arrive neither too early nor too late, and hence proper circuit operation can be assured. Since STA is capable of verifying every path, it can detect other problems like glitches, slow paths and clock skew.





##  Introduction to OpenLANE and Strive chipsets

**About OpenLANE Asic flow**
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2e3e3299-fb60-4c67-8f49-b3f3029e041d)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a824bc59-85de-4451-9675-7b3a3a0f188f)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/37fcc522-474a-41eb-9faa-3c1072ffd859)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c05fc1ec-b87e-4638-8643-a2c2511eee56)





## Introduction to OpenLANE detailed ASIC Design flow


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8a173daa-5151-4b35-a28d-70cfb654fde5)

OpenLANE is based on several open source projects. such as below

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/baf9654f-d0fe-4c39-8b81-4866bae0be15)

**RTL synthesis**

RTL is fed to **yosys** with the design constraints yosys translates the RTL into logic circuits using engineering components this ckt can be optimized and mapped into cells in standard cell library using **ABC**, this ABC has to be guidedduring the optimization.

The different designs can use different stratergies to achieve the design targets , for that we have **synthesis exploration** that can be used to generate the report, that shows how the design delay on the area.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a9e295dd-437c-4d4c-9c32-80c0e51ca8f2)

Also OpenLANE has **design exploration** utility which can be used to sweep design configurations.
we have 16 configs , the report is looks like below,  
This report is very useful to find the best config for OpenLANE.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/dd412617-aef6-4e18-8cea-49513dab7998)

Also design exploration can be used to OpenLANE regression testing.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e1313290-aeaf-4fbb-bfa4-5e5f8972aefc)

**DFT (Design for Testablility)**

After fabrication we can enable this to test the device. This step add extra logic to the ckt without modifying the original functionality.
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3171c4e5-0cef-4936-8a69-fc33d091bacf)

**Physical implementation**

It includes several steps, all of them are doing by **openroad**.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f1fc9411-aba4-47c6-93c1-ef68f87d9418)

**LEC**
If they are not equivalent, eventually the optimization is something wrong.
 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/21304e08-bb10-4692-bab7-78268e540d7e)

During physical implementatio we have a special step that is Fake antenna diodes insertion.

This is required to address the antenna diode violations.

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/759add7f-f611-40e2-bcb3-5ac5ca0635d9)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f230c2e3-d799-4b41-9459-791b45158daf)


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/91066508-bec3-4c79-9215-032d23f678a6)


**STA**


![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2375b7a8-576d-4b2c-baa2-5ad4be6e1207)

**Signoff**

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/91b8b267-a303-4875-86e9-8d4c2f90b387)
