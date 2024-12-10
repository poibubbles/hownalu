So far it's been a failure. At most, it seemed as though a floppy kickstarter did cause the installer to use the `Pacific/Honolulu` timezone but it failed to create users and make software selections.

See:
* [Automatically installing RHEL (9)](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/automatically_installing_rhel)
* [13.2. Sharing the installation files on a local volume for automatic loading](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/automatically_installing_rhel/semi-automated-installations-making-kickstart-files-available-to-the-rhel-installer_rhel-installer#making-a-kickstart-file-available-on-a-local-volume-for-automatic-loading_semi-automated-installations-making-kickstart-files-available-to-the-rhel-installer) 
* [Appendix B. Kickstart commands and options reference](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/automatically_installing_rhel/kickstart-commands-and-options-reference_rhel-installer#cmdline_kickstart-commands-for-installation-program-configuration-and-flow-control)
* [Red Hat's online kickstart creator](https://access.redhat.com/labs/kickstartconfig/)
* [Red Hat's tmux installer windows](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/interactively_installing_rhel_from_installation_media/consoles-logging-during-install_rhel-installer#consoles-logging-during-install_rhel-installer)

Leftovers:
* It's not clear if QEMU is recognizing the floppy device (using `-fda`).
* Can we  get `/run/initramfs/rdsosreport.txt` from the `dracut` shell? We have at least `ip` and `curl` available to send it elsewhere.
* Maybe `netdev_add` in the `qemu` shell can help with networking.
* We received an `inst.stage2`  - does it need to be pointed somewhere else?
* Do our QEMU VM options or GRUB boot options need [volume names](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/automatically_installing_rhel/starting-kickstart-installations_rhel-installer#starting-a-kickstart-installation-automatically-using-a-local-volume_starting-kickstart-installations )?

FYI:
* kernel boot options `console=ttyS0 inst.cmdline` needs a kickstart

## Kickstart creation

Making a kickstart floppy according to https://fedoraproject.org/wiki/Make_QEMU_image_with_kickstart:
```
dd if=/dev/zero of=rhel-9.5-floppy.img bs=1440K count=1
/sbin/mkfs -F -t ext2 rhel-9.5-floppy.img
mkdir -p tmp-floppy
sudo mount -o loop rhel-9.5-floppy.img tmp-floppy
cp -p ks.cfg tmp-floppy/
sudo umount tmp-floppy
```

Get the UUID and path to the kickstarter from the mounted floppy image:
```
mount -o loop rhel-floppy.img ./floppy
find ./floppy -name ks.cfg  # confirm the kickstarter
lsblk -l -p -o name,size,type,mountpoint,uuid  # note UUID
```
## Kernel boot options

Because MacOS doesn't run with `mkfs` and because `hdiutil create` was giving attitude, I just tried making the floppy image on the Red Hat VM. 

Added console output to the kernel boot options:
```
console=ttyS0
```

Then tried adding the location of the kickstarter using one or the other of these kernel boot options (I'm not clear if the slash should or shouldn't be there):
```
inst.ks=hd:UUID=94348681-fbcf-4f84-8655-9a27335e2f06:/ks.cfg
inst.ks=hd:UUID=94348681-fbcf-4f84-8655-9a27335e2f06:ks.cfg
```

Note that the `inst.ks=hd:UUID...` above is apparently preferable to `ks=floppy`.

Also tried with:
```
inst.text
```
..alone, no arguements needed.

And then started booting.


## Errors and dracut

Received the following error after reaching the "Basic System":
```
[  OK  ] Reached target Basic System.

It seems that the boot has failed. Possible causes include
missing inst.stage2 or inst.repo boot parameters on the
kernel cmdline. Please verify that you have specified
inst.stage2 or inst.repo.
Please also note that the 'inst.' prefix is now mandatory.
```

`Ctrl-c` at this point drops into:
```
Starting Dracut Emergency Shell...
Generating "/run/initramfs/rdsosreport.txt"
Entering emergency mode. Exit the shell to continue.
Type "journalctl" to view system logs.
You might want to save "/run/initramfs/rdsosreport.txt" to a USB
stick or /boot after mounting them and attach it to a bug report.

dracut:/#
```

Apparently `inst.stage2` was set:
```
dracut:/# dmesg | grep stage2
# ..inst.stage2=hd:LABEL=RHEL-9-5-0-BaseOS-x86_64..
```

And then it was time for a break.