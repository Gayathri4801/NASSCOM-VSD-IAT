## Setup timing analysis with real clocks.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ea6a8883-470a-4934-b9cb-9b5694d4d8fa)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d9e04865-f8d3-4969-9b0d-7b169ed41ffc)
delta 1 is launch flop clock Network delay. (delta 1 = 1+2).   Time required for the clk signal to reach the clock starting point to launch clock path end point.  
delta 2 is capture flop clock Network delay. (delta 1 = 1+3+4). Time required for the clk signal to reach the clock starting point to capture clock path end point.   
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/7303fff5-62d4-45bc-ac56-da3491a95e5f)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e634861b-14a9-43bd-9881-0c2a51a3ede5)

Any circuit on thip satisfying this particular eqution is ready to work 0n 1Ghz.  
If is voilates this equation , slack will become negative. Slack we will expect as positive or 0.  
Slack = Data required time - Data arrival time    
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3270617f-986e-499c-bfac-95a19857d179)


## Hold Analysis    
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b4377e23-e14a-4497-aa21-af812dad330e)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/61ff82aa-e15c-4c78-b9c6-9f0d05efdb0a)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/68f4ee1b-3460-4d2c-9a0a-b20caeb9d96d)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/ddd79083-1df9-49e9-ae58-a3ac441d3243)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/e29a8027-0fc1-4cda-8bc4-dc15b9508a77)

Setup slack = T+ T skew(delta2(-x%) - delta1 (+x%) )- T setup2- Setup uncertainty+CPPR - (Tcomb(+x%) + Tcq(+x%))    
Hold slack = (Tcomb(-x%) + Tcq(-x%))-  Hold2- T skew(delta2(+x%) - delta1 (-x%) )-  Hold uncertainty+CPPR     
