---
title: "My journey through hardware"
date: 2024-04-29 12:00:00 +200
categories: [homelab,hardware]
tags: [servers, ups, nas, synology, asus, intel]
---

I went through a few older enterprise servers, experimenting with older Supermicro servers from Xeon v1 or v2 family.

Soon realized that those CPUs were power hungry and i had to cut down my power usage.
Soon some Supermicro v3 and v4 came along and i found my soft spot for performance per watt with some lower TDP units. Unfortunately, the 4U chassis that i had at the time, was not ideal for power savings ( dual PSU and high RPM fans ).

So i bought a Synology NAS for the 16TB drives i already had. With Intel NUC Skull Canyon as computing power, that was enough to run my most needed services for about year or so, than i started to hit limits of that small computer, lot of testing for work, moving VMs, etc.

I still needed to hold my power consumption on short leash, so i searched for some low power CPUs with decent computing from one of the last Intel generations.

Finaly i found Intel i9-11900, that will be (hopefully) enough for some years to come. This CPU was chosen mostly for iGPU with IntelQuickSync. Also it has enough horsepower for a lot more VMs than the older NUC i7-6700hq. Also with the chosen case i have room to add more HDDs, SSDs, and even some PCIe cards to play with.

# My current status of homelab:
- It's a homelab, I’m always working on this. But this current state, until i move it to my garden house ( i need to build it first...)

### Networking recap:
Router/Firewall - Mikrotik RB5009Up ( 8port 1Gbit POE, 1x SFP+ 10Gbit )
 - 3x Unifi Protect cameras
 - Unifi CloudKey Gen2Plus
 - 2x Unifi enterprise 6E APs
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

this PC only turns on on saturday by WOL event in HomeAssistant, few minutes after startup, RSYNCs all data from Synology NAS and shuts down again. ( backup script and explanation will be in one of the upcoming blog posts )

####  Synology DS923+
 - 4x WD Ultrastar HC550 16TB ( currently only 2 drives pluged in, saving power, drive health, i dont need that much space right now)
 - 2x Kioxia 512GB SSD NVMe ( RW cache drives )
 - Synology E10G22-T1-Mini 10Gbit LAN card 

#### APC Smart UPS C1000
 - power supply backup for whole rack
 - connected to Dell Wyse, serving NUT (Network UPS Tools) to other servers

![data rack1]({{ BASE_PATH }}/assets/img/2024-04-30-my-homelab/IMG_9751.JPEG)
![data rack2]({{ BASE_PATH }}/assets/img/2024-04-30-my-homelab/IMG_9748.JPEG)
![data rack3]({{ BASE_PATH }}/assets/img/2024-04-30-my-homelab/IMG_9750.JPEG)