---
title: "Network Storage"
date: 2022-09-04T22:57:24Z
draft: false
---



So I had a way of creating virtual machines, and a good way of having most of my devices that I care about be able to have an ethernet connection. I figured that a good expansion was in the way of Network Attached Storage, or a NAS. I thought it would be good to have a centralized storage device that not only I could use, but those in my house for file sharing, device backups, and to extend parts of the virtual computing like testing virtual machines with their hard drives residing over the network and not stored locally.

 

First off was which operating system to use for this task. I wanted something that had a good community around it so if I had issues I could ask questions or read the Q&A to get things working relatively quickly. I also wanted it to not cost a fortune and preferably was free. The two operating systems that I was looking at was [Lime Technology's Unraid]('https://unraid.net/product') and [iXsystems TrueNAS]('https://www.truenas.com/truenas-core/') due to their popularity, and for their good reviews that I was seeing online. I ultimately decided on TrueNAS as it was free, and seemed simple enough to use and get going with. Unraid seemed like it was more than just a NAS and you could also run virtual machines on them. While you can run "jails" on TrueNAS, it didn't seem like it was too much of the focus and with it being based on FreeBSD (For the CORE version, TrueNAS SCALE is currently based on Debian and has some more features) and seemed to be pretty stable.

Next up was the actual computer that was going to house all of this. I was trying to find a good computer case to use to house my NAS, and stumbled across the Fractal Design [Node 304]('https://www.fractal-design.com/products/cases/node/node-304/black/') which was able to house six 3.5" hard drives. I used that with some consumer parts (Intel Pentium G4560, 16gb ddr4, and a 16gb flash drive for booting) to get started, and started off with a pair of 2tb IronWolf NAS hard drives. I used a RAIDZ1 setup which is similar to a raid 1 mirror, so I had 2tb of usable data from the total pool. After some time, I felt like I wanted to upgrade and used this [ZFS RAIDZ Capacity Calculator]('https://wintelguy.com/zfs-calc.pl') to determine how I should setup my pool and get a good estimate on how much space I would have depending on the configuration I went with. I decided on getting four 4tb IronWolf NAS hard drives and place all of them in a single RAIDZ1 pool, meaning of the 16tb of storage I had in raw capacity I only had about 10tb of storage I could use. Meaning I could lose a single disk without losing any data that was in the pool. I decided to go this route so if I needed to upgrade, I could expand by adding an additional 4 drives to double the current space I had available currently.

 

Everything was working fine, but I also wanted to have the ability to have more than six disks as well as be able to stack it with my other servers. So back to YouTube and ebay I went. Turns out, [Craft Computing]('https://www.youtube.com/watch?v=F1xX3V_n0kw&t=4s') created a video not long before that covered a 12-bay 1U server that was also relatively cheap. I liked what the server offered and decided to buy one. After it arrived, I had installed a 120gb ssd for the boot disk (removing the need for the usb drive), installed TrueNAS onto it, and installed my hard drives into that machine. TrueNAS had an option to import a pool and it detected the pool just fine and I was able to get back up and running without issues. I also installed the dual 2tb hard drives, and two 1tb WD Blue hard drives I also had and created a pool with those to be a location I could back up my virtual machines to.

 

After configuring the existing and new pools to be Network File System (NFS) and Samba (SMB) shares over the network, I just left it and it seems to be working great and I don't have any complaints with it at all.

