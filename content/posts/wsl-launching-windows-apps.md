---
title: "Launching Windows Apps From Within WSL"
description: While using a Linux in Windows it is possible to run Windows applications..  
date: 2021-07-21T10:29:00+01:00
draft: false
toc: true
tags:
  - WSL 
  - VSCode
categories:
  - Windows
  - Linux
series:
  - Windows Subsystem for Linux
---

The interoperability provided by WSL enables calling or running Windows applications directly from within the Linux command line.

<!--more-->

From within the WSL shell, type the name of the Windows executable, with ".exe" appended, followed by any arguments you want to include. 

Some examples:

```Bash
notepad.exe .bashrc
```
Will launch the Windows program Notepad, opening the linux hidden file, ".bashrc" for editing.


```Bash
explorer.exe .
```
Launches the Windows Explorer, defaulting to the current location in the linux file system.

```Bash
vscode.exe .
```
Opens the Windows app VSCode, in "remote WSL" mode, allowing VSCode to support the development of native Linux apps.
