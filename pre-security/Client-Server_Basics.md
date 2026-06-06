# [Client-Server Basics](https://tryhackme.com/room/clientserverbasics)

**Path:** Pre Security · **Difficulty:** Easy · **Date:** 2026-06-06

## What the room covers (1-2 sentences, my words)
This room covers the basics of servers and client-server communication, an important foundation for web hacking.

## Key concepts
- How requests travel from client to server, how DNS resolves names, and how the whole thing maps neatly onto a simple pizza order (lol).
- The ground concepts: the requests a client makes to a server, and HTTP itself (the plain protocol, not the TLS-wrapped HTTPS). The room only scratches the surface, but it introduces the methods you use to make an HTTP request: GET, POST, PUT, HEAD, PATCH, DELETE, and so on.
- A server should always validate the request a client makes. If that were always the case, we probably would not have so many SQL injections out there in this day and age.

## What I learned (the part that's mine)
> Nothing really new for me here, but it is a nice refresher that my Burp Suite proxy is not doing anything magic. It is only intercepting the very same request I (the client) send to the server (the pizzeria). Sorry, that analogy made me want pizza again.
> A fun room overall, and a necessary one for beginners heading into web hacking: the basics of HTTP, DNS, IP addresses, and how typing google.com ultimately resolves to an IP address.

## Gotchas / what tripped me up
A common beginner mistake is assuming HTTPS hides the request from you too. It does not. HTTPS encrypts the request in transit, so anyone sniffing the network cannot read