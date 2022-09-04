---
title: "How To Avoid Long OneDrive Folder Names"
description: OneDrive from Microsoft is excellent, but those long folder names get in the way.  
date: 2022-09-04T14:13:00+01:00
draft: false
toc: false
pinned: false
featuredImage: ''
tags: [OneDrive, Explorer]
categories: [Windows]
---

If your employer or university provides you with Microsoft OneDrive, you'll know how useful it can be. But the OneDrive folder name tends to be very, very long, like "OneDrive - The University of Quahog".  The long name can get in the way, for example when in the prompt of an IDE, in a terminal session or when browsing files in Explorer. One simple command, `mklink`, can fix that.

<!--more-->

It is possible to rename the OneDrive folder, but the renaming method is very hacky, **high risk** and involves numerous changes within the Windows registry.  It is not recommended.

An alternative is to keep the long folder name unchanged and to simply avoid using it by creating a symbolic link ("symlink", for short) to it and using the symlink instead.  The specific type of symlink being used here is a [Junction Point](https://docs.microsoft.com/en-gb/windows/win32/fileio/symbolic-links).

> The symlink looks and behaves similar to a folder. You can give it a simple & short name, for example, "uni".

![screenshot of Quick access in Explorer](/images/mklinkqa2.png "Quick access to your handy new shortname for OneDrive")

For example, the paths below point to the *same location*:

```Powershell
C:\Users\fred\OneDrive - The University of Quahog\...

C:\Users\fred\uni\...
```

In the example above, the OneDrive folder called "OneDrive - The University of Quahog" exists, it remains unaffected and can continue to be used as normal.  Also, the much short folder, "uni", can be used in place of the long OnrDrive folder.

Firstly, make a note of the following 3 things:
1. The long name of the OneDrive folder, for example "OneDrive - The University of Quahog".
1. The **parent folder** of the OneDrive folder - *hint*, the parent folder is usually the *user* folder of the current Windows user, for example, "C:\Users\fred".
1. The name of the symlink you want to use, for example something short like, "uni".

## Method 1, Using a Command/CMD Prompt
- open a CMD prompt, so press <kbd>Windows</kbd> and type `cmd`, click on the top search result (Command Prompt App)
- navigate to the parent folder you noted above and create your new symlink with a short name, using the `mklink` command with the `/J` parameter, for example:

```Batchfile
cd C:\Users\fred
```

then:

```Batchfile
mklink /J uni "OneDrive - The University of Quahog"
```

![screenshot of CMD prompt with example command for mklink](/images/mklinkhi.png "using mklink to create a symlink")

You're done, you can now close the cmd terminal and use *uni*, or whatever name you created, as an alternative folder to your long OneDrive folder.

**Tip:** add it to you Quick access shortcuts in Explorer, so in Explorer navigate to your new folder, for example, C: > Users > fred > uni, right-click on *uni* and select "Pin to Quick access".

![screenshot of right-click context menu with Pin to Quick access selected](/images/mklinkqa.png "right-click to enable Pin to Quick access")

## Method 2, using PowerShell
- open a PowerShell prompt, enter the following command, remembering to use the 3 values you noted above:

```Powershell
New-Item -ItemType Junction -Path 'C:\Users\fred\' -Name 'uni' -Target 'C:\Users\fred\OneDrive - The University of Quahog'
```
