## Open Systems Interconnection Model

- Standardized 7 stages of communication functions of a telecommunication or computing system

![OSI 7 Layer](https://i.pinimg.com/564x/13/28/fa/1328fad216c9b577ad274f5303513ea8--osi-model--layers.jpg)


## What for?

![OSI Model](https://base.imgix.net/files/base/ebm/electronicdesign/image/2019/04/electronicdesign_15724_0913wtdosipromo.png?auto=format&fit=crop&h=562.5&w=1000)
    1. To track the flow of data transmission
        **Encapsulation** : Each time data passes through each layer, a header is added. It makes the data transmitted in a set order regardless of the data type.
    2. To find the source of a problem faster (e.g. Ping)
    3. To enhance compatibility between networking hardwares


## Let's dive into the each layer!
    
![Physical Layer](https://www.lifewire.com/thmb/g2w4_fzKLA47R4wGCsJAYnQQDzw=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/layers-of-the-osi-model-illustrated-818017-finalv1-2-ct-ed94d33e885a41748071ca15289605c9.png)
1. Physical Layer
    - Transfers **binary data using** **physical cable**. (e.g. cabels and hubs)
    - Electrical on/off
    - Forwards data without any involvement in what the data is, what errors are present, etc.


![Data Link Layer](https://www.lifewire.com/thmb/zPGFUYqE7hR9f4EQpeh-DyGFqvc=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/layers-of-the-osi-model-illustrated-818017-finalv1-3-ct-9d3e1bf44a554e3db31f706201fc69f6.png)
2. Data Link Layer
    - Divided as Media Access Control sub-layer and Logical Link Control sub-layer.
    - MAC sub-layer controls authorization of data access and transmission. (**MAC address)**
    - LLC sub-layer cheks physical data transmission errors.


![Network Layer](https://www.lifewire.com/thmb/TSScK6WTSLEnjNToI1AwzBXZbYo=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/layers-of-the-osi-model-illustrated-818017-finalv1-4-ct-9ffde2c7142849819c3fcf5e305a242f.png)
3. Network Layer
    - addresses using **IP**, the logical address.
    - selects the safest and fastest path selection to the destination.
    - forwards data packet.

⇒ **Routing**


![Transport Layer](https://www.lifewire.com/thmb/intF9AgvkoWdF0Gjpv8axHvd2Gw=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/layers-of-the-osi-model-illustrated-818017-final-5-ct-373fc5a9edc74359819021555f37467d.png)
4. Transport Layer
    - delivers data across network connections by **transport protocols**. (TCP, UDP)
    - Transport protocols support error recovery, flow control, and support for re-transmission.

# References

[https://iebmedia.com/technology/looking-behind-the-automation-protocols/](https://iebmedia.com/technology/looking-behind-the-automation-protocols/)

[https://www.electronicdesign.com/unused/article/21800810/whats-the-difference-between-the-osi-sevenlayer-network-model-and-tcpip](https://www.electronicdesign.com/unused/article/21800810/whats-the-difference-between-the-osi-sevenlayer-network-model-and-tcpip)

[https://www.lifewire.com/layers-of-the-osi-model-illustrated-818017](https://www.lifewire.com/layers-of-the-osi-model-illustrated-818017)
