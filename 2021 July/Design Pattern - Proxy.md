# Design Pattern - Proxy

Created: August 3, 2021
Created by: Lee Anne
Tags: Design_Pattern

# Last Session...

- Factory Pattern: basis of Dependency Inversion Principle("Depend upon abstractions, do not depend on concrete implementation")
- Simple Factory Pattern VS Factory Method Pattern: Factory method pattern is more free and flexible to create concrete implementation
- You can refer the below architecture image. This explains Factory Method and Abstract Factory well

![IMG_8258436F871F-1](https://user-images.githubusercontent.com/15176192/130213691-f9527dfb-b672-4e64-b322-d03e8d4551c3.jpeg)

# Purpose

- As a structural design pattern, it functions as a 'Substitute' or 'Placeholder' for another object.
- Controls access to the original object.(before or after request)
- Protection of the original object!

# Concept

- Proxy stands for 'local representative to a remote object'. It means that you are talking to proxy object even if you think you are communicating with the real remote object.(Real-World Analogy: Credit Card)

![IMG_87C2FD49D536-1](https://user-images.githubusercontent.com/15176192/130213676-8e80d674-73b4-464c-bf20-2a8cb387555b.jpeg)

- It's like calling remote method through proxy object.
- 4 types of proxies
    - Remote Proxy

        *representing the object that is located remotely such as a different heap on JVM. You don't have to worry about releasing the logic. It is based on encapsulation.*

    - Virtual Proxy

        *provide some default and instant results if the real object is supposed to take some time to produce results. Once the real object is done to be generated, the proxy pushes a real data where it has provided dummy data earlier.(efficient in resource-intensive case)*

    - Protection Proxy

        *has an access to some resources that some object might not approach since they has no access.*

    - Smart Proxy

        *can provide additional security layers by interposing specific actions when the object is accessed.*

# Architecture

<img width="940" alt="Screen_Shot_2021-08-11_at_7 25 04_PM" src="https://user-images.githubusercontent.com/15176192/130213707-9731fce0-02c8-40cd-9f38-717afbabda0b.png">

- Proxy should follow the interface class that is a parent of the real object.

# Sample

- Real World Case: **Internet which restricts a few website**

---

Interface of an Internet

```java
public interface Internet
{
    public void connectTo(String serverhost) throws Exception;
}
```

---

RealInternet.java

```java
public class RealInternet implements Internet
{
    @Override
    public void connectTo(String serverhost)
    {
        System.out.println("Connecting to "+ serverhost);
    }
}
```

---

ProxyInternet.java

```java
import java.util.ArrayList;
import java.util.List;
  
  
public class ProxyInternet implements Internet
{
    private Internet internet = new RealInternet();
    private static List<String> bannedSites;
      
    static
    {
        bannedSites = new ArrayList<String>();
        bannedSites.add("abc.com");
        bannedSites.add("def.com");
        bannedSites.add("ijk.com");
        bannedSites.add("lnm.com");
    }
      
    @Override
    public void connectTo(String serverhost) throws Exception
    {
        if(bannedSites.contains(serverhost.toLowerCase()))
        {
            throw new Exception("Access Denied");
        }
          
        internet.connectTo(serverhost);
    }
  
}
```

---

Client.java

```java
public class Client
{
    public static void main (String[] args)
    {
        Internet internet = new ProxyInternet();
        try
        {
            internet.connectTo("geeksforgeeks.org");
            internet.connectTo("abc.com");
        }
        catch (Exception e)
        {
            System.out.println(e.getMessage());
        }
    }
}
```

---

Result

> Connecting to [geeksforgeeks.org](http://geeksforgeeks.org/)
Access Denied

# More...

Pros: Security, increase of the performance thanks to avoiding the duplication of real objects, manage the lifecycle of the real object, Open for Extensions and Closed for the Change.

Cons: Complicated code, Delay of the response from the service object

Applicability: Lazy initialization, Access Control, Caching, Logging Request, etc...

Decorator has a similarity with Decorator pattern. However, in terms of Proxy it manages the lifecycle of its service object on its own. On the other hand, the composition of Decorators is controlled by the client.

# Reference

- [Refactoring Guru - Proxy](https://refactoring.guru/design-patterns/proxy)
- [GeeksforGeeks - Proxy Design Pattern](https://www.geeksforgeeks.org/proxy-design-pattern/)
- [Headfirst Design Pattern](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=582754)
