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

