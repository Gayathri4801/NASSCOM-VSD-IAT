# TritonRoute Features 
##  Topics to be covered
**--> TritonRoute feature 1- Honors pre-processed route guides**   
**--> TritonRoute Feature2&3 - Inter-guide connectivity and intra- & inter-layer routing**    
**--> TritonRoute method to handle connectivity**     
**--> Routing topology algorithm and final files list post-route**

**TritonRoute is a engine which is used for detailed routing**  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8ae3eb9b-cd03-4b2a-aa02-42e54fa8f143)
Via connection won't happen  when lower layers routing taken place. Only it will happen when upper layers routing taken place.   

**pre-processed route guides**

1. M1 preferred direction is vertical. Whenever the tool determines/encountered the non preferred direction, then the tool divides into unit 2. width.This is called as splitting.   
3. Merging (reducing the grids).   
4. Bridging :-Edges which are parallel to the preferred routing direction are bridged with the additional upper layer.
5. Non preffered routing guides has now been converted into Preffered routing guides of metal 2.  Metal 1 has been converted into metal 2.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/5944079e-e9a8-43c9-b5ca-24822cb8b749)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2b17c150-d562-40b4-b4e6-397ed5878ab0)

Metal 1 & 2 connected at the purple colour areas. The tool will understand there is nonzero overlap area, then it will try to put via to connect Metal1 & 2.   As we seen above the black dots are need to overlapped with the route guides/vias.  

Intra layer --> Within the layer.   
Inter layer --> Between the layers.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d9c7705a-b84a-4841-be47-a81904c3338f)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/a28caf18-574e-49a5-b756-f55b11f2c2d8)

M1 layer preffered direction is verical. So the lines are in vertical direction. These dash lines are called as panels.  each routing guide is assigned to one panel.  

If the routing is happening in the even indexes that is called as intra layer parallel panel routing.  First routing will happen in parallel in all the even index pannel. next it will happen all the odd index pannel.  
But It is happening in parallel in partivular layer, but the routing is within the layer.  
Routing will happen from loyer to upper layers.  
