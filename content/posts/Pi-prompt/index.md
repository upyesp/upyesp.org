---
title: "Raspberry Pi Pretty Prompt, With... Oh My Posh, LSD & CPUfetch / Neofetch"
description: Give your Raspberry Pi's command-line a boost by adding Oh My Posh and and a few other neat utilities.
date: 2022-05-08T15:00:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [RaspberryPi, Terminal, Bash, WSL]
categories: [Linux]
---

Give your Raspberry Pi's command-line a boost by adding [Oh My Posh](https://ohmyposh.dev/) and add a few other neat utilities.  Before starting, make sure your Pi is running a **64bit operating system**, such as [Raspberry Pi OS](https://www.raspberrypi.com/software/), [Ubuntu 22.04 LTS Desktop or Server](https://ubuntu.com/download/raspberry-pi) and [Manjaro 22.04](https://manjaro.org/download/#ARM).

<!--more-->

![Screenshot of a terminal running on a Raspberry Pi. The content is enhanced from that of a standard Raspberry Pi terminal, with added information and colour.](/images/pipromptprettycpufetch.png "Oh My Posh on a Raspberry Pi")

## First, Set The Terminal Emulator To Use A Suitable Font 

For these enhancements to display correctly you'll need to install a font that includes graphical characters, known as "glyphs". An excellent source of such fonts is https://www.nerdfonts.com/.  Have a browse of the fonts available and decide which you want to use, hold off installing one just now.

### Where To Install The Font

When using the Pi's command-line, you're working in a terminal emulator.  It is the terminal emulator that will need to use the new font.

#### Using SSH To Connect To A Headless Raspberry Pi?
If you're connecting to your Pi via `SSH`, then the terminal emulator is running on the device you are connecting from, such as a desktop or laptop.

So if you're using `SSH`, this is where you'll need to install the font, not on the Pi itself.  You won't need to install a new font on the Pi.  Just install it on your desktop/laptop.  If you already have a suitable font installed (maybe you're already using *Oh My Posh* on that device), jump to [Setting Up The Pi](#pisetup).

The device you are connecting from could be running Windows, MacOS or Linux, refer to instructions for that OS. 

![Screenshot of Windows Terminal, showing the settings screen. The setting for Font is displayed and has been highlighted. It is set to font "Hack NF"](/images/windows-terminal-font.png "Windows Terminal Font Setting")

1. Download your preferred font from https://www.nerdfonts.com/.
1. Install the font on the desktop/laptop your are connecting from.
    > Tip: When installing the font, follow the method to install the font *system-wide / for all users*, not just a single user.
1. Change the settings in your terminal emulator to use the font you just installed.

#### Standalone Raspberry Pi (With Keyboard/Mouse/Monitor Attached)

If you are working with your Pi directly, install the new font on the Pi.  In the future, if you also `SSH` to the Pi from another device,  install the new font on that device, as per above.

Example, installing the font called "Hack Nerd Font", using the Pi's command-line:

```Bash
cd
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Hack.zip
mkdir -p .local/share/fonts
unzip Hack.zip -d .local/share/fonts
cd .local/share/fonts
rm *Windows*
fc-cache -fv
```

![Screenshot of LXTerminal, showing the settings screen. The setting for Font is displayed and has been highlighted. It is set to font "Hack Mono Regular"](/images/Raspberry-Pi-Desktop-LXTerminal-Font.png "Raspberry Pi LXTerminal Font Setting")

1. From the Raspberry Pi, download your preferred font from https://www.nerdfonts.com/.
1. Install the font on the Pi.
    > Tip: When installing the font, install the font system-wide, for all users (not just a single user).
1. Change the settings in LXTerminal to use the font you just installed.



## Setting Up The Pi  {#pisetup}

Log in to your Raspberry Pi to install the software below.

### Oh My Posh

> For the latest documentation, refer to the Oh My Posh [website](https://ohmyposh.dev/docs/linux). Remember to change name of the binary being downloaded to that for ARM 64. 

Example, download *Oh My Posh*, choosing the binary for ARM based linux devices:

```Bash
sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-arm64 -O /usr/local/bin/oh-my-posh
sudo chmod +x /usr/local/bin/oh-my-posh
```

Download the latest collection of prompt themes:

```Bash
mkdir ~/.poshthemes
wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/themes.zip -O ~/.poshthemes/themes.zip
unzip ~/.poshthemes/themes.zip -d ~/.poshthemes
chmod u+rw ~/.poshthemes/*.json
rm ~/.poshthemes/themes.zip
```

> Tip: If you have previously made your own custom theme, copy it to your Pi using `scp`. Here's an example command, run from a Windows machine: `scp 'C:\Users\fred\Desktop\Oh My Posh custom theme\upyesp.omp.json' fred@192.168.10.174:~/.poshthemes/` (you'll need to change the Windows folder to yours, along with the Pi's user name and IP address).

Change the Pi's `.bashrc` to invoke Oh My Posh and select the theme you want to use:

```Bash
sudo nano ~/.bashrc
```

Add this line to the end of `.bashrc` (change the theme to the one you want to use):

```Bash
eval "$(oh-my-posh init bash --config ~/.poshthemes/powerlevel10k_modern.omp.json)"
```
Exit `nano` by pressing <kbd>Ctrl</kbd> + <kbd>x</kbd> and press <kbd>y</kbd> to save changes.

Restart `Bash` to see the new prompt, with `exec bash`.

### LSD (LSDeluxe)

> For the latest documentation, refer to the LSD [project repository](https://github.com/Peltoche/lsd). Remember to change name of the binary being downloaded to that for ARM 64. 

Example, download and install *LSD (LSDeluxe)*, choosing the binary for ARM based linux devices:

```Bash
wget https://github.com/Peltoche/lsd/releases/latest/download/lsd_0.21.0_arm64.deb
sudo dpkg -i lsd_0.21.0_arm64.deb
rm lsd_0.21.0_arm64.deb
```

Change the Pi's `.bashrc`, set an Alias to use LSD in place of `ls`:

```Bash
sudo nano ~/.bashrc
```

Add this line to the end of `.bashrc` to set up the Alias:

```Bash
alias ls='lsd'
```

Exit `nano` by pressing <kbd>Ctrl</kbd> + <kbd>x</kbd> and press <kbd>y</kbd> to save changes.

Restart `Bash`, with `exec bash`. Then use `ls` as normal, for example `ls -al`.

### Neofetch, Command-line System Information

> For the latest documentation, refer to Neofetch [project repository](https://github.com/dylanaraps/neofetch).  Neofetch is highly configurable, for more information visit the [wiki](https://github.com/dylanaraps/neofetch/wiki/Customizing-Info).

![Screenshot of a terminal running on a Raspberry Pi. The content is enhanced from that of a standard Raspberry Pi terminal, with added information and colour.](/images/pipromptpretty.png "Oh My Posh on a Raspberry Pi")

To install Neofetch:

```Bash
sudo apt update
sudo apt install neofetch
```

Change the Pi's `.bashrc`, add a line to call Neofetch:

```Bash
sudo nano ~/.bashrc
```

Add this line to the end of `.bashrc` to call Neofetch:

```Bash
neofetch
```

Exit `nano` by pressing <kbd>Ctrl</kbd> + <kbd>x</kbd> and press <kbd>y</kbd> to save changes.

Restart `Bash`, with `exec bash`.

### CPUfetch, System CPU Information

> For the latest documentation, refer to CPUfetch [project repository](https://github.com/Dr-Noob/cpufetch).  CPUfetch is similar to Neofetch, but is focused on providing detailed information about the system's CPU(s).

To install cpufetch:

```Bash
# for ARM - Raspberry Pi
sudo wget -O /usr/local/bin/cpufetch https://github.com/Dr-Noob/cpufetch/releases/latest/download/cpufetch_arm_linux

# set executable permission
sudo chmod a+x /usr/local/bin/cpufetch
```

> Note, change your .bashrc to call cpufetch as an alternative to Neofetch, you wouldn't normally call both Neofetch and cpufetch.
 
Change the Pi's `.bashrc`, add a line to call cpufetch:

```Bash
sudo nano ~/.bashrc
```

Add this line to the end of `.bashrc` to call cpufetch:

```Bash
cpufetch
```

Exit `nano` by pressing <kbd>Ctrl</kbd> + <kbd>x</kbd> and press <kbd>y</kbd> to save changes.

Restart `Bash`, with `exec bash`.
