## What is Ethernet?
- a method of networking
- unarguably the world’s **most widely-used** connectivity technology
- uses CSMA/CD


## What is CSMA/CD?
- stands for **'Carrier Sense Multiple Access/Collision Detection'**
- transmits frame on a network


## Procedure of CSMA/CD communication
![CSMA/CD Process, image from vCenter Group](https://en.vcenter.ir/wp-content/uploads/2020/07/csma-cd.jpg)
1. **[Carrier Sense]** A PC or server checks if someone is using the network's resource.
2. If a carrier's detected, it holds sending the frame onto the network.
3. It starts transmitting its frame if there's no other PC or server transmitting.
4. **[Multiple Access]** Collision occurs if multiple frames are uploaded at the same time.
5. **[Collision Detection]** The PC or server stops transmitting and waits for a random amount of time(*random backoff period*) until the problem's solved.
6. It restarts the transmission of frame.


## Collision Domain
![Collision Domain, image from thebryantadvantage](https://www.thebryantadvantage.com/wp-content/uploads/2018/10/Collision-Domain-1.png)

All four hosts are connected to a hub. If one PC tries to communicate, all other PCs will not be able to communicate. 
If collision occurs in that network, all of the PCs will be affected. They are in one 'collision domain'.
CSMA/CD had developed in order to protect the collision.  


## Bridge & Switch
While hubs have the risk of the collision, bridge and switch can separate collision domains. 


#### Reference
https://www.wired.com/insights/2013/05/ethernet-still-going-strong-at-40-years/
https://en.vcenter.ir/network/csma-cd-carrier-sense-multiple-access-collision-detection/
https://www.thebryantadvantage.com/videos-and-tutorials/ccna-and-ccent-tutorials/csma-cd/
