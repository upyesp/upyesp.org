---
title: "Use An Alias To Quickly Find Your IP Address"
description: How to create an Alias as a quick & easy way to retrieve your IP address, in Linux and Windows.
date: 2022-03-30T11:37:01+00:00
draft: false
toc: true
featuredImage: ''
tags: [Bash, PowerShell]
categories: [Windows, Linux]
---

Here's how to create Alias commands to simplify tasks on the command line.  The examples given relate to retrieving IP addresses.  The process is shown for Linux using Bash and Windows using PowerShell.

<!--more-->

![screenshot of a terminal running Linux with the Bash shell.  The user has entered the command "ipext" and the external IP address has been returned](/images/AliasIP.png "Using an Alias to return the external IP address")

## Definitions - Internal & External IP Address

Your computer has an IP address on the LAN it is connected to. This blog post will refer to that address as the _internal IP address_, typical examples being... `192.168.1.12/24` at home or `10.23.8.7/20` on a corporate network.

Your computer also has an IP address as seen by devices from external to the LAN, for example by servers on the internet.  This blog post will refer to that address as the _external IP address_, for example `123.44.23.87`. If you open a browser and Google "whats my ip", you will find yours.

## Linux: Creating Aliases In Bash To Return The Internal & External IP Address

> TL;DR: append the following lines to the .bashrc file to create aliases `ipint` and `ipext`:

```zsh
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

```zsh
ip addr | awk '$1=="inet" && $3!="scope" {print $2}'

ip addr | awk -F' |/' '$5=="inet" && $8!="scope" {print $6}'
```

#### External Address

In order to find the external IP address, a service beyond the LAN needs to be called, such as a server on the internet. Many services exist, this example uses `icanhazip.com`.  This can be changed to your own preferred service.

```zsh
curl icanhazip.com
```

### Creating Aliases For The Bash Commands

When creating an Alias for the above commands certain characters, such as `"` and `$` must be be escaped for the command string to be parsed successfully. This can be achieved by inserting a `\` character before them. So the Alias commands are:

```zsh
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

```zsh
sudo nano ~/.bashrc
```

![screenshot of a terminal running Linux with the Bash shell.  The editor Nano is running and the contents of .bashrc are displayed.](/images/AliasIPNano.png "Using nano to edit .bashrc")


## Windows: Creating Aliases In PowerShell To Return The Internal & External IP Address

> TL;DR: append the following lines to $PROFILE to create aliases `ipint` and `ipext`:

```powershell
function Get-IP-Internal { 
    $myip = Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp
    Write-Host "$($myip.IPAddress)/$($myip.PrefixLength)"
}
Set-Alias -Name ipint -Value Get-IP-Internal


function Get-IP-External {
    curl.exe icanhazip.com
}
Set-Alias -Name ipext -Value Get-IP-External
```

### How To Retrieve IP Addresses Using PowerShell

#### Aliases & Functions

So far this article has talked about Aliases.  These are supported in PowerShell, though they are implemented differently than Linux.  There is a restriction regarding [Alias parameters and passing values](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.2) - see "Example 5". As shown in that example, this can be easily overcome by creating a [Function](https://docs.microsoft.com/en-us/powershell/scripting/learn/ps101/09-functions?view=powershell-7.2) and setting an Alias to it.

#### Address On The LAN, Using `Get-NetIPAddress`

PowerShell provides several methods to retrieve IP addresses.  The examples below use `Get-NetIPAddress`.  The [Microsoft docs page](https://docs.microsoft.com/en-us/powershell/module/nettcpip/get-netipaddress?view=windowsserver2022-ps) details various parameters for this command. In my examples below I specify `IPv4` addresses. Also, I'm requesting IP addresses issued by `DHCP`.  You may want to adjust these to suit your requirements. Examples of the `Get-NetIPAddress` command include:

```powershell
Get-NetIPAddress -AddressFamily IPv4

Get-NetIPAddress -AddressFamily IPv4 | Format-Table 

Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Table  -Property IPAddress,PrefixLength

Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Table -HideTableHeaders -Property IPAddress,PrefixLength

(Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Table -HideTableHeaders -Property IPAddress,PrefixLength | Out-String).Trim()

Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Wide -Property IPAddress

(Get-NetIPAddress -AddressFamily IPv4 -PrefixOrigin Dhcp | Format-Wide -Property IPAddress | Out-String).Trim()
```

#### External IP Address

As with Linux, in order to find the external IP address, a service beyond the LAN needs to be called, such as a server on the internet. Many services exist, this example uses `icanhazip.com`.  This can be changed to your own preferred service.

```powershell
function Get-IP-External {
    curl.exe icanhazip.com
}
Set-Alias -Name ipext -Value Get-IP-External
```

### Adding Aliases To The $PROFILE File

As with Linux, Aliases in PowerShell typically only exist in the session in which they are created.  A simple way to ensure the `ipint` and `ipext` persist in PowerShell sessions is to add their definition to the $PROFILE file.  This can be edited with an editor, such as `notepad` or `VS Code`, like this:

```powershell
notepad $PROFILE

code $PROFILE
```

![screenshot of the VS Code editor with the contents of the $PROFILE displayed.](/images/AliasIPVSCODE.png "Using VS Code to edit $PROFILE")




