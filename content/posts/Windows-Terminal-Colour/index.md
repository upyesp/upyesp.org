---
title: "Adding Colour & Icons to File Listings in a Terminal"
description: Add colour to file listings in PowerShell. 
date: 2023-12-28T11:34:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [PowerShell, NerdFonts]
categories: [Windows]
series: [Windows Terminal]
---

Adding icons and colour to folders and files improves the user experience in PowerShell.

<!--more-->

![screenshot of PowerShell with colour file names and icons](/images/terminal-icons.png "icons and colour in file listings")

The [Terminal-Icons](https://github.com/devblackops/Terminal-Icons) project is a PowerShell module adding icons and colour to directory listings.

## Prerequisite

For the PowerShell terminal session to include icons with filenames, the session must first be configured to used a font that includes icons.  The standard fonts shipped with Windows do not include the required fonts.

The [Nerd Fonts](https://www.nerdfonts.com/) project is an excellent source for such fonts.  There are many, for example "Caskaydia Cove Nerd Font". 

Download a font, install it - choosing "INSTALL FOR ALL USERS" and configure PowerShell to use it.

## Install Terminal-Icons

Start a PowerShell terminal session. Enter the following:

```Powershell
Install-Module -Name Terminal-Icons -Repository PSGallery
```

To ensure the module runs every time you open a PowerShell session, add an import of the module to your PowerShell profile. So, edit $PROFILE (`notepad $PROFILE`) and add this line:

```Powershell
Import-Module Terminal-Icons
```

Save the profile.

To see the change, restart PowerShell or reload the profile, with:

```Powershell
. $PROFILE
```

If at some point you want to remove the module, enter:

```Powershell
Uninstall-Module -Name Terminal-Icons
```

And remove the import from your profile.