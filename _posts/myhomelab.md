---
title: "Semi-Stable status of my homelab"
date: 2024-04-30
categories: [homelab,hardware]
tags: [servers, ups, nas, synology, asus, intel]
---

# My Homelab:
- 🔭 I’m ALWAYS working on this... It's a homelab, what did you expect?


### Hardware recap:
Router/Firewall - Mikrotik RB5009Up ( 8port 1Gbit POE, 1x SFP+ 10Gbit )
 - 3x Unifi Protect cameras
 - Unifi CloudKey Gen2Plus
 - Loxone MiniServer ( smart home )
House Main Switch - USW-Enterprise-8-PoE  ( 8x 2,5Gbit, 2x SFP+ 10Gbit )
 - 2x Unifi Wifi6
Homelab switch - Zyxel XGS1250 ( 8x 1Gbit, 3x 1G/2,5G/5G/10G/, 1x SFP+ 10Gbit )
 - described in "Homelab RACK"


## Homelab RACK

###  Dell wyse 5070 ThinClient - Proxmox host
 - Intel J5005
 - 16GB RAM DDR4
 - generic 128GB SSD

###  Intel Skull Canyon nuc6i7kyk - Proxmox host
 - i7-6700HQ
 - 32GB RAM DDR4
 - Samsung NVMe Evo 970 Plus 1TB  ( single drive )

###  Intel PC Server - Proxmox host
 - Intel i9-11900
 - 64GB RAM DDR4
 - 2x WD Red SN700 NVMe 2TB
 - 3x 1TB Samsung EVO 870 1TB
 - MPG Z490 GAMING PLUS ( 2,5Gbit ethernet, PCIe slots not used currently )
 - built in Fractal Design Meshify2 RGB

###  Intel PC Backup Server ( Ubuntu )
 - Intel i5-7500
 - 8GB RAM DDR4
 - generic desktop case
 - 2x 240GB Kingston SSD
 - 4x 3TB SATA HDD (ZFS raidz1)
 - 2,5Gbit LAN Broadcom PCIe card

this PC only turns on on saturday by WOL event in HomeAssistant, few minutes after startup downloads all data from Synology NAS and shuts down again. ( backup script will be avalible on my gitghub )

#####  Synology DS923+
 - 4x WD Ultrastar HC550 16TB ( currently only 2 drives pluged in, saving power, drive health, i dont need that much space right now)
 - 2x Kioxia 512GB SSD NVMe ( RW cache drives )
 - Synology E10G22-T1-Mini 10Gbit LAN card 

#### APC Smart UPS C1000
 - power supply backup for whole rack
 - connected to Dell Wyse, serving NUT (Network UPS Tools) to other servers


### My journey of homelabing
I went through a few enterprise server chassis, few CPUs, motherboards and a lot of drives.

Mostly older Supermicro servers from Xeon v1 or v2 series, started experimenting with those, soon realized that those CPUs were power hungry and not a lot performant.
Soon some Supermicro v3 and v4 came along and i found my soft spot for performance per watt. Unfortunately, the 4U cases that i had were not ideal for power savings ( duh ... ).
I Also built AMD EPYC server that was going to be a diamond in my homelab, but the energy prices are currently too high to run that server 24/7. Mabye later...

So i finaly bought a Synology NAS for my 16TB drives. With Intel NUC Skull Canyon as computing power, that was enough for about year or so, than i started to hit limits of that small computer, lot of testing for work, lot of moving VMs, etc.

My recent Intel i9-11900 PC server will be (hopefully) enough for some years to come. This CPU was chosen mostly for iGPU and IntelQuickSync capabilities, for my media collection. Also it has enough horsepower for a lot more VMs than older i7-6700hq. Also with the chosen case i have a lot of room to add HDDs, SSDs, and some PCIe cards to play with, for example a Tesla P4 8GB is waiting on the shelf for some AI workload.
