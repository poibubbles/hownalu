*YO* Append `console=ttyS0` to the kernel boot options.

Inspired by [Virtual Machines on MacOS With QEMU — Intel based](https://medium.com/code-uncomplicated/virtual-machines-on-macos-with-qemu-intel-based-351b28758617) (and the accompanying [Github repository](https://github.com/oliversavio/youtube-vid-code/tree/main/qemu-virtual-machines-macos)) by Oliver Mascarenhas.

* [[QEMU]] 
* [[GRUB]]
* [RHEL 9 boot options reference](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/interactively_installing_rhel_from_installation_media/custom-boot-options_rhel-installer#installation-source-boot-options_custom-boot-options)


## Make a floppy kickstart

So far, no love. See [[2024-12-04 Trouble with RHEL9 kickstart and text install]].

## Download an ISO installer

* Download ISOs from https://developers.redhat.com/products/rhel/getting-started.
* Create custom ISOs at https://console.redhat.com/insights/image-builder/imagewizard.


## Create the VM

For example:
```
qemu-img create -f qcow2 rhel.qcow2 8G
```
8G is probably enough to experiment with a minimal install. For a graphical
install (and for the Sander courses) 20G was used.


## Run the install in a terminal

For example:
```
qemu-system-x86_64 \
-machine type=q35,accel=hvf -cpu host -smp 2 -m 2G \
-vga none -nographic \
-drive file=rhel.qcow2,if=virtio \
-cdrom rhel-installer.iso -fda rhel-kickstart-floppy.img \
-boot menu=on,splash-time=6000
```

Then add `console=ttyS0` to the kernel options in the appropriate GRUB menu
entry to see console logging during boot and get a nice text-based
installation wizard.

Note: So far these options worked the best to get a text-based install working
in the terminal:
```
-vga none -nographic -boot menu=on,splash-time=6000
```


## Run RHEL

For example:
```
qemu-system-x86_64 \
-machine type=q35,accel=hvf -cpu host -smp 2 -m 2G \
-vga none -nographic \
-drive file=rhel.qcow2,if=virtio -usb -device usb-tablet \
-net user,hostfwd=tcp::10022-:22 -net nic \
-boot menu=on,splash-time=6000
```

## Installation decisions

* Used 8G total; 3.66 GiB was required for system data according to partitioning option.
* Did not connect to Red Hat Insights.
* Subscribed in Simple Content Access mode.
* Chose the minimal install. The default Server with GUI would take more than 5G.
* Used automatic configuration of disk storage.
* Disabled KDUMP due to memory needs.
* No security profile was selected.
* Created root with password and SSH login.
* Created ``ansible`` user.


## Installation tips

* Have RedHat developer credentials for installation registration.
* (If using the graphical installer..)Use QEMU's menu to select ``View > Zoom
  to fit`` and then resize the VM window to be able to see buttons and text
  fields.
* Achieve copy/paste ambivalence. Or look up a bunch of Spice issues,
  compiles, workarounds. Just live without it for now.
* Note network connection as: ``enp0s2``


## TODO

* Try `console=tty0 console=ttyS0,9600n8 s`. See the [Remote Serial Console HOWTO](https://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/configure-kernel-grub.html).
* Try `qemu -curses` with [[SSH]].
* Try `qemu -serial stdio` and [[GRUB]] with `console=ttyS0`. See [How to start qemu directly in the console](https://serverfault.com/questions/471719/how-to-start-qemu-directly-in-the-console-not-in-curses-or-sdl)
* Try `-display none -monitor stdio` as an alternative to `-nographic`. See [How to use qemu with "-nographic" and "-monitor stdio" at the same time?](https://stackoverflow.com/questions/77715457)
* See https://fragdev.com/blog/using-qemu-inside-terminal-serial-output
* See https://fadeevab.com/how-to-setup-qemu-output-to-console-and-automate-using-shell-script/


## Post-installation work

* `dnf install vim-enhanced tmux rsync`
* `tmux.conf`


## STIGs

For fun, try manually applying [STIGs during
installation](https://www.reddit.com/r/redhat/comments/1g5yi6z/rhel_9_red_hat_stigs_applied_via_custom_iso/).

Red Hat provides an OpenSCAP profile for DISA STIGs at
(`xccdf_org.ssgproject.content_profile_stig`) at the
[ImageBuilder](https://console.redhat.com/insights/image-builder/imagewizard).

Kernel arguments:

```
audit_backlog_limit=8192 audit=1 slub_debug=P page_poison=1 vsyscall=none pti=on
```

Disabled services:

```
kdump autofs debug-shell
```

Enabled services:

```
auditd usbguard sshd chronyd fapolicyd firewalld systemd-journald rsyslog pcscd
```


## Issues

#### Copy-paste
Apparently the issue is that `qemu` needs to be compiled with Spice, which the
Homebrew version isn't. Might have to do it yourself..
https://johnsiu.com/blog/macos-qemu-spice/

#### Clocksource log spam
See  [[2024-12-03 tsc hpet acpi_pm clocksource issues on RedHat 9.5]]
