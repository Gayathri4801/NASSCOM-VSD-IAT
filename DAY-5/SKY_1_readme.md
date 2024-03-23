## Routing and Design rule check (DRC)

Routing means we need to route two points and finiding best possible connection & shortest path & min twist and turns(there should not be many zig zag lines) between two points.one point is source and one point is destination/target.      
Routing is the process of creating physical connections based on logical connectivity in the netlist file.   
There are various algorithms being developed for routing.  
One of the algorith follwed by people is Maze algorithm and lee's algorithm.   
The connections made between source and target should be mostly L shape lines. There should be very few zig zag lines.   
From the algorith point of view,  The algorith doesn't care it is flop flop or buffer.   
For software it is just 2 point, it has to connect that 2 points.    
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/d0578ece-50e5-4aab-8794-b4b1a09c94ff)

when we are connecting two points we should take care of other blocks and blockages. They should not effect because of this routing. 

**Maze Routing Algorithm**

Maze routing algorithm tries to find the shortest path between two points in a maze for a single wire if such a path exists. In this scheme the source cell sends messages to its four neighbors. The message propagates in the form of a wave to other nodes. The first wave front that reaches the destination determines the connecting path. There are two phases in this algorithm. In the first phase nodes are labeled with their distances from the source. In the next phase distances are used to trace from sink to source choosing a path with the least distance to the source.   
**Lee algorithm**

Lee algorithm is one possible solution for Maze routing problems. This algorithm represents the routing layer as a grid, where each grid point can contain connections to adjacent grid points. 

**Lee Algorithm steps:-**   
1. It creates a routing grid at the backend.There are some standard dimensions for grid.
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2ed5dbec-6c91-48c6-912b-e175a9056e51)

2. When this routing grid created, the algorithm creates the 2 points source and target.
3. Now throgh the help of this routing grid the algorithm has to find the best possible way to connect this sorce to target.
4. The 1st step is it tries to label all of grids all around it only horizontal and vertical not diagonal.
5. It will continue till reached to target as shown in image.  
6. After that it will trace some path.
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/2b2235ff-7572-44b1-82a0-412dd0c387c3)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/83a376d9-2894-44a5-aae4-824818f4197e)
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/c4ceaacd-fbc5-47e8-a32f-6ecd840e926a)

7. Now we have to identity which one we should picking up.
   In 1st way we can see 2 bends to reach source to target. In 2nd way only 1 bend is there. Any route with single bend is prefferable in case of algorithm.
This Maze algorith is used for global routing.
For 1 path it is easy. when we are making millions connections then this algorithm will consume more time.Because it has to store all paths information.     
 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/6834f714-bb42-4d2b-8067-4fd635395152)

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/b709132f-2e6d-4d89-8a5d-1c7aa5a517bf)

Green paths are routing paths. 


## Design Rule Checks (DRC)   

While we are routing it's not about only connecting two points. we need to take care certain rules that we are follow while routing. 
These rules say that when you are trying to build two wire there should min spacing, distance between that two wires.  
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/66bcf2b3-8761-4b29-a6f6-941db2403773)

3 basic Rules are,  
Width, Spacing, Pitch.   

Width of wire, There are some techniques to build the wires. Those techniques reffered as photolithography.  Photolithography is used light to build these wires. Light has got certain minimum wavelength.  with that min wavelength it can draw certain min width of the wire.  Considering that we come up with some rules, say that the optical wavelength of the light can build a wire with certain width.  wee can't go below that width.    
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3b9c7e6b-ca08-4c49-a857-d95268fb930b)

The another rule of photolithography says that the min pitch between wires should be minimum. These things comes after lot of optimizations done on the lithography. It can be more, but It can't be less. 
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/9cb55e42-8997-4e6f-ba0a-bf3601928dbe)

The another rule of photolithography says that the min spacing between wires should be minimum. It can be more, but It can't be less. Because it won't get printed on silicon as per lithography rules.       
![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/3f491395-5f21-482b-b547-485290abb9a7)

While routing millions of routes, the routing algorithm needs to remembeer(aware of) thousands of rules.   

Some violations we can see below, These things can lead to functionality failures.  These are very serious things for good IC.  

![image](https://github.com/Gayathri4801/NASSCOM-VSD-IAT/assets/163323618/8f4a46c7-f9cc-4406-b46b-591cd4753045)

How do we solve signal short?  
