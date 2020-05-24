# Live USB
* Has to create from a Desktop ISO.
* [The latest for Lubuntu is 16.04.03 LTS](https://lubuntu.net/downloads/)

# Boot
* Bootloader has to be installed on /dev/sda not /dev/sda1
* Repair a boot loader with a Live Ubuntu of the same version 

Boot with Live Ubuntu, assume the system is installed on /dev/sda1

```method 1
sudo apt-add-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair
```
```method 2
sudo su
mkdir /mnt/uu
mount /dev/sda1 /mnt/uu
grub-install --boot-directory=/mnt/uu/boot /dev/sda
```
Ref: https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/

# Grub
I used a live Lubuntu 16.04LTS media rescured a LUbuntu 18.04LTS with method 2 described above. The system was able to boot, but only into a grub mode.
```
grub> ls (hd0,1)/
grub> linux (hd0,1)/vmlinuz root=/dev/sda1
grub> initrd (hd0,1)/initrd.img
grub> boot
```
Ref: 
* https://askubuntu.com/questions/929833/how-do-i-boot-my-pc-from-grub

* https://www.gnu.org/software/grub/manual/grub/html_node/Installing-GRUB-using-grub_002dinstall.html

* https://www.pcsuggest.com/grub-error-no-such-device/

Boot with installation media into Rescue Mode - Rescue operations

  * Execute a shell in /dev/sda1
  
  * Execute a shell in the installer environment
  
  * Choose a different root file system
  
  * Reboot the system

Choose "Execute a shell in /dev/sda1"

```
# grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
```

# Fix a Lubuntu installed on USB

It could not boot because I put boot loader on /dev/sdc1 instead of /dev/sdc at installation process.

1. Boot with installation media into Rescue Mode

2. Plug USB with Lubuntu installed

3. Choose "Choose a different root file system"

4. Select from "Device to user as root file system:" - /dev/sdc1

5. Choose "Execute a shell in /dev/sdc1"

Assume that GRUB should put images under /boot directory:

```
# grub-install /dev/sdc
Installing for i386-pc platform.
Installation finished. No error reported.
```

After I ran `grub-install` for a Lubuntu 18.04 LTS with a Lubuntu 16.04.3 LTS live USB, the system can boot into grub environment. Ran `grub-install` again with the right version didn't fix it.
```
sudo grub-install /dev/sda && sudo update-grub && sudo update-initramfs -u
Installing for i386-pc platform.
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-20-generic
Found initrd image: /boot/initrd.img-4.15.0-20-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 18.04 LTS (18.04) on /dev/sda1
done
update-initramfs: Generating /boot/initrd.img-4.15.0-20-generic
```
After this, reboot into grub rescue mode - Error: no such device: xxxxx-xxxx-xxxx-xxxx-xxxxx. This is probable caused by the last command "update-initramfs" since I repeated the above steps without that command and the boot was fixed.

```
extra notes: Boot with installation media into Rescue mode
Choose `/dev/sda1` from "Device to use as root file system"

Execute a shell in /dev/sda1 - you will be given a shell with /dev/sda1 mounted on "/"

> blkid
/dev/sdb1: UUID="2018-04-26-18-20-57-00" LABEL="LUBUNTU 18.04 LTS i386" TYPE="iso9660" PARTUUID="756db-49-01"
/dev/sda1: UUID="c5b0028c-1b81-455d-8638-4868e0ef64a8" TYPE="ext4" PARTUUID="f1d796ce-01"
```
