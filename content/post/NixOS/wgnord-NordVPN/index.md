---
title: NordVPN on NixOS with wgnord
description: This is quick guide to run NordVPN on NixOS with wgnord.
slug: wgnord-nixos-nordvpn
date: 2024-07-17 12:22:00+0000
image: cover.jpg
categories:
    - Desktop
    - Linux
tags:
    - NixOS
weight: 1
---

# wgnord
NordVPN is not available to install yet on NixOS. Though, there are a few ways to use it on NixOS. Here is one relatively easy by using [wgnord](https://github.com/phirecc/wgnord).

## Install
Packages to install/include in the nix config:
- openresolv
- wireguard-tools
- wgnord

Discussion & tips from: https://github.com/NixOS/nixpkgs/issues/101864#issuecomment-1859214194

```bash
sudo mkdir /etc/wireguard # create if it doesn't exist
sudo mkdir -p /var/lib/wgnord # create if it doesn't exist
sudo nano /var/lib/wgnord/template.conf	# copy content from https://raw.githubusercontent.com/phirecc/wgnord/master/template.conf
sudo wgnord l "keyxxx" # create a token in the NordVPN dashboard
sudo wgnord c Germany # connect to a server, e.g Germany 
sudo wgnord d # disconnect
```

---
Cover image by <a href="https://unsplash.com/@pawel_czerwinski">Pawel Czerwinski</a> on <a href="https://unsplash.com/photos/a-black-and-blue-abstract-background-with-squares-and-rectangles-O_lLr6e8NtQ">Unsplash</a>

