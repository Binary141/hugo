---
title: "Ethernet All the Things"
date: 2022-09-04T22:58:24Z
draft: false
---



Ethernet. We all love it when we can have it, so why not try to have it in all the places if we can? That is the thought that started it all, the project of me trying to run ethernet to as many areas as I could in my house where devices were likely to be. Little did I know what I was actually getting myself into when starting this project.

 

I initially started this project at the beginning of summer, and all of the wiring resided up in the attic where all the insulation was blown in and sitting on top of all the drywall. This meant that it got really hot, was quick to tire you out, and had to figure out how to tread across the trusses while moving through roughly 24 inches of insulation which means that jeans would be the ideal attire as to not constantly rub insulation on my bare skin. Needless to say, I tried to work on the wiring during the morning and the evening when it was the coolest temperature to work. Fortunately, I only needed to run cable to 2 rooms on the main floor of a house with a basement so the work was a little easier, since the rest of the rooms that I wanted wired devices in seemed to have cat5e cable already ran to them.

In order to run the cable, I purchased a spool of cat6 ethernet cable that I found had good reviews and was not Copper Clad Aluminum (CCA), so I felt confident in the decision to purchase it. After running the cable to the rooms and terminating the rj-45 jacks on the ends and installing the face plates, I decided to route the cable through the wall and into the basement where I had wanted to setup my homelab with my pfSense router along with just about anything else that I could need for my networking needs.

 

But for those rooms that already had cable that was ran to them, how do I figure out which cable is which in the mess of the bundle of cables? I simply just went to each destination, stripped off 2 wires (in my case I did blue and white/blue) and wrapped the bare copper around each other. Then I went to the bundle of cables that was in the closet where they were all strung together for the phone line connections that were there previously, stripped the blue and white/blue wires, and hooked them up to my multi-meter set to the continuity mode. This mode made the meter create an audible 'beep' upon having detected a closed circuit, and having the bare copper connected at the other end meant that it would be a closed circuit and when it beeped I knew exactly where it would lead to. I labeled all of the cables that were relevant to where I needed, and then crimped those ends to create an ethernet cable I could actually use. After quite a bit of back and forth, I had roughly 5 cables that I had crimped and ready to go.

 

Unfortunately, I had quite a bit of devices and cables to plug into compared to how many ports were available on my poor little 8 port gigabit switch that I had at the time to use for this. I was able to plug in the critical devices, like network Access Points (AP) and the other Proxmox server that I had with a couple virtual machines running on it at that point. I was able to make do with what I had at that point, but I knew that at some point I would need some more ports to work with and to ebay I had visited once again. I knew that I wanted something with many ports, some possibly sfp to play around with, and definitely something that supports VLANs as I knew I wanted to play around with them, and I happened to stumble across the [SMC SMCGS24C-Smart]('https://www.edge-core.com/temp/edm/old_downloads/mn/SMCGS24C-Smart_User-Guide.pdf') 24 port gigabit ethernet switch. This was a definitely used item with some cosmetic issues, but I thought for $30, what could go wrong?

 

It arrived and I plugged it in and did a quick test to see if each port had gigabit functionality, and it did! For $30 I was able to get a managed switch with all the ports working and I considered it a win. One thing that I did have difficulty with was how to actually get into the web managed interface to setup VLANs. After a fair amount of research on google, I discovered that to reset the switch I needed to connect ports 1 & 2 together with a regular patch cable and not a crossover cable, for at least 40 seconds. Once it resets, it defaults to the IP address 192.168.2.10/24 and to access it I had to manually change my adapter IP address since it was out of my networks 192.168.1.0/24 space. The web interface was fairly simple and I was able to find where to change the address for the switch, and placed it on something that I could navigate to from my normal address space.

 

Once everything was setup on the web interface, I simply had to plug in all the cables that I wanted to and it seemed to be working as intended. All devices could contact my DHCP server and get an address, and was able to get out onto the internet, with the ability to connect at gigabit speeds. Since my networking "rack" was a little out of the ordinary (and by that I mean I had found some space in a nice little closet and had created some shelving for the couple servers using wood 2x4s to stack them vertically similar to that in a proper networking rack), I had to create my own mounting system for the switch to live. I ended up using some spare wood and a few screws to mount it vertically on the side of the wall where it was at, and it seemed to be holding well.

So after all was said and done, I ran some cable and had a way to connect just about all the devices that I could want at the moment and had some additional room to expand with.

