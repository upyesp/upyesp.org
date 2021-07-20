---
title: "How To Avoid Long OneDrive Folder Names"
description: OneDrive from Microsoft is excellent, but those long folder names get in the way.  
date: 2021-07-20T14:13:00+01:00
draft: false
toc: false
tags:
  - OneDrive
  - Explorer
categories:
  - Windows
---

If your employer or university provides you with Microsoft OneDrive, it is so useful right? But the long folder name can get in the way, like in the prompt of an IDE, terminal session or when browsing files in Explorer. One simple command, ```mklink```, can fix that.

<!--more-->

It is possible to rename this folder, but the renaming method is very hacky, **high risk** and involves numerous changes within the Windows registry.  It is not recommended.

An alternative is to keep the long folder name unchanged and to simply avoid using it by creating a symbolic reference to it and using the reference instead.  The specific type of symbolic reference being used here is a [Junction Point](https://docs.microsoft.com/en-gb/windows/win32/fileio/symbolic-links).

For example, the paths below point to the *same file*, in the *same location*:

```dos
C:\Users\pete\OneDrive - The University of Quahog\CS\misc\CampusMap.pdf

C:\Users\pete\uni\CS\misc\CampusMap.pdf
```

## tl;dr

1. press the Windows key, type `cmd`, right-click on the top search result (Command Prompt App) and select "Run as administrator"
1. navigate to the parent folder of the OneDrive folder - *hint*, it is usually in the *user* folder of the current Windows user, for example: ```cd C:\Users\pete```
1. create a Junction Point using the ```mklink``` command with the ```/J``` parameter, for example if you want to call your symbolic reference *uni*, use: ```mklink /J uni "OneDrive - The University of Quahog" ```
1. **done**, you can now close the cmd terminal and use *uni*, or whatever name you created, as an alternative route to your long OneDrive folder
1. for extra convenience, in Explorer, navigate to your link, (in ```C:\Users\pete```), right click on *uni* and select "Pin to Quick access"