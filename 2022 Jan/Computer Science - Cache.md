# Computer Science - Cache

Created: January 5, 2022
Created by: Anonymous
Property: handles OS concept too
Tags: Computer Architecture

# What is Cache?

- one of memory hierarchy between processor and main memory.
- `A safe place of hiding or storing data` from Webster’s New Word Dictionary

# Why Cache?

- Higher performance: decrease the frequency of access to main memory by processors(locality of reference).

# How it works

![Cache_동작원리](https://user-images.githubusercontent.com/15176192/148331459-fcae3119-ed15-40e3-aaea-2474e99b0b53.png)

# What kind of Cache?

- Local Cache: the most fastest way of access
    - CPU Cache(e.g. Ehcache)
- Global Cache: Resolve synchronization
    - Web Cache: CDN(Content Delivery Network)
    - In-memory Cache: Redis(Single Thread & multiple data types), Memcached
- Disk Cache

# Strategy

- depends on the business domain
- Usually, memory Read case(In some case, Write-Back strategy can be applied)
- Not recommended while in Finance business domain

# Reference

- [Youtube Channel - Toby’s Spring](https://www.youtube.com/watch?v=zkbvFOwJFgA&t=1746s)
- [Computer Architecture and Organization-William Stallings](http://home.ustc.edu.cn/~louwenqi/reference_books_tools/Computer%20Organization%20and%20Architecture%2010th%20-%20William%20Stallings.pdf)
