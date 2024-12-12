
From `lspci`:
```
03:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43224
802.11a/b/g/n (rev 01)
        Subsystem: Apple Inc. AirPort Extreme
```

```
lspci -nnk | grep -i 'network\|ethernet' -A3

iw list
iwconfig

dmesg | grep iwl
lsusb
```
Can find harware info at https://linux-hardware.org/?id=pci:14e4-43ba:
```
# 0280 is for networking specifically?
lspci -nn | grep 0280   # search for pci.id like [14e4:43ba] online
```

```
find -L /sys/class/net -maxdepth 3 -name "uevent" -exec grep -iH "iwlwifi" {} \; 2> /dev/null
find -L /sys/class/net -maxdepth 3 -name "uevent" -exec grep -iH "iwlwifi" {} \; 2> /dev/null | awk -F / '{print $5}'
```


https://askubuntu.com/questions/1470530/finding-the-name-of-a-wireless-interface-from-kernel-module
finding drivers in play

https://discussion.fedoraproject.org/t/need-help-wi-fi-is-very-slow-or-limited-on-2011-macbook-air-blocking-updates-and-flatpak/108621
Suggests a different driver.

https://forums.fedoraforum.org/showthread.php?323563-MacBook-Air-slow-wifi&p=1832934#post1832934
Some assessment tips.

https://community.clearlinux.org/t/broadcom-bcm43224-wifi-slow/2668/4
Kernel module blacklisting.

https://superuser.com/questions/597805/linux-bcm43224-wifi-adapter-slows-down-a-couple-minutes-after-boot
rfkill lspci -nnk | grep -iA2 net

https://forum.endeavouros.com/t/broadcom-bcm43224-slow-speeds/3195
more blacklisting
