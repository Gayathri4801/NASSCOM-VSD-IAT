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
