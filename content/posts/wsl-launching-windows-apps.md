---
title: "Launching Windows Apps From Within WSL"
description: While using a Linux in Windows it is possible to run Windows applications. 
date: 2021-07-21T10:29:00+01:00
draft: false
toc: true
featuredImage: ''
tags: [WSL, VSCode]
categories: [Windows, Linux]
series: [Windows Subsystem for Linux]
---

The interoperability provided by WSL enables calling or running Windows applications directly from within the Linux command line.

<!--more-->

From within the WSL shell, type the name of the Windows executable, with ".exe" appended, followed by any arguments you want to include. 

Some examples:

## NotePad

```Bash
notepad.exe .bashrc
```
Will launch the Windows program, Notepad.  A file name can be included as a parameter.  In the above example, a file name has been passed, ".bashrc", which happens to be a hidden file in linux. When Notepad starts in Windows, the linux file ".bashrc" will be open for editing/saving.

## Explorer

```Bash
explorer.exe .
```
Launches the Windows Explorer. The "." parameter specifies Explorer to start the current location in the linux file system. So Explorer launches in Windows, browsing linux files.

## VSCode

```Bash
code.exe .
```
Opens the Windows app VSCode, in "remote WSL" mode, allowing VSCode to support the development of native Linux apps. As with Explorer above, the "." parameter specifies to work with the current location in the linux file system.
