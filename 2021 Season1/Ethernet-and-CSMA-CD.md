## What is Ethernet?
- a method of networking
- unarguably the world’s **most widely-used** connectivity technology
- uses CSMA/CD


## What is CSMA/CD?
- stands for **'Carrier Sense Multiple Access/Collision Detection'**
- transmits frame on a network


## Procedure of CSMA/CD communication
<img src="https://en.vcenter.ir/wp-content/uploads/2020/07/csma-cd.jpg" width="80%">

1. **[Carrier Sense]** A PC or server checks if someone is using the network's resource.
2. If a carrier's detected, it holds sending the frame onto the network.
3. It starts transmitting its frame if there's no other PC or server transmitting.
4. **[Multiple Access]** Collision occurs if multiple frames are uploaded at the same time.
5. **[Collision Detection]** The PC or server stops transmitting and waits for a random amount of time(*random backoff period*) until the problem's solved.
6. It restarts the transmission of the frame.


## Collision Domain
<img src="https://www.thebryantadvantage.com/wp-content/uploads/2018/10/Collision-Domain-1.png" width="80%">

All four hosts are connected to a hub. If one PC tries to communicate, all other PCs will not be able to communicate. 
If a collision occurs in that network, all of the PCs will be affected. They are in one 'collision domain'.
CSMA/CD had developed to protect the collision.  


## Bridge & Switch

<img src="https://user-images.githubusercontent.com/50111853/116780792-a93dbf80-aab9-11eb-9ae0-08b2f997b69b.png" width="48%"/><img src="https://user-images.githubusercontent.com/50111853/116780799-b0fd6400-aab9-11eb-9ddf-696b9c7fb204.png" width="50%"/>
While hubs have the risk of collision, bridge and switch can separate collision domains. 

<img src="https://user-images.githubusercontent.com/50111853/116781127-ee62f100-aabb-11eb-98db-87385600dbb4.jpg" width="80%">
In this regard, PCs connected to the switch can communicate with each other even though other PCs are on transmission.

#### Reference
- https://www.wired.com/insights/2013/05/ethernet-still-going-strong-at-40-years
- https://en.vcenter.ir/network/csma-cd-carrier-sense-multiple-access-collision-detection
- https://www.thebryantadvantage.com/videos-and-tutorials/ccna-and-ccent-tutorials/csma-cd
- 후니의 쉽게 쓴 CISCO 네트워킹
