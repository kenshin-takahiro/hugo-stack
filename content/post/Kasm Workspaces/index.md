---
title: Kasm Workspaces
description: How to host Kasm Workspaces on your server.
slug: kasm-workspaces
date: 2024-07-18 12:22:00+0000
image: cover.jpg
categories:
    - Homelab
    - Linux
    - Server
tags:
    - Homelab
weight: 1
---

# Kasm Workspaces
[Kasm⁠ Workspaces](https://www.kasmweb.com) is a docker container streaming platform for delivering browser-based access to desktops, applications, and web services.


## Install with Docker Compose
Template and instructions from [linuxserver.io](https://hub.docker.com/r/linuxserver/kasm).

Create a file `compose.yaml` and copy paste inside it:

```yaml
services:
  kasm:
    image: lscr.io/linuxserver/kasm:latest
    container_name: kasm
    privileged: true
    environment:
      - KASM_PORT=443
      - DOCKER_HUB_USERNAME=USER #optional
      - DOCKER_HUB_PASSWORD=PASS #optional
      - DOCKER_MTU=1500 #optional
    volumes:
      - ./data:/opt
      - ./profiles:/profiles #optional
      - ./dev/input:/dev/input #optional
      - ./run/udev/data:/run/udev/data #optional
    ports:
      - 3006:3000 #custom port 3006
      - 446:443 #custom port 446
    restart: unless-stopped
```

_Note: Ports 3006 & 446 are custom, make them anything you want, but don't change the right side: port 3000 & 443._

### Start the container
```
docker compose pull
docker compose up -d
```

### Access
Access the interface from: `your.ip:446`

### Optimizations
Disable pulseaudio to lower cpu consumption:
- Go to Admin->Workspaces->Edit a workspace:
- In Docker Run Config Override (JSON)
		Add inside the "environment": {}:
		, "START_PULSEAUDIO": "0"


Example:
```
{
  "hostname": "kasm",
  "environment": {
    "TERMINAL_ARGS": "--fullscreen --hide-borders --hide-menubar --zoom=-1 --hide-scrollbar",
    "START_PULSEAUDIO": "0"
  }
}
```

---
Cover image by <a href="https://unsplash.com/@pawel_czerwinski">Pawel Czerwinski</a> on <a href="https://unsplash.com/photos/a-black-and-gold-abstract-painting-of-cubes-9QL8ZbEP1ew">Unsplash</a>
