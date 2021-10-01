# TCP - Nagle's Algorithm

Created: September 29, 2021
Created by: Anonymous
Tags: Network

- A means of improving TCP/IP network by reducing the number of packets that need to be sent over the network.
- This is introduced by John Nagle and published in [RFC 896](https://www.rfc-editor.org/rfc/rfc896.html).
- Simply put, the principal of this algorithm is to send all packets all at once.

```
In particular, IP
gateways are vulnerable to a phenomenon we call  "congestion col-
lapse",  especially when such gateways connect networks of widely
different bandwidth.  We have developed  solutions  that  prevent
congestion collapse.
																												*John Nagle*
```

# Concept

```
if there is new data to sendthenif the window size ≥ MSSand available data is ≥ MSSthen
        send complete MSS segment now
elseif there is unconfirmed data still in the pipethen
            enqueue data in the buffer until an acknowledge is received
else
            send data immediately
end ifend ifend if
```

This is the resolution of the two problems(too small packets and source-quench)

- `inhibit the sending of new TCP segments` when new outgoing data arrives from the user if any previously transmitted data on the connection remains unacknowledged.

# Performance

```
...
Thus, for all cases examined, our scheme provides at least 98% of
the  performance  of  both other schemes, and provides a dramatic
improvement in Telnet performance over paths with long round trip
times.
...
```

- Even if this algorithm provides the most effective network communication by handling TCP congestion control, a delay problem still exist.(too long wait time and delayed ACK interaction)
- When it comes to Delayed ACK method, we should avoid using Nagle's algorithm at the same time.
- This can't work properly with real-time network communication such as games or multi-player videos.
- Many operating systems implement Nagle's algorithm.

# Conclusion

Except Nagle's Algorithm, there are lots of congestion control solutions. Even though congestion control problems are difficult to manage, we can make better network communication by applying those solutions.

# Reference

[Nagle's algorithm - Wikipedia](https://en.wikipedia.org/wiki/Nagle%27s_algorithm)

[RFC Official Documentation(896)](https://www.rfc-editor.org/rfc/rfc896.html)