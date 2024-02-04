---
title: Git Cheatsheet in 2024
description: This is a cheatsheet with the most common commands in Git for the year 2024.
slug: git-cheatsheet-2024
date: 2024-02-04 11:23:00+0000
image: cover.jpg
categories:
    - WebDev
tags:
    - git
weight: 1
---

# Git

## Install
- https://git-scm.com/download/linux
- https://docs.github.com/en/get-started/quickstart/set-up-git

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
git --version
```

## Configure

### Configure git settings
```
git config --global user.name "Xxxxxx"
git config --global user.email "xxxxxx@xxxxxx.xyz"

# Enable main as the default branch
git config --global init.defaultBranch main

# Enable colours
git config --global color.ui auto

# Check the configuration
git config --list
```

### Generate ssh key
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
```
ssh-keygen -t ed25519 -C "xxxxxx@xxxxxx.xyz"

# save in:
/home/user/.ssh/id_ed25519

# start the ssh agent:
eval "$(ssh-agent -s)"

# add the new key in the agent we just startred:
ssh-add ~/.ssh/id_ed25519

# see the new public key:
cat ~/.ssh/id_ed25519.pub
```

Using ssh to connect with GitHub:
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/using-ssh-agent-forwarding

## Connect to Github Repo

### First initialization
- https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository

```
cd webdev/sites/myWebsite
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:xxxxxx/xxxxxx.git
git push -u origin main
```

### Connect to Remote
- https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes
- https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories

```
git clone git@github.com:xxxxxx/xxxxxx.git

# Restore Submodules (themes) if any:
git submodule update --init --recursive

git remote -v
git remote show origin
```

### Make Commits
- https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository

```
git status
git add file
git commit -m "commit"
git push -u origin main
```

Cover photo by <a href="https://unsplash.com/@pawel_czerwinski">Pawel Czerwinski</a> on <a href="https://unsplash.com/photos/an-abstract-photo-of-a-green-and-black-background-pSNM2lEOnTo">Unsplash</a>
