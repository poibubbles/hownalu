Universal Extensible Firmware Interface

Maybe the OS needs to be booted in UEFI mode. Not sure if this is the default
or built-in for RHEL and Fedora.

CSM is backwards compatibility for old BIOS.


`grub2-install` should ensure `/boot/eft/EFI/fedora/grubx64.efi`.

## 

## Booting directly from UEFI

From "Installing efibootmgr on Linux" by Ethannij on YouTube

Given:
```
lsblk
sr0      rom
sda     disk  rom
|-sda1  part  /boot
\-sda2  part  /
```

Use a kernel to boot.. (maybe forward slashes? backslashes were used in the
video):
```
mkdir -p /boot/efi/boot
cp /boot/vmlinuz-5.10.0-rc2+ /boot/efi/boot/bootx64.efi
# -c [create] [at device] -d /dev/sda [at partition] -p 1 -l [load]
efibootmgr -c -d /dev/sda -p 1 -L "MyLabel" -l "\efi\boot\bootx64.efi"

# Or maybe..
efibootmgr -c -d /dev/sda -p 1 -L "MyLabel" -l "\efi\boot\bootx64.efi"
  -u "initrd=\initramfs-5.9.1.img" root=/dev/sda2
  rootflags=subvol=/gentoo
```

Only after adding kernel boot options..
```
reboot
```
