---
title: "Proxmox Install"
date: 2022-09-04T22:55:24Z
author: "Brendan Davidson"
draft: false
---



I wanted to get into the world of virtualization on premises, so I went on google and searched for some good hypervisors that I could firstly use to accomplish this task. I found a few different solutions, from Citrix's [Xen]('https://xenserver.org/') hypervisor to VMware's [vSphere]('https://www.vmware.com/products/vsphere.html'). But after some time in searching, I decided on using [Proxmox]('https://www.proxmox.com/en/proxmox-ve'). It seemed to be the go to hypervisor for those that are creating their own 'homelab' setup and looked to be relatively user friendly.

 

So I had the software, but what about the hardware? I decided to hop onto YouTube to find some videos as to how to start a homelab and what was really needed. It seemed like the general consensus was to find what your needs are and just start with something. Armed with this I took to ebay to search for some used servers that were relatively cheap and ultimately purchased a pair of IBM 7944-AC1 X3550 servers with dual Intel Xeon E5620's in each machine. By no means was it the most powerful machine, but I felt it was a good start since I wasn't exactly sure on where I wanted to go with this endeavor.

Once they arrived, I downloaded the latest version of Proxmox, flashed it to a usb, and turned on the server. It booted to the installer and it seemed to be fairly straight forward, but being new to servers I had no idea which ethernet interface to use since they had two interfaces each. After the install finished, I wasn't able to get to the web interface, so I had to move the ethernet cable from one interface to the other, and I was able to get into the web gui.

 

While in the web gui, I found a way to create a new pool to store the images and iso files to get started and relied on google and youtube to upload an iso and to create my first vm, and found this video from [Craft Computing]('https://www.youtube.com/watch?v=azORbxrItOo&ab_channel=CraftComputing') to be very useful. My first virtual machine of choice was an Ubuntu server since I was familiar with the install process and wanted to get started with a linux vm that I could work with for some homework assignments. Once the virtual machine was all setup, I didn't find the installation or setup of Ubuntu server to be much different than it would've been if I installed it on a bare metal machine. I was able to assign a static IPv4 address and was able to route to it just fine.

 

And that was it! I had Proxmox installed and running a virtual machine, and I was satisfied with the progress that I had made and wanted to install some more purpose built virtual machines, but wanted to think of some ways I can utilize them in a meaningful way.

