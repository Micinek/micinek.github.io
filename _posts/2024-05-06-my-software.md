---
title: "My journey through software"
date: 2024-05-06 06:00:00 +200
categories: [homelab,software]
tags: [servers, ups, nas, proxmox, cluster,virtualisation, docker, linux]
---


My first servers were mostly Debian or Ubuntu Server (without desktop interface). Later i started to use Proxmox to have a nice GUI that i don't have tinker with all the time and focus on the virtual machines part. Lots of installations, lots of errors have been made, repairing or even recreating my hypervisor was on monthly basis when i was learning how it all works. I got some tutorials from work, than i had to study on my own, learning Linux, LVM, ZFS than clustering, replicating storage, high avability, etc.


My current homelab consists of 3 node Proxmox Cluster and a Synology NAS, as covered in [my hardware post](https://micinek.github.io/posts/my-hardware/). Cluster is running on my home LAN subnet, it also has separate network in public VLAN that is routed on separate public IP that I can use for publishing some services to the internet if needed, even tho i access all my software through Tailscale.

#
### What are my main services or VMs running?

### Media stack on docker
- radarr            - managing movie collection
- sonarr            - managing TV series collection
- overseerr         - requesting new media
- qbittorrent       - for downloading Linux ISOs...
- tautulli          - statistics for Plex usage
- requestrr         - addition to overseerr, this connects requesting media to Discord server, you can request from chat
- prowlarr          - a indexer manager, to manage lists of torrent trackers
- bazarr            - subtitle manager for your media collection, automatic downloads of subtitles ( my wife's request)
- lidarr            - managing music / audiobook collection

These applications can work together seamlessly to automate my media collection.

Before i found this ["arr stack"](https://wiki.servarr.com/), i had to do a lot of steps to get my media, to place them in correct folders, rename them, and be able to play it on any of my devices, now i have fully automated workflow that will get any media based on single request from app web page in my homelab.

### Other docker containers
- homebridge        - older part of smart home ( unifi cameras with online stream to Apple HomeKit )
- homepage          - a dashboard to have neat list with some additional information and links in one place
- portainer         - docker aplication to manager your docker / swarm / kubernetes servers / clusters / aplications
- watchtower        - neat container that periodicly checks if your containers are at the latest version, updates them, recreates them on newest version and cleans up old unused images

#
### VMs I'm running

### [Plex](https://www.plex.tv/)
Plex is a player or "frontend" for media collections. It has web interface and apps for all mobile devices or TV OSes. It supports hardware acceleration on IntelQuickSync or Nvidia cards. Also not officialy supported, but some people tested on AMD GPUs or iGPUs.

### [Tailscale](https://tailscale.com/)
Tailscale is a fantastic solution for VPN if you dont have a public IP, but you want to access your network from outside, and keep it secure at the same time.

### [HomeAssistant](https://www.home-assistant.io/)
Open source home automation that puts local control and privacy first. Powered by a worldwide community of tinkerers and DIY enthusiasts.

My smart home consists of Loxone and HomeAssistant devices, but ost of automations are done through HomeAssistant.

### [Nginx](https://www.nginx.com/)
Nginx is a webserver engine that can be used as webserver, loadbalancer and reverse proxy. I use nginx as internal reverse proxy with some plugins as certbot to obtain SSL certificates for my internal and external domains.

### [Ubuntu Server](https://ubuntu.com/server)
Ubuntu 22.04 LTS is a distro of my home backup server, i chose this OS mostly for integrated ZFS support. Also made some simple backup bash scripts that i will share in upcoming posts.
