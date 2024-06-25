---
layout: post
title:  "Day 1 - Ansible, setting up and planification"
date:   2024-06-25 17:10:00 +0200
categories: jekyll update
---


![custom header](/assets/images/SrewPUfo2c0.png)


Welcome to my very first day at the 100 days of code trip!

First things first, as I want to stay as organized as possible, for that, I will be focusing in a broad-scoped learning,
in other words, I will be lookinng into learning more about the technologies themselves rather than achieving a perfectly coded
website or pristine and operative configured [homelab](https://github.com/Akirapearl/homelab).

For my homelab setup, I will be diving into Ansible, while my objective for the webdev aspect of this challenge, I will set my goal
on learning the basics of React and/or finishing said chapter within [Odin project's site](https://www.theodinproject.com/paths/full-stack-javascript)

Moving on, and taking this from the example that experienced gave me as devops, I figured out that I needed two
different environments for the homelab part of this learning process, for that, I have already prepared a Virtualbox VM with the same
OS as my current server (Rocky Linux 9).


### About the setup

One potential question that can easily appear here is, why Rocky Linux? Well, there is no secret behind the fact that nowadays there are
2 main Linux distributions being used at production environments for most big companies, those being Red Hat or Debian-based.

Knowing this, I tested both of them around my bare-metal server, which is an HP Elitedesk 800 G2, starting with Ubuntu server and Rocky
Linux, I stepped into a situation where my wifi dongle (not possible to perform an ethernet connection to my domestic router) did not work properly using
Ubuntu, leading to an installation of Rocky that went pretty smooth and functional.


I had already the same ISO locally, so I prepared a Virtualbox VM with the same OS, so it can be used as testing environment.


__But why Virtualbox?__

Even though I do have a Linux system with Qemu/Kvm Virtual Machines already available, it was a bit of a hussle to setup a local
bridge network, so the VM could be connected to the same network as my current workstation. [1] [2]  Thus, since I already have experience with
Virtualbox, and it would make things easier in case of failure to clone or rebuild my setup, I opted for the quickest and most familiar option this time.

![setup diagram](/assets/images/image_diagram.png)


### So, about DAY 1's progress

Today's been focused into properly setting up both my server and the VM in order to properly connect via SSH from my Workstation computer. On the other hand,
the above contemplated aspect of "learning before completing a specific thing" appeared half-way through, so this would be it for today! 

Also I want to highlight that this post includes a Unsplash image that i slightly edited, yet I do NOT claim any ownership over it or the font I did use 
(Jetbrains Mono Italic).

---
#### Credits:
[Challenge image](https://unsplash.com/photos/black-flat-screen-computer-monitor-turned-on-near-blue-and-white-sky-SrewPUfo2c0)
[Diagram website](draw.io)
[1](https://wiki.qemu.org/Documentation/Networking)
[2](https://apiraino.github.io/qemu-bridge-networking/)