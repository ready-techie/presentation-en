# UDP Hole Punching

💡 **User Datagram Protocol (UDP)**: a communications protocol that is primarily used to establish low-latency and loss-tolerating connections between applications on the internet

# P2P (Peer-to-Peer)

![https://t1.daumcdn.net/cfile/tistory/9923B3475C03F5B01D](https://t1.daumcdn.net/cfile/tistory/9923B3475C03F5B01D)

- each computer acts as both a server and a client
- communicate without any server between them
- should know each other’s ip address and port number
- Mostly p2p is implemented by UDP than TCP, because it’s faster

![Router](https://expatitparis.com/wp-content/uploads/2020/09/wifi-routers.jpg)

- Luckily these days we all have **router** in our homes to connect multiple devices on the internet
- And here we confront some problem with NAT

💡 **NAT: Network Address Translation**
Method of mapping an IP address space into another to communicate between inner-outer network
Converts private ip ↔ public ip

# Problem (thanks to NAT😈)

![Untitled](https://t1.daumcdn.net/cfile/tistory/99E5193C5C03FF0E18)

- We have to know each other’s ip and port number! (which is not private)

# UDP Hole Punching

![Hole puncher](https://ae01.alicdn.com/kf/Hccc7f484a4b94cccb25a0c5cc80b93f3f/Double-Hole-Puncher-Manual-Porous-Paper-Puncher-Hand-Pressure-Puncher-School-Office-Round-Hole-Punching-Thickness.jpg_Q90.jpg_.webp)

- We need `Relay server` which only transfers packet to another

![Untitled](https://t1.daumcdn.net/cfile/tistory/13749E394F0A5BEA25)

- Send a packet to relay server to get public ip and port of device
  - NAT maps public ↔ private ip address and stores on table

![https://t1.daumcdn.net/cfile/tistory/99D2F7475C053CCF32](https://t1.daumcdn.net/cfile/tistory/99D2F7475C053CCF32)

- Now two users can communicate with each other with their public address
- Seems a **hole** has been made!

# Consider

- Has to continuously `ping` to maintain the mapped NAT table
- Because UDP is unreliable, relay server have to consider reliability for better performance

# Reference

- [https://cjwoov.tistory.com/5](https://cjwoov.tistory.com/5)
- [https://gamedevforever.com/47](https://gamedevforever.com/47)
- [https://www.sysnet.pe.kr/2/0/1226](https://www.sysnet.pe.kr/2/0/1226)
