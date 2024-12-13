## Nice for lessons

Reverse SSH shell for root access via workstation gives the nicest console
screen with colors, wraps, and whatnot. Also, tmux copy/paste history works
without the extra hop.

## In general
Organize into topics:
* commands, files, environment variables
* arguments and options for common tasks
* man/info/docs supporting the above

In RHEL:
* `dnf install bash-completion` and restart/relogin/resource environment
* `export EDITOR=/usr/bin/vim`

## Booting
How to identify whether we have a BIOS or UEFI system? Know how to install
GRUB on both.

* Determine devices.
* Determine if they have GRUB installed on them.
* Determine what kind of system they have - BIOS or UEFI.

For UEFI boots - does secure boot have to be off?

To test boot options, don't just edit the only one you have.
Add another option to the menu. Looking at you `console=ttyS0`.

Know common kernel boot options. For example:
```
crashkernel=1G-4G:192M,4G-64G:256M,64G-:512M resume=/dev/mapper/rhel-swap
rd.lvm.lv=rhel/root rd.lvm.lv=rhel/swap rhgb quiet console=ttyS0
```
`rhgb` Red Hat graphical boot
`rd.lvm.lv` stuff pertains to `dracut`: https://www.kernel.org/pub/linux/utils/boot/dracut/dracut.html#dracutcmdline7

Know common GRUB options.

https://www.redhat.com/en/blog/interrupt-linux-boot-process

## fstab columns
know um

## Manually configure a Red Hat repository
Strong hint from Sander that you gotta do this.
See if got old docs from former work.

## dnf & subscription-manager

Is there man doc on repo file format?
Memorize the simple yum.repos.d/repofile.repo format cuz generator utilities
forget gpgcheck:
```
[nicename]
name=NiceName
baseurl=file:///..
gpgcheck=0
```

## NetworkManager
* Probably know what all the permissions in `nmcli general permissions` mean.
* Probably know more about the role of `dbus`.
* Non-privileged users have permissions yanked if logqed in via SSH. How is
  this accomplished?

## nmcli
`nmcli dev` shows a `p2p-dev-wlp3s0` which I don't know what it is or where it
comes from. In general I want to know how nmcli overlaps with `ip` commands.
For example, stuff like:
```
ip -br addr show to "$(nmcli -g ip4.address con show <connection-name>)" | cut -d ' ' -f 1
```

## Networking
What is a link local address in the IPV6 context? See `ping6` usage that
requires a NIC name.

Probably do the lesson 11 lab.

Check out the LPI:
https://learning.lpi.org/en/learning-materials/102-500/109/

And the RHEL 9 networking guide:
https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/configuring_and_managing_networking/index

## ss
New netstat, get used to it.

## Set UID, Set GID, sticky bit
```
man chmod
-X, -t, -s
stat -c '%a %n' *
```
[[stat]]


## Netmasks

ELI5: https://www.reddit.com/r/explainlikeimfive/comments/1e50ril

* RFC 1519 "Classless Inter-Domain Routing"
* "supernet overlap"
* "route summarization"

Finally: Your network is what you can talk to directly. You need a gateway
(that's on your network) to talk outside your network. If you think someone is
on your network, you can send it to them directly. If you think someone isn't
on your network, then you send it to the gateway.

It's all about minimizing broadcasts and using local resources to communicate
locally.
