---
title: "Launching Windows Apps From Within WSL"
description: While using a Linux in Windows it is possible to run Windows applications. 
date: 2024-01-22T10:29:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
featured: false
carousel: false
tags: [WSL, VSCode]
categories: [Windows, Linux]
series: [Windows Subsystem for Linux]
---

The interoperability provided by WSL enables calling or running Windows applications directly from within the Linux command line.

<!--more-->

From within the WSL shell (typically Bash), type the name of the Windows executable, with ".exe" appended, followed by any arguments you want to include. 

Some examples:

## Notepad

```BASH
notepad.exe .bashrc
```
Will launch the Windows program, `Notepad`.  A file name can be included as a parameter.  In the above example, a file name has been passed, ".bashrc", which happens to be a hidden file in Linux. When Notepad starts in Windows, the Linux file ".bashrc" will be open for editing and can be saved.

## Explorer

```BASH
explorer.exe .
```

Launches the Windows Explorer. The "." parameter specifies Explorer to open with the current location in the Linux file system. So Explorer launches in Windows, browsing Linux files.  By specifying a path to a folder, Explorer will open in Windows, browsing the contents of that folder.  

## VSCode

```BASH
code.exe .
```
Opens the Windows app VSCode, in "remote WSL" mode, allowing VSCode to support the development of native Linux apps. As with Explorer above, the "." parameter specifies to work with the current location in the Linux file system.
