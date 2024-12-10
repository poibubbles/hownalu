## Getting to the Mac Mini boot prompt

Apparently different keyboards and USB ports matter.

Ultimately success depended on some combination of:

* ..using the right USB keyboard. One of Elias' worked. My Corsair didn't.
* ..plugging the keyboard into the right port. The keyboard plugged into the
  outer port worked. Maybe another one could've worked, but who cares. See
  https://apple.stackexchange.com/questions/87349 for inspiration.
* ..pressing the left `Alt` key at the startup chime

..that allowed me to use a USB mouse to select the Fedora 41 live USB
installer.


## Fedora 41

### What's working best

At the GRUB prompt, select `Troubleshooting..` and then run the basic graphic
mode.

Selected:

* Automatic partitioning of the 298.1 GiB ATA Hitachi HTS54503
  5000cca673ce3b3b.
* "Free up space by removing or shrinking existing partitions" (..which I
  think means LVM?)

It's running fine with what's apparently on the USB. I thought an earlier
install with this same USB (not in troubleshooting mode) did a network
install.

### What didn't work

Fedora 41 USB installer, when booted normally, wound up with a pink background
and a mouse cursor that would occasionally indicate that it was over a button
or text field or something clickable - but no windows appeared. It was just a
pink background and cursor. Pressing `Enter` over interesting locations (like
over phantom buttons) resulted in some spinny icons but nothing else was
visible.

Tried again, editing the kernel boot options, removing `rhgb` and adding
`text`. From:
```
setparams 'Start Fedora-Workstation-Live 41'

linuxefi /images/pxeboot/vmlinuz root=live:CDLABEL=Fedora-US-Live-41-1-1
rd.live.image quiet rhgb
initrdefi /images/pxeboot/initrd.img
```

..to:
```
setparams 'Start Fedora-Workstation-Live 41'

linuxefi /images/pxeboot/vmlinuz root=live:CDLABEL=Fedora-US-Live-41-1-1
rd.live.image quiet text
initrdefi /images/pxeboot/initrd.img
```

Started the boot with F10 which resulted in nice `systemctl` startup info
..also against a windowless, pink background, with a nice cursor.

### Try also..

* `inst.text console=ttys0` per F36 install guide's kernel options - **NOPE**
  striped pink background.
* `rhgb quiet 3` for runlevel 3 - didn't try.
* `single` user mode - didn't try.


## RHEL9.4

RHEL9.4 USB installer failed with:
```
Fatal glibc error: CPU does not support x86-64-v2
Kernel panic - not syncing: Attempted to kill init! exitcode=0x00007f00
```
