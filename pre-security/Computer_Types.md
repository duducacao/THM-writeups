# [Computer Types](https://tryhackme.com/room/computertypes)

**Path:** Pre Security · **Difficulty:** Easy · **Date:** 2026-06-06

## What the room covers (1-2 sentences, my words)
The room covers the many everyday objects that are quietly computers, things we rarely stop to think of as computers at all.

## Key concepts
- Almost anything can be a computer, and the moment a computer connects to a network, it becomes something that can be attacked.
- From a solar panel controller to a server room's temperature sensor, anything with a chip inside and a network connection is a potential target.

## What I learned (the part that's mine)
> There is a lot to take from a room like this if you look at it through an ethical hacker's lens. You start to realize that almost everything around you is a potential entry point, or vulnerable in some way; you just have to be creative enough to see it.
> Which leads to the harder question: how do we defend all of these computers?

## Gotchas / what tripped me up
I had no idea smart fridges were a real thing. Who actually needs one? Although... maybe a fridge that reminds me to buy milk is not the worst idea I have heard.

## War story: when "it's just a controller" wasn't
On a real engagement I compromised a solar panel controller. The specifics are kept deliberately vague for confidentiality (Thanks NDA), but here is how it went:

- **How it was exposed:** The internal network had little to no segmentation. The VLAN setup was mostly decorative, more about organization than actual security, which is more common than people think. The controller showed up in an `nmap -sV` sweep across the client's IoT devices, still running default credentials. A quick admin/admin attempt was all it took.
- **Why it mattered:** People rarely consider how much impact this kind of access can carry. From that one device I could have affected physical operations, and that is exactly why demonstrating impact matters: it shows the business what the risk means in practice. Default credentials on IoT are far more common than they should be.
- **What it gave me:** The controller became an initial foothold. From there I pivoted to an outdated, internet-facing perimeter device and leveraged a known unpatched vulnerability to widen my access and move deeper into the network.

This room's point in one line: the device you dismiss is the one an attacker targets.