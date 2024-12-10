* https://qemu-project.gitlab.io/qemu/
* https://web.archive.org/web/20180104171638/http://nairobi-embedded.org/qemu_monitor_console.html
* [-bios vs. -kernel options](https://stackoverflow.com/questions/58420670/qemu-bios-vs-kernel-vs-device-loader-file)
* [QEMU ELI5 - Part 7, Networking](https://medium.com/@tunacici7/qemu-eli5-part-7-networking-ec49f8418826)
* https://mac.getutm.app/ - $10

Run without options, `qemu-system-x86_64` starts up an [iPXE](https://ipxe.org/cmd) prompt:

* `-nographic` : All command line. `Ctrl-a x` to exit.
* `-display curses` : As above, but apparently [works with SSH](https://stackoverflow.com/a/6752062).
* `-serial stdio -nographic` with guest GRUB to `console=ttyS0` then have host `tmux` log it

[QEMU and Linux kernel module cheat environment](https://github.com/cirosantilli/linux-kernel-module-cheat/tree/82872f9467852c2773e420e7cdc3f157da30199e#text-mode)

Tutorial:
* https://medium.com/@tunacici7/qemu-eli5-part-1-introduction-957ae2f48de5
* https://github.com/TunaCici/QEMU_Starter

From  https://github.com/TunaCici/QEMU_Starter:

> When launched with a display windows, QEMU offers some basic controls on the taskbar. Be sure to check that out as well.

- **Release mouse (Display only):** GNU/Linux & Windows: `CTRL + ALT + G`, macOS: `control + option + G`
- **Switch to guest (Display only):** GNU/Linux & Windows: `CTRL + ALT + 1`, macOS: `control + option + 1`
- **Switch to QEMU Monitor (Display only):** GNU/Linux & Windows: `CTRL + ALT + 2`, macOS: `control + option + 2`
- **Toggle between guest & QEMU Monitor (`-nographic` only):** All systems: `CTRL + A` then `C`
- **Terminate machine (`-nographic` only):** All systems: `CTRL + A` then `X`

> QEMU Monitor is an amazing feature that QEMU offers. It is an advanced topic that is targeted to developers. For this reasons, I won't be explaining it here. Maybe down the road I will... If you are really curious, check out the official documentation [QEMU Monitor](https://qemu-project.gitlab.io/qemu/system/monitor.html).

Snapshots, sockets, savevm, loadvm oh my..
https://superuser.com/questions/1768173/how-to-work-with-qemu-snapshots-savevm-in-a-way-that-is-predictable-like-virtual

`Ctrl-Alt-F1` and `Ctrl-Alt-F6` toggle `tmux` and GUI views. In `tmux`, use standard `Ctrl-b + n|p` to move between `tmux` windows.


CURRENT MISSION

Use [QEMU monitor](https://qemu-project.gitlab.io/qemu/system/monitor.html) commands (available at the `(qemu)` prompt) on the guest to enable networking such that the guest (currently in a `dracut:/# ` shell prompt)  can send information to the host.

* `info` 
* `info pci` 
* `info network` 
* `info qom-tree` 

What monitor commands show the QEMU options running the guest?

Some funky commands: `dumpdtb` `hostfwd_add` `hostfwd_remove` ``