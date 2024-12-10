BIOS boots use:
```
linux
initrd
```

UEFI boots use:
```
linuxefi
initrdefi
```

## Catch the boot menu

Press `Shift` or `Esc` on startup.



## Runlevel 3

Catch the boot menu and append `3` to the end of the kernel boot options. Or..

Edit `/etc/default/grub`:
```
GRUB_CMDLINE_LINUX="... 3"
```

And update `grub.cfg`:
```
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```


## Un/hiding the menu

"`timeout` is the length of time the menu is displayed. When the menu is hidden
there is no timeout and booting is immediate." - "Make grub hidden again" by
Crazy Monkey at discussion.fedoraproject.org

`/etc/grub.d/12_menu_auto_hide` - see if SHIFT or ESC forces visibility

Turn hiding off:
```
sudo grub2-editenv - unset menu_auto_hide
```

Turn hiding on:
```
sudo grub2-editenv - set menu_auto_hide=1
```

Boot entry on new F41 installl:
```
load_video
set gfxpayload=keep
insmod gzip
linux ($root)/vimlinuz-6.11.4-301.fc41.x86_64
root=UUID=97ac068f-9d01-4a7b-bc8d-5e7f5927fa7b ro rootflags=subvol=root
nomodeset rhgb quiet
initrd ($root)/initramfs-6.11.4-301.fc41.x86_64.img $tuned_initrd
```
