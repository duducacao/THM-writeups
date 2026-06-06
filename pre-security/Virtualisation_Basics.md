# [Virtualisation Basics](https://tryhackme.com/room/virtualisationbasics)

**Path:** Pre Security · **Difficulty:** Easy · **Date:** 2026-06-06

Terminology notes:
- Virtualization: Enables a single physical computer to act like multiple separate computers.
- Hypervisor: The "manager" software that creates and runs the virtual computers.
- Lab Machine (VM): A whole virtual computer inside the real one, with its own OS and kernel.
- Container: A small, isolated box for one app that shares the host's kernel instead of running its own.
- Container Images: A pre-packed recipe/template used to create containers.
- Network Ports: Numbered entry points that apps use to talk over the network.

## What the room covers (1-2 sentences, my words)
Well, this room covers virtualization and goes into some depth on how VMs and containers work, and why we actually use them.

## Key concepts
- The key concepts of virtualization, though many, boil down to one idea: using one machine to run many machines. Confusing at first, so bear with me. Say you have a fridge. You don't keep only milk in it, right? Why would anyone buy a whole fridge just to store a single jug of milk? That is exactly why virtualization exists. When we buy a computer, say a powerful one and not the super slow thing granny used to have (haha), we barely use it to 100%. So some smart person built the hypervisor, which lets us carve that computer into multiple separate "segments".
- The hypervisor is the management software that creates and runs our virtual computers. PWN a hypervisor and you get access to every VM it manages. Simple as that. Or not quite. A virtual machine is another computer running inside your computer, that is as simple as it gets. It can run a different OS, a different amount of cores and threads (just not more than your host actually has, obviously, this is not "free RAM download"), its own RAM, and its own disk space, which is all a VM needs to run. And as you would guess, it is cheaper and more effective than buying a SECOND LAPTOP. That is the principle of virtualization.
- Then there are containers, which package a single application. Unlike a VM, a container does not get its own kernel: it runs as an isolated user-space process and shares the host's kernel, fenced off by kernel features (namespaces and cgroups). So no ring 0 here, that is where something like Vanguard plants itself, right inside your kernel (would you trust Riot with that?). The kernel-sharing part has a consequence: a Linux container needs a Linux kernel, so on Windows you cannot run one natively, Docker quietly spins up a hidden Linux VM (WSL2) to lend it one, capiche? Containers are still isolated from other apps and from the host OS, and that is the principle: computers within your computer, walled off from the main one. Be careful though, most setups are NOT isolated from your network by default. So if you are going to detonate a MW (not Modern Warfare, I mean malware) sample, isolate the machine from your network first, and preferably make the host OS different from the guest OS, it avoids a lot of problems. But what if you want a Windows VM to run Windows malware and your host is also Windows? Calm down, padawan. Nested virtualization comes in clutch: with virtualization enabled you can run a VM inside your host, turning that VM into a host for yet another VM, and so on, as far as your resources stretch.

## What I learned (the part that's mine)
> Hypervisors are vulnerable, and because containers share the host kernel, a kernel bug can turn them into an escape path too, which can be a handy thing during privilege escalation if it is exploitable. Pretty cool knowledge from this one. I have always loved the concept of virtualization and how VM escapes work, so understanding even a tiny bit more about it puts a huge smile on my face.

## Gotchas / what tripped me up
The real gotcha here is that a VM is also vulnerable if you do not take the right measures to protect it. VM escapes are a thing: rare, but actively researched (a recurring Pwn2Own category), and they exist precisely because of the hypervisor sitting underneath. So pick trustworthy virtualization software and keep it updated.