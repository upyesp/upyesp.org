---
title: "Browsing A WSL Distro In Explorer"
description: How to use Explorer to work with files contained in a WSL distro.  
date: 2021-10-01T11:37:01+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [WSL, Explorer]
categories: [Windows, Linux]
series: [Windows Subsystem for Linux]
---

If you have installed WSL and one or more linux distributions, it is possible to work with the contents of their file systems from within Windows Explorer.

<!--more-->

![screenshot of Windows Explorer, highlighting the address bar, pin to quick access button and the list of quick access short cuts](/images/wsl-explorer-quickaccess.png "Browsing WSL Distros in Explorer")

1. start WSL
1. start Explorer (for example, <kbd>Windows</kbd> + <kbd>E</kbd>)
1. in the address bar, type `\\wsl$\` + <kbd>Enter</kbd>
1. the folder content pane shows each WSL distro installed
1. double-click on a distro to access it's file system

Tip: When you enter `\\wsl$\` in the address bar, right-click on a specific distro then in the context-menu select "Pin to Quick access".  You'll be able to navigate to it quickly and without having to start WSL first.