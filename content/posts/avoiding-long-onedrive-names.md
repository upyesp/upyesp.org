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

If your employer or university provides you with Microsoft OneDrive, you'll know how useful it can be right? The OneDrive folder name tends to be very long though, like "OneDrive - The University of Quahog".  The long name can get in the way, like in the prompt of an IDE, in a terminal session or when browsing files in Explorer. One simple command, `mklink`, can fix that.

<!--more-->

It is possible to rename the OneDrive folder, but the renaming method is very hacky, **high risk** and involves numerous changes within the Windows registry.  It is not recommended.

An alternative is to keep the long folder name unchanged and to simply avoid using it by creating a symbolic reference to it and using the symbolic reference instead.  The specific type of symbolic reference being used here is a [Junction Point](https://docs.microsoft.com/en-gb/windows/win32/fileio/symbolic-links).

The symbolic reference looks and behaves similar to a folder. You can give it a simple & short name, for example, "uni".

For example, the paths below point to the *same location*:

```Batchfile
C:\Users\pete\OneDrive - The University of Quahog\...

C:\Users\pete\uni\...
```

In the example above, the OneDrive folder called "OneDrive - The University of Quahog" exists, it remains unaffected and can continue to be used as normal.  Also, the much short folder, "uni", can be used in place of the long OnrDrive folder.

Firstly, make a note of the following 3 things:
1. The long name of the OneDrive folder, for example "OneDrive - The University of Quahog".
1. The **parent folder** of the OneDrive folder - *hint*, the parent folder is usually the *user* folder of the current Windows user, for example, "C:\Users\pete".
1. The name of the new folder you want to use, for example something short like, "uni".

## Method 1, Using a Command/CMD Prompt
- open a CMD prompt as an Administrator, so press <kbd>Windows</kbd> and type `cmd`, right-click on the top search result (Command Prompt App) and select "Run as administrator"
- navigate to the parent folder you noted above and create your new "folder" with a short name, using the `mklink` command with the `/J` parameter, for example:

```Batchfile
cd C:\Users\pete
```

then:

```Batchfile
mklink /J uni "OneDrive - The University of Quahog"
```

You're done, you can now close the cmd terminal and use *uni*, or whatever name you created, as an alternative folder to your long OneDrive folder.

**Tip:** add it to you Quick access shortcuts in Explorer, so in Explorer navigate to your new folder, for example, C: > Users > uni, right-click on *uni* and select "Pin to Quick access".

## Method 2, for More Experienced Windows Users
- open a PowerShell terminal as an administrator and enter the following command, remembering to use the 3 values you noted above:

```PowerShell
New-Item -ItemType Junction -Path 'C:\Users\pete\' -Name 'uni' -Target 'C:\Users\pete\OneDrive - The University of Quahog'
```
