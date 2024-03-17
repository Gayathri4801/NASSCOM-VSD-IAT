#  SKY130_D2_SK4 - General Timing Characterization Parameters
##  Topics to be covered
**--> Timing Threshold Definitions**   
**--> Propgation delay and Transition time** 

From this types of characterization we will understand various syntax and what it represents. This syntax is very important to understand the GUNA software.   
GUNA software works on variables. These variables are available with us in order to fed into the software.  
![Screenshot 2024-03-17 113639](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/01e8e5b9-76a0-43d6-8e1d-3fa75ce693b7)

**Propogation Delay**  
The time difference between when the transitional input reaches 50% of its final value and when the output reaches 50% of its final value.   
Dealy = output time threshold - input time threshold

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f27dfd23-d292-486e-a1be-4a9aaef24b5e)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/f8b77712-eb6d-4e28-b474-995abea1a5c5)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/36bd2835-20d5-4071-872c-ff94f63b7a1b)

Here we can see negative delay, It is not correct because negative delay is not expected. we need positive delay. we can see in above images.  
The reson behind this negative delay is poor choice of threshold points. Choosing the threshold points is very important. 

**Transition Time**

The transition is the time it takes for the pin to change state. 
When we calculate the transition time it should always high -low. 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/0e9a074a-213f-43f1-befc-ce42eeeb174e)
