---
title: "Use An Alias To Quickly Find Your IP Address - Windows & Linux"
description: How to create an Alias as a quick & easy way to retrieve your IP address, in Linux and Windows.
date: 2022-08-21T11:37:01+00:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [Bash, PowerShell]
categories: [Windows, Linux]
---

Here's how to create Alias commands to simplify tasks on the command line.  The examples given relate to retrieving IP addresses.  The process is shown for Linux using Bash and Windows using PowerShell.

<!--more-->

![screenshot of a terminal running Linux with the Bash shell.  The user has entered the command "ipext" and the external IP address has been returned](/images/AliasIP.png "Using an Alias to return the external IP address")

## Definitions - "Internal" & "External" IP Addresses

Your computer has an IP address on the LAN it is connected to. This blog post will refer to that address as the _internal IP address_, typical examples being... `192.168.1.12/24` at home or `10.23.8.7/20` on a corporate network.

Your computer also has an IP address as seen by devices from external to the LAN, for example by servers on the internet.  This blog post will refer to that address as the _external IP address_, for example `123.44.23.87`. If you open a browser and Google "whats my ip", you will find yours.

[Jump to Windows Method](#windows)

## Linux: Creating Aliases In Bash To Return The Internal & External IP Address {#linux}

> TL;DR
> 1. Open a terminal.
> 1. Edit file .bashrc by entering `sudo nano ~/.bashrc`.
> 1. Copy/paste the lines below to the end of .bashrc.
> 1. Exit `nano` by pressing <kbd>Ctrl</kbd> + <kbd>x</kbd> and press <kbd>y</kbd> to save changes.
> 1. Restart Bash with `exec bash`.
> 1. Done! You can now use the newly created aliases `ipint` and `ipext` to return IP addresses.

```Bash
# Alias for IP address on the LAN.
# - this version returns the address + CIDR/subnet suffix e.g. xxx.xxx.xxx.xxx/xx
alias ipint="ip addr | awk '\$1==\"inet\" && \$3!=\"scope\" {print \$2}' "
# - this version returns the address only e.g. xxx.xxx.xxx.xxx
#alias ipint="ip addr | awk -F' |/' '\$5==\"inet\" && \$8!=\"scope\" {print \$6}' "

# Alias for device's IP address externally, from the internet.
# An external service is required to return the external IP address
alias ipext="curl icanhazip.com"
```

### How To Retrieve IP Addresses Using Bash

#### Address On The LAN

Linux provides several methods to retrieve IP addresses.  The examples below use `ip addr`, piping the output to `awk` to select the values of interest.

The following two commands return the internal IP address. The first example returns the IP with the CIDR suffix (subnet range), the second without.

```Bash
ip addr | awk '$1=="inet" && $3!="scope" {print $2}'

ip addr | awk -F' |/' '$5=="inet" && $8!="scope" {print $6}'
```

#### External Address

In order to find the external IP address, a service beyond the LAN needs to be called, such as a server on the internet. Many services exist, this example uses `icanhazip.com`.  This can be changed to your own preferred service.

```Bash
curl https://icanhazip.com
```

Note that other external services are available, for example:

```Bash
curl https://ipinfo.io
```

Also, using the Linux DNS util command, `dig`:

```Bash
dig TXT o-o.myaddr.l.google.com @ns1.google.com +short
dig TXT ch whoami.cloudflare @1.0.0.1
```

### Creating Aliases For The Bash Commands

When creating an Alias for the above commands certain characters, such as embedded `"` and `$` must be be escaped for the `Alias` command string to be parsed successfully. This can be achieved by inserting a `\` character before, to escape them. So the Alias commands are:

```Bash
#this version returns the address + CIDR/subnet suffix e.g. xxx.xxx.xxx.xxx/xx
alias ipint="ip addr | awk '\$1==\"inet\" && \$3!=\"scope\" {print \$2}' "
#this version returns the address only e.g. xxx.xxx.xxx.xxx
#uncomment the line below if you want to use this version
#alias ipint="ip addr | awk -F' |/' '\$5==\"inet\" && \$8!=\"scope\" {print \$6}' "

# Alias for device's IP address as seen externally, from the internet.
# An external service is required to return the external IP address
alias ipext="curl icanhazip.com"
```

### Adding Aliases To The .bashrc File

Aliases typically only exist in the session in which they are created.  A simple way to ensure the `ipint` and `ipext` persist in Bash sessions is to add their definition to the .bashrc file in your home directory.  This can be edited with `nano`.  Note that root privileges are required, so use `sudo`, like this:

```Bash
sudo nano ~/.bashrc
```

![screenshot of a terminal running Linux with the Bash shell.  The editor Nano is running and the contents of .bashrc are displayed.](/images/AliasIPNano.png "Using nano to edit .bashrc")

Exit `nano` by pressing <kbd>Ctrl</kbd> + <kbd>x</kbd> and press <kbd>y</kbd> to save changes.

Then restart Bash with `exec bash`.

That's it, done.  Use the newly created aliases `ipint` and `ipext` to return IP addresses.

## Windows: Creating Aliases In PowerShell To Return The Internal & External IP Address  {#windows}

> TL;DR
> 1. Open a PowerShell terminal.
> 1. Edit file $PROFILE by entering `notepad $PROFILE`.
> 1. Copy/paste the lines below to the end of $PROFILE.
> 1. Save and exit notepad.
> 1. Reload the new version by entering `. $PROFILE`.
> 1. Done! You can now use the newly created aliases `ipint` and `ipext` to return IP addresses in a PowerShell terminal session.

```Powershell
function Get-IPInternal { 
    $IPAddr = Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp
    Write-Output "$($IPAddr.IPAddress)/$($IPAddr.PrefixLength)"
}
Set-Alias -Name ipint -Value Get-IPInternal


function Get-IPExternal {
    $Response = Invoke-WebRequest -URI icanhazip.com
    $Response.content
}
Set-Alias -Name ipext -Value Get-IPExternal
```

### How To Retrieve IP Addresses Using PowerShell

#### Aliases & Functions

So far this blog post has talked about Aliases.  These are supported in PowerShell, though they are implemented differently than Linux.  There is a restriction regarding [Alias parameters and passing values](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.2) - see "Example 5". As shown in that example, this can be easily overcome by creating a [Function](https://docs.microsoft.com/en-us/powershell/scripting/learn/ps101/09-functions?view=powershell-7.2) and setting an Alias to it.

#### Address On The LAN, Using `Get-NetIPAddress`

PowerShell provides several methods to retrieve IP addresses.  The examples below use `Get-NetIPAddress`.  The [Microsoft docs page](https://docs.microsoft.com/en-us/powershell/module/nettcpip/get-netipaddress?view=windowsserver2022-ps) details various parameters for this command. In my examples below I specify `IPv4` addresses. Also, I'm requesting IP addresses issued by `DHCP`.  You may want to adjust these to suit your requirements. Examples of the `Get-NetIPAddress` command include:

```Powershell
Get-NetIPAddress -AddressFamily IPv4

Get-NetIPAddress -AddressFamily IPv4 | Format-Table 

Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Table  -Property IPAddress,PrefixLength

Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Table -HideTableHeaders -Property IPAddress,PrefixLength

(Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Table -HideTableHeaders -Property IPAddress,PrefixLength | Out-String).Trim()

Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Wide -Property IPAddress

(Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Wide -Property IPAddress | Out-String).Trim()
```

This is the version I settled on.  It provides the IPv4 address, along with the CIDR suffix.  Also, the output exactly matches the Linux version above.

```Powershell
function Get-IPInternal { 
    $IPAddr = Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp
    Write-Output "$($IPAddr.IPAddress)/$($IPAddr.PrefixLength)"
}
Set-Alias -Name ipint -Value Get-IPInternal
```


#### External IP Address

As with Linux, in order to find the external IP address, a service beyond the LAN needs to be called, such as a server on the internet. Many services exist, this example uses `icanhazip.com`.  This can be changed to your own preferred service.

```Powershell
function Get-IPExternal {
    $Response = Invoke-WebRequest -URI icanhazip.com
    $Response.content
}
Set-Alias -Name ipext -Value Get-IPExternal
```

### Adding Aliases To The $PROFILE File

As with Linux, Aliases in PowerShell typically only exist in the session in which they are created.  A simple way to ensure the `ipint` and `ipext` persist in PowerShell sessions is to add their definition to the $PROFILE file.  This can be edited with an editor, such as `notepad` or `VS Code`, like this:

```Powershell
notepad $PROFILE

code $PROFILE
```

![screenshot of the VS Code editor with the contents of the $PROFILE displayed.](/images/AliasIPVSCODE.png "Using VS Code to edit $PROFILE")

Save the changes exit the editor.

Force a reload the new version by entering `. $PROFILE`.

That's it, done.  Use the newly created aliases `ipint` and `ipext` to return IP addresses.


