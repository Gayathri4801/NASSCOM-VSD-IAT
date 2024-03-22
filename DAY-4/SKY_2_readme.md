#  SKY130_D4_SK2 -Timing analysis with ideal clocks using openSTA
##  Topics to be covered
**--> Setup timing analysis and introduction to flip-flop setup time**   
**-->Introduction to clock jitter and uncertainity**  
**--> Lab steps to configure openSTA for post-synth timing analysis**    
**--> Lab steps to optimize synthesis to reduce setup violations**    
**--> Lab steps to do basic timing ECO**    



Typical Ideal clock scenario to identify setup time.   
**Setup Time -->** Setup time is the minimum amount of time before the clock edge that the data input
must be stable and not change to ensure correct data is latched by the clock edge.   
**Hold Time -->** Hold time is the minimum amount of time after the clock edge during which the data
input must remain stable after the clock edge has occurred.   

Ideal clock network : the clock tree is not yet build.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/63308581-2598-47bc-bad5-f81afa1e04cf)
The data should reach capture flop within the time period.   
This below picture says it will operate at 1Ghz frequency.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f42f9007-358b-496e-8680-6ad178bc30df)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3b32c2a9-a0d1-49dc-9d36-79be4ceb733f)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3a41ded1-cf58-477a-901c-d5945f00a1b7)

## Introduction to clock jitter and uncertainity   

Clock is being prepared by phase-locked loop (PLL).   These circuits might not provide exact clock source. some variations will be there.  Ideally the clock change at exactly particular time period. But because of some in built variation in clock circuit it will change before or after.   
**Jitter** --> Clock jitter refers to the variation in the timing of a clock signal's pulses.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/64f82c17-5fe0-4141-a663-e85935eb57b1)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5eeb1cd1-b8d2-4d2e-9573-fe3e4e060459)

Here teta = Combinational delay. It should be less than 0.9ns.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/477c754a-665c-4761-a3a0-161f94ba1c67)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/dadbb188-c03a-4e3e-9901-378d2019e0e3)
