# REST from book “웹을 지탱하는 기술”

![book](https://image.yes24.com/momo/TopCate121/MidCate09/12085526.jpg)

I read this book recently.

Since development of web is SOOOOO fast, some features looked a bit obsolete.. but how the book explains REST was very interesting.

Let me share what I got!

# RESTful, REST api... What is REST??

- Representational State Transfer
  - REST express what they do based on **resource**
  - HTTP is a protocol to transfer Hypertext, but it actually transfers various things like image, file.. and it is called Presentation of Resource State
- An Architecture style
  - Other architecture styles: MVC, pipe and filter, event system ..
- Especially, Network system’s architecture style.
  - Most famous style is Client/Server. And Web is also Client/Server. Which means REST has derived from Client/Server.

<aside>
💡 What’s the difference?

- Architecture style - REST (enhance abstraction from architecture)
- Architecture - Browser, Server, Proxy, HTTP, URI, HTML (enhance abstraction from Implementation)
- Implementation - apache, firefox, IE
</aside>

# REST combined with styles

## Client Server: `CS`

![Client-Server](https://darvishdarab.github.io/cs421_f20/assets/images/client-server-1-d85a93ea16590c10bed340dd78294d0d.png)

- Separates User interface - Processing
- Client and Server communicate using HTTP protocol Based on Request - Response
- With this style, client can be multi platform and server can be many

## Stateless server: Client Stateless Server `CSS`

- Stateful

```markdown
Customer: 1 Pineapple Hamburger plz.
🧑‍🍳: Yap, Anything else?
Customer: Oh and 1 Coke plz.
🧑‍🍳: It's $10.
Customer: Sorry, I wanna change the burger to Cheese one.
🧑‍🍳: Then.. it's $9.
```

- Stateless

```markdown
Customer: 1 Pineapple Hamburger plz.
🧑‍🍳: Yap, Anything else?
Customer: 1 Pineapple Hamburger and 1 Coke plz.
🧑‍🍳: It's $10.
Customer: Sorry, I wanna change into 1 Cheese burger and 1 Coke plz.
🧑‍🍳: Then.. it's $9.
```

_Couldn't find proper images 😅 Check for [this slide](https://www.slideshare.net/guruguru/ss-14241987) please_

- Server doesn’t manage state of client
  - Implementation of server become simple
  - Cons to manage session using cookie

## Cache: Client Cache Stateless Server `C$SS`

- Client reuse resources once fetched.
- It reduces amount of communication.
- But decrease reliability

## Uniform Interface: Uniform Client Cache Stateless Server `UC$SS`

- Every server use same interface for the resource represented with URI
- Simple architecture
  - ex. HTTP limits number of method (HTTP 1.1 contains 8)
- Kind of Core feature of REST because other features can be followed naturally when using HTTP

## Layered system: Uniform Layered Client Cache Stateless Server - ULC$SS

- System is divided into layers
- Became easy to be layered thanks to uniformed interface
- Client have no idea whether server added load balancer or proxy .. because the server has same interface using HTTP

## Code on demand: Uniform Layered Code on demand Client Cache Stateless Server `ULCODC$SS`

- download the program code from server and execute
  - JS, Flash, Java applet
- JS became more important

# Hope it was time for easier/better understanding!

# Reference

- book
- [https://www.slideshare.net/guruguru/ss-14241987](https://www.slideshare.net/guruguru/ss-14241987)
- [https://minkukjo.github.io/cs/2020/09/04/Network-08/](https://minkukjo.github.io/cs/2020/09/04/Network-08/)
