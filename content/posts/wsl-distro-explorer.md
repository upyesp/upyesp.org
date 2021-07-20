---
title: "Browsing A WSL Distro In Explorer"
description: How to use Explorer to work with files contained in a WSL.  
date: 2021-07-20T11:37:01+01:00
draft: false
toc: true
authors:
  - upyesp
tags:
  - WSL 
  - Explorer
categories:
  - Windows
  - Linux
series:
  - Windows Subsystem for Linux
---

If you have installed WSL and one or more linux distributions, it is possible to work with the contents of their file systems from Windows Explorer.  

- start Explorer (for example, press Windows + e)
- in the address bar, type `\\wsl$\`, press ENTER
- the folder content pane shows each WSL distro installed
- double-click on a distro to view it's file system and work with files

Tip: When you enter `\\wsl$\` in the address bar, click the "Pin to Quick access" button from the "Home" tab.