---
layout: post
title:  "Day 3 - Back to Ansible, Virtualbox issues and first playbooks"
date:   2024-07-03 23:10:00 +0200
categories: jekyll update
---


![custom header](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/SrewPUfo2c0.png)

Welcome back!

Today I planned to expand my current infrastructure for Ansible's deployments a bit, and also test some basic instructions to update all packages, and
just may be going further, and ensuring a secure SSH connection on all my current servers.

This is my new approach, as a quick summary I just added a new local VM running the recently released Debian 12.6, so I can have further experience with
two different package managers.

![updated diagram for July](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/diagram_2.png)


**Sidenote:** Due to time restrictions and situations out of my control, this "day 3" was distributed within 3 actually different days, those being
July 2nd, 3rd and 8th.

### 02/07/2024 -- First attempt - Virtualbox messing around.

It is mostly said that new begginings are rough...well, I agree it can be hard to start over something you already had some acquired knowledge,
as for my case, that's the entire objective of the challenge, go over something I like and are somewhat passionate to know more about, get some
rolling experience and hopefully be good enough so I can create more and better things out of it.

As for today's situation, I encountered a virtualbox error disclaiming an issue in suplibosinit "Kernel driver not installed (rc=-1908)", after some
googling/duckduckgoing(?) around and checking my current kernel (output for `uname -a` command is `Linux pop-os 6.9.3-76060903-generic #202405300957~1718348209~22.04~7817b67 SMP PREEMPT_DYNAMIC Mon J x86_64 x86_64 x86_64 GNU/Linux`) I got to tinker a bit with the current state of my virtualbox installation, since first off I wasn't even able to startup my VM.

I tried the basics, following up the pop up's indications, which ended up not working at all, so I partially reinstalled my 
then current virtualbox package and I succesfully came up with a functional VM again. 

#### Not so easy...

After the first issue was fixed, I proceeded to download the latest available ISO for Debian, in order to prepare a new VM, once after the installation
process was over, I noticed that the bridge adapter I picked to actually be able to send Ansible instructions/commands to said VM was not giving a proper 
IP nor giving acces to the internet to either of my current VMs, for that, I made some adjustments with both VMs shutted down, mostly at a GUI level, with
no success so far.

I checked back again around common search engines with no clear answer either, so, since the previous issue disclaimed some unknown behavior with the kernel
for my current Virtualbox installation, I decided to totally remove it, including kernel modules, in order to ensure a clean install, yet I made sure to **NOT** delete my VM virtual disks and other related information, so I would not need to reinstall both again.

After that, I proceeded to reinstall virtualbox as clean as possible, which, after rebooting my system (just a bit of sysadmin magic here) ended up not only 
allowing me to work properly with both VMs powered ON, but it did also allow them to get a local IP without changing any default value for the bridge network
adapter.

Kind of pleasing to see everything work out after a soft reboot, right?


### 03/07/2024 -- Starting of with Ansible, following Jeff Geerling's steps once again

I'm not a stranger with Jeff Geerling's youtube channel, I do follow him on said platform and every now and then check about his latest tinkerings with 
technology. Even so, I prefer to focus on today's matter, Ansible, trying to quickstart it as much as possible, without burning me out too much.

I do also have a copy of his book "Ansible for Devops" (2nd Edition), which I will also be using in paralell so I can better follow his instructions or rather
continue learning on my own with multiple sources, so I shouldn't stumble around too much. There are other resources I found over time,like [roadmap.sh](https://roadmap.sh/devops) or [Ansible's docs](https://docs.ansible.com/ansible/latest/getting_started/index.html).

Taking a look back into my previous projects, I took a snippet of code from my [Ansible repo](https://github.com/Akirapearl/Ansible). This part of the code
is pretty much easy to read, and it also should be useful to export to a proper apt playbook.

```
  - name: Upgrade all packages
    ansible.builtin.dnf:
      name: "*"
      state: latest

  - name: Remove not required packages
    ansible.builtin.dnf:
      autoremove: yes
```

May be separating playbooks into smaller/atomic tasks could be of use, so every topic stays properly located, as in the following example/concept:

1. First- Ping all servers, update all packages, remove unnecesary dependencies.
2. Second- Reboot Flask web services.
3. Third- Ensure Docker is up and running and make sure specific Jenkins container is existent.
4. Fourth- Take local Golang code, compile it via Jenkins and output success or failed brief description.
4. Fifth- Move localy stored photos into [Photoprism](https://www.photoprism.app/) filesystem.


### Expected day to continue - 08/07/2024

### What I learned

- Do not disrespect the value of rebooting your system after a big update or install, even on linux, it just need a bit more of care on what you are 
actually doing (i.e removing virtualbox related kernel modules).
- Taking a look back is fine, but really consider starting from scratch sometimes, it will be useful to see things clearly and not full of "this used to
work" kind of mess.


### Next steps



