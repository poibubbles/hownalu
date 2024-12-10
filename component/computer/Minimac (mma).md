## Issues

### Slow network

What worked: Returning the wifi connection to DCHP.

Following a couple of reboots after the installation, the network speed slowed
to a trickle. But it seemed fast enough just after the installation.

Tried the following from "17. Using NetworkManager to disable IPv6 for a
specific connection":
```
# nmcli connection modify TWRboathouse ipv6.method "disabled"
# nmcli connection up TWRboathouse
# cat /proc/sys/net/ipv6/conf/wlp3s0b1/disable_ipv6
```

And from https://discussion.fedoraproject.org/t/network-very-slow/73157/6
added to `/etc/sysctl.conf`:
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

Then `sysctl -p` and `cat /proc/sys/net/ipv6/conf/all/disable_ipv6` (confirm
response is `1`).


## Installation

* Installed Fedora 41 on 2024-12-10 on a Mac Mini from 2011 (?).
* Used the Fedora Media Writer for MacOS from
  https://fedoraproject.org/workstation/download to create a USB installer.
* Needed the right USB keyboard in the right slot to get the left `Alt` key to
  catch the MacOS boot device menu.
* Needed the right HDMI cable in the right TV to see anything.
* Needed to use the "Troubleshooting.." and basic graphical option to get a
  useful display to install. After installation..
* Wifi worked out of the box.
* Turned off power suspension from the GUI. I believe this is a GDM feature.
* Turned off boot menu's auto hide option.
* Set to boot into runlevel 3.
* Set SSH to start automatically.
* Set manual IPv4 address to 192.168.1.111/24 on wifi.
* Let IPv6 alone in default DHCP mode. This may have been an issue. See the
  Issues section.
