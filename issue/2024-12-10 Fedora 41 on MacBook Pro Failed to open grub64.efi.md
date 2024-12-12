
## The error

The error on startup was:
```
Failed to open \EFI\redhat\grub64.efi - Not Found
Failed to load image : Not Found
start_image() returned Not Found, falling back to default loader
Failed to open \EFI\redhat\grub64.efi - Not Found
Failed to load image : Not Found
start_image() returned Not Found
```
..and then it just hung there. Note that the error included `\EFI\redhat`..

## Rebooting issues

After a couple reboots, it wouldn't power up at all, until I held
`Shift-Ctrl-Option + Power` for about 15 seconds, which at resulted in the
error above.

## Troubleshooting environment

Powered on (if it will) as normal holding the left `Option` key (`Alt` if you
have an external keyboard) to get the Macbook boot screen. Then used the
Fedora 41 installer environment (pretty much a full desktop) to troubleshoot.

## Orientation

Look for devices and the `/EFI/redhat/` directory.
```
lsblk
mount | grep `/dev/sd`      # /dev/sdb is the installer
mount /dev/sda1 /mnt/sda1   # after looking around at /dev/sd* partitions
```

Again, this is a Fedora install.
```
ls -d sda1/EFI/* 
sda1/EFI/BOOT  sda1/EFI/fedora  sda1/EFI/redhat

ls sda1/EFI/fedora/grub

efibootmgr
Boot0000* Fedora  ...
Boot0001* redhat  ...
```

### Gonna do a reinstall to check efibootmgr

The installer's automatic partitioning results in:
```
/boot/efi   sda1   EFI system partition
/boot       sda2   ext4
fedora      sda3   btrfs
```

After installation, winds up there is a `redhat` entry. Whoops.
```
efibootmgr
Boot0000* Fedora  ...
Boot0001* redhat  ...
```

What about the EFI partition `/boot/efi/` on a fresh install? **No redhat.**
```
ls -d /boot/efi/EFI/*
/boot/efi/EFI/BOOT /boot/efi/EFI/fedora
```

```
parted /dev/sda print
parted /dev/sda1 print
```


## Possibilities

### Reinstalling grub2-efi-* and shim-*

Basically, try `dnf reinstall grub2-efi-* shim-*` for whatever `x64` and
`ia32` and whatnot exists.

Shows files installed to `/boot/efi/EFI/BOOT`, `/boot/efi/EFI/fedora`, and
`/etc/dnf/protected.d/shim.conf`:
```
rpm -qa | grep shim
shim-x64-15.8-3.x86_64
shim-ia32-15.8-3.x86_64
rpm -ql shim-x64
rpm -ql shim-ia32
```





## Failures

### Killing the redhat entry with efibootmgr
I thought I could just delete the `redhat` entry. After rebooting the screen
remained blank and soft chimes repeated every few seconds.
```
dnf reinstall grub2-efi shim
efibootmgr -b 0001 -B  # delete redhat
reboot
```

Hopefully to make things easier to check..
```
grub2-editenv /mnt/sda2/grub2/grubenv unset menu_auto_hide
```


