
# Windows - How To Update System Path From Command Line

Example... adding \OpenSSH to the path

```PowerShell
[Environment]::SetEnvironmentVariable("Path", [Environment]::GetEnvironmentVariable("Path",[System.EnvironmentVariableTarget]::Machine) + ';' + ${Env:ProgramFiles} + '\OpenSSH', [System.EnvironmentVariableTarget]::Machine)
```


# SSH post - update now Windows 11 2022H2 has shipped



## Desktop, Win 11 prior to 22H2
OpenSSH_for_Windows_8.1p1, LibreSSL 3.0.2


## Laptop

Was
OpenSSH_for_Windows_8.9p1, LibreSSL 3.4.3

Removed via winget then installed through windows Optional Features.
Now:

OpenSSH_for_Windows_8.6p1, LibreSSL 3.4.3



# SSH From Windows With X11 Graphical Apps

PETE - you are getting this warning, investigate it....
Warning: No xauth data; using fake authentication data for X11 forwarding.


## Install an X11 Server on Windows

### Paid options



x410
https://x410.dev/

### Free options
VcXsrv
https://sourceforge.net/projects/vcxsrv/


```PowerShell
winget install VcXsrv
```

## Connect to X11 Server
run the X11 server
Windows Firewall
set DISPLAY environment variable

https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.2




```PowerShell
$Env:DISPLAY="127.0.0.1:0.0"
```
You can see the value of $env:DISPLAY or any other environment variable with the command:

```PowerShell
$Env:DISPLAY
```

ssh to remote device
ssh -Y

## On remote machine, call the GUI program
vlc
thonny

or call the gui app directly on the ssh command




# Useful awk scripts

## Remove duplicate lines in a file
https://iridakos.com/programming/2019/05/16/remove-duplicate-lines-preserving-order-linux
```bash
awk '!/./ || !seen[$0]++' your_file > deduplicated_file
```

# tmux

project repository
https://github.com/tmux/tmux/wiki

install with

```text
sudo apt install tmux
```

Starting tmux

```text
tmux
tmux attach
```

While in tmux

```text
```

# VSCode.dev
Here's an example of how to open vscode.dev on a specific GitHub page: https://vscode.dev/github.com/aymericdamien/TensorFlow-Examples

