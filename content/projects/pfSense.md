---
title: "pfSense"
date: 2022-09-04T22:56:24Z
draft: false
---



After I had installed Proxmox onto one of my servers, I wanted to install something useful that I could utilize all the time that I could also learn from. I went looking on YouTube and found a few videos, namely from [NetworkChuck]('https://www.youtube.com/watch?v=lUzSsX4T4WQ&t=2138s') [Level1Techs]('https://www.youtube.com/watch?v=ledv33t6SNE') and [Techno Tim]('https://www.youtube.com/watch?v=hdoBQNI_Ab8&t=8s'). The video from Techno Tim actually goes into detail on how to virtualize pfSense inside of Proxmox and so I thought I would give it a go.

I decided to initially purchase a cheap [dual port gigabit network card]('https://www.amazon.com/gp/product/B08MBRWDK8/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1') to use for the WAN and LAN interfaces so I could pass in a single Network Interface Card (NIC) to the virtual machine to make it a little more simple in design. I installed the NIC, installed pfSense on a vm giving it 4 cpu cores and 4 gigabytes of ram, and setup the interfaces. The NIC showed up on the web interface, but for some reason I would get internet dropouts and overall had a bad experience with it. But one thing that I didn't think would be an issue was that the NIC I had purchased was based on the Realtek RTL811GN chipset. The issue with this is that pfSense uses [FreeBSD]('https://docs.netgate.com/pfsense/en/latest/general/why-freebsd.html') and it doesn't have all the drivers to be able to communicate as intended to my NIC.

 

So I went back to googling a good NIC to use for pfSense, and found that just about any Intel card should work, so I went ahead and purchased an [Intel 82576]('https://www.amazon.com/gp/product/B074PQWQB5/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1') card for only around $15 more than I was able to get the Realtek card for. I repeated the same steps of passing the card into the virtual machine, setup the interfaces, and this time it just seemed to work. I was able to use a wired connection and have some reliable downloads and any speed tests that I performed did not drop out at all.

 

After I was able to get the router all setup and working, my next issue was how do I install it logically into my network for use. I had upgraded to fiber recently, and as such the Internet Service Provider (ISP) had brought over a modem/router combo and having two routers on the same subnet can cause issues. So I setup the provided router to be in the 192.168.0.0/24 space, and my pfSense router in the 192.168.1.0/24 space. This wasn't quite enough as I also wanted to have the pfSense box handle all my port forwarding so I could essentially get the full router experience while also having two routers on my network. So to fix this, I went into the ISP provided modem, and placed the pfSense machine in the DMZ and also port forwarded just about all the ports I could to pfSense. With those changes, I was able to control port forwarding through pfSense and it was able to work properly and as I had intended it to function.

 

After I was able to get everything setup as I wanted it to, I setup all the access points to use the pfSense machine for routing and left it to do its thing. Setting this up was only the beginning and some additional upgrades like VLANs that I would like to implement in the future to play around with to learn a little more on how to add them to a network.

