---
title: "Windows SSH To Remote Server With FIDO2 + Hardware Key (YubiKey) Multi Factor Authentication MFA / 2FA"
description: Use the latest version of OpenSSH in Windows with a YubiKey for more secure authentication. 
date: 2022-07-03T08:34:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [PowerShell]
categories: [Windows, Linux]
series: [Windows SSH]
---

Windows ships with OpenSSH.  Here's how to update the version then use it with MFA option FIDO2 + a hardware security key, such as a YubiKey.

<!--more-->

SSH is a core element of the [OpenSSH](https://www.openssh.com/) project.  Several Unix-like operating systems are supported. Microsoft Windows is also supported.  This blog details using SSH on the Windows command-line, secured with multi factor authentication (MFA / 2FA). 

> TL;DR
> 1. Open a PowerShell console as Admin.
> 1. Install the latest version of [OpenSSH for Windows](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH-Using-MSI).
> 1. Generate a new key pair, with: `ssh-keygen -t ecdsa-sk`.
> 1. Copy the new .pub key to the remote server, with: `Get-Content $env:USERPROFILE\.ssh\id_ecdsa_sk.pub | ssh alice@example.com 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'` (change alice@example.com to your user/server).
> 1. SSH to the server, with: `ssh alice@example.com` (change alice@example.com to your user/server).

## Install The Latest Version of OpenSSH for Windows

SSH is included in Windows as a `Windows Optional Feature`, see the [Microsoft Docs](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) page for more information.  As such it is updated as part of Windows Feature Updates. 

To find the version currently installed, use:

```PowerShell
ssh -V
```

At the time of writing, this returns: "OpenSSH_for_Windows_8.6p1, LibreSSL 3.4.3".  This version does not support FIDO2 hardware security keys (YubiKeys), so it needs to be updated to a newer version.

> Ok, funny story... according to [Microsoft's development repo](https://github.com/PowerShell/openssh-portable#readme), the latest *stable* release of OpenSSH for Windows, which they recommend, appears to be available as __source code only, no installer__, hosted (along with the source code for other platforms), at [OpenSSH](https://www.openssh.com/portable.html). No installer for the latest stable release, how weird is that? The [Microsoft Wiki](https://github.com/PowerShell/openssh-portable/wiki) points to the most recent installation package as being for the latest __beta version__ only. It appears the latest stable version is not available to install, only to build/compile yourself.

So, to install the latest version available to the public, the latest *beta* version:

1. Uninstall the version of OpenSSH that was delivered with Windows, using [this method](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse#uninstall-openssh-using-windows-settings).
1. Open a PowerShell terminal and install the latest beta version, by either of 2 methods... using winget, ```winget install Microsoft.OpenSSH.Beta```, or follow [these instructions](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH-Using-MSI) to install the MSI and update the System Path.
1. Close and re-open the PowerShell terminal.

The SSH version should now have changed, check it again, with:

```PowerShell
ssh -V
```

At the time of writing, this is now: "OpenSSH_for_Windows_9.5p1, LibreSSL 3.8.2", which supports FIDO2 hardware security keys.

## Install Or Update OpenSSH On The Remote Linux Server

Updating OpenSSH on the remote server may not be required, but it is recommended. The minimum version required for the method in this blog is: "OpenSSH 8.2p1".

On Debian based systems:

```Bash
# establish current version
ssh -V
# update to latest version
sudo apt update
sudo apt install openssh-server
# restart SSH service
sudo systemctl restart ssh.service
```

## Multifactor Authentication - FIDO2 With A Hardware Security Key, Such As YubiKey

> OpenSSH supports a number of configurations for FIDO2.  For more details and to determine which configuration best suits your needs, see the [OpenSSH Manual Pages](https://www.openssh.com/manual.html). See also the documentation for the specific hardware security key you are using, for example [YubiCo](https://developers.yubico.com/SSH/Securing_SSH_with_FIDO2.html).

### Set A FIDO2 PIN On Your Hardware Security Key

If you have already set a FIDO2 PIN on your hardware security key, for example if you have used the security key with other FIDO2 services, then you can skip this step.

To set a FIDO2 PIN on your hardware security key, follow the instructions provided by the manufacturer.  For example, if you are using a YubiKey, then use their Windows App, [YubiKey Manager](https://www.yubico.com/support/download/yubikey-manager/) and follow the instructions [here](https://support.yubico.com/hc/en-us/articles/4402836718866-Understanding-YubiKey-PINs#:~:text=PIN%20Management,FIDO2%20and%20clicking%20Set%20PIN.).

### Create An SSH Key Pair

Use the `ssh-keygen` command to create a public/private key pair. 

The type of key used in this example is "ecdsa-sk".  You could alternatively use "ed25519-sk", if you hardware security key supports it.

A simple example would be:

```PowerShell
ssh-keygen -t ecdsa-sk
```

You might want to add to this and use the following optional parameters:

- use `-O` to specify the application (SSH) and remote server name (in this example, "server21"), *example:* `-O application=ssh:server21`
- use `-C` to specify a comment, *example:* `-C "Host:ThinkPadX1 Security Key:yubikeyusb"`

For example:

```PowerShell
ssh-keygen -t ecdsa-sk -O application=ssh:server21 -C "Host:ThinkPadX1 Security Key:yubikeyusb"
```

Follow the on-screen instructions. As you are using a hardware security key, you will see a number of prompts generated by Windows Secuirty, guiding you through the process of when to enter the FIDO2 PIN and when to physically touch your key.

You are about to use your hardware security key:

![screenshot of a security prompt from Microsoft Windows, informing the user they are about to use their security key for OpenSSH.](/images/ssh-secuirtykey1.png "First security prompt")

Make & model will be shared:

![screenshot of a security prompt from Microsoft Windows, warning.](/images/ssh-secuirtykey2.png "Warning that the make and model of the key will be shared with SSH")

Enter the FIDO2 PIN:

![screenshot of a security prompt from Microsoft Windows, requesting a FIDO2 PIN.](/images/ssh-secuirtykey3.png "Enter the FIDO2 PIN")

Touch the key to, prove you are physically present:

![screenshot of a security prompt from Microsoft Windows, touch the key.](/images/ssh-secuirtykey4.png "Touch the key to prove you are physically present")

- follow the instructions in the terminal window
- enter a specific name for the key pair you are creating, or accept the default values
- enter a passphrase for the key pair you are creating, or leave blank

The `ssh-keygen` command will generate a public/private key pair.  The public key will be stored in the `.ssh/id_ecdsa.pub` file, and the private key will be stored in the `.ssh/id_ecdsa` file.

To view the public key, use one of these commands:

```PowerShell
Get-Content $env:USERPROFILE\.ssh\id_ecdsa_sk.pub
```

or, in a CMD prompt:

```Batchfile
type $env:USERPROFILE\.ssh\id_ecdsa_sk.pub
```

or, this Linux style command will be accepted by PowerShell:

```Bash
cat ~/.ssh/id_ecdsa_sk.pub
```

### Copy The Public Key To The Remote Server

The public key you just created, ~/.ssh/id_ecdsa_sk.pub, must be copied to the remote server. The current version of OpenSSH for Windows does not support the `ssh-copy-id` command. To copy the .pub key to the remote server, use:

> Note, before using one of the examples below, replace `same@server21` to the actual user and remote server you are using, *for example* `betty@108.23.54.237`.
    
```PowerShell
Get-Content $env:USERPROFILE\.ssh\id_ecdsa_sk.pub | ssh sam@server21 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
```

or, in a CMD prompt:

```Batchfile
type $env:USERPROFILE\.ssh\id_ecdsa_sk.pub | ssh sam@server21 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
```

or, this Linux style command will be accepted by PowerShell:

```Bash
cat ~/.ssh/id_ecdsa_sk.pub | ssh sam@server21 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
```

### Test The Connection

Now you can SSH to the remote server, and you should be able to use the key pair you just created, authenticated with FIDO2.

```PowerShell
ssh sam@server21
```
