```
> ipconfig
...
Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : ....
   IPv4 Address. . . . . . . . . . . : 192.168.0.125  <---***
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.0.1
...

Ethernet adapter vEthernet (WSL):

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : ....
   IPv4 Address. . . . . . . . . . . : 172.26.0.1  <---***
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . :
```

# Map network drive
* File explorer --> Computer --> Map Network Drive
```
Drive: U:
Folder: \\wsl$\Ubuntu
Finish
```
## Access from MobaXterm terminal
~$ ls -l /drives/u/

Ref: https://superuser.com/questions/1128634/how-to-access-mounted-network-drive-on-windows-linux-subsystem

# xwin apps
```
$ sudo apt install x11-apps
$ xclock
Error: Can't open display:

$ echo $DISPLAY

$ export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0
$ echo $DISPLAY
172.26.0.1:0
xin$ xclock
Error: Can't open display: 172.26.0.1:0
```

## MobaXterm
Got the same error
Cause: When Mobaxterm started, it started X server with a IP

```
 ➤ Your computer drives are accessible through the /drives path
 ➤ Your DISPLAY is set to 192.168.0.125:1.0
 ➤ When using SSH, your remote DISPLAY is automatically forwarded  
```
I didn't figure out a way to change that IP addess to 

## VcXsrv Windows X Server
Download: https://sourceforge.net/projects/vcxsrv/

Install

XLaunch
* allow public access in Allow app through Windows Firewall
* add -ac in under "Additional parameters for VcXsrv" in "Extra settings" step
* Save the configuration on Desktop

```
$ export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0
$ xclock --> works!
```

* save export ... to .bashrc

Ref: https://superuser.com/questions/1476086/error-cant-open-display-0

# ssh to WSL
sshd is not running on WSL-Ubuntu

https://superuser.com/questions/1123552/how-to-ssh-into-wsl

Didn't do much about this.

https://nickjanetakis.com/blog/using-wsl-and-mobaxterm-to-create-a-linux-dev-environment-on-windows

# VS Code with WSL -Remote
Remote - WSL runs commands and extensions directly in WSL so you don't have to worry about pathing issues, binary compatibility, or other cross-OS challenges. You're able to use VS Code in WSL just as you would from Windows.

* Start VS Code.
* Press F1, enter Remote-WSL: New Window, and hit enter.
* Use the File menu to open your folder.
* Terminal --> New Terminal

Ref: https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl


