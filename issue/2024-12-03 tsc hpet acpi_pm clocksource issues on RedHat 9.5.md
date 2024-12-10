
## Move along, apparently nothing to see here..

As of 2024-12-03, https://access.redhat.com/solutions/6995981 reports on
2024-06-13: *These messages are just informational. It is not even a warning.
It just notes that the read-back delay from hpet is too high to make it useful
for checking TSC reliability. So as long as it doesn't cause tsc fallback to
hpet, you can ignore the messages.*

**NOTABLY** The install of the full GUI + Netowrking version of RHEL9.5
*installed using UTM* did not have the clocksource problem at all.

## Fix for RHEL9.3+

To prevent all the warnings in `/var/log/messages`:

* Edit `/etc/default/grub`.
* Add `tsc=nowatchdog` to `GRUB_CMDLINE_LINUX` options.
* Run `grub2-mkconfig -o /boot/grub2/grub.cfg --update-bls-cmdline` in
  RHEL9.3+. See https://access.redhat.com/solutions/6668601 for details.

This did not work:

* Adding `clocksource=acpi_pm` to `GRUB_CMDLINE_LINUX` options.
* Adding `clocksource=hpet` to `GRUB_CMDLINE_LINUX` options.
## Problem

After installation using ``rhel-9.5-x86_64-boot.iso``, startup (and login
prompt) got inundated with the following in `/var/log/messages`:
```
[954.817701]
clocksource: wd-tsc-wd read-back delay of 215000ns, clock-skew test skipped!
[955.312808]
clocksource: timekeeping watchdog on CPU0: hpet wd-wd read-back delay of 61000ns
```

Later in the same log:
```
[46668.574749] clocksource: Not enough CPUs to check clocksource 'tsc'.
[46668.574854] clocksource: Switched to clocksource hpet
```
	
This was *not* resolved by simply adding ``-smp 2`` to the ``qemu`` launcher.

Clocksources can be checked and set dynamically via:
```
/sys/devices/system/clocksource/clocksource0/available_clocksource
/sys/devices/system/clocksource/clocksource0/current_clocksource echo tsc > !$
```

## Tips

* Check running kernel options after reboot: `cat /proc/cmdline`.
* Set kernel options for RHEL9:  https://access.redhat.com/solutions/6668601.
* Check `/var/log/messages` after changing
  `/sys/devices/system/clocksource/clocksource0/current_clocksource`
  dynamically.


## See also

* https://access.redhat.com/solutions/434883
* https://access.redhat.com/solutions/6989115
* https://access.redhat.com/solutions/18627
* https://bbs.archlinux.org/viewtopic.php?id=278494
* https://letmegooglethat.com/?q=tsc+vs+hpet

From RHEL 7 for Real Time "Chapter 15: Timestamping": *Reading from the TSC
means reading a register from the processor. Reading from the HPET clock means
reading a memory area. Reading from the TSC is faster, which provides a
significant performance advantage when timestamping hundreds of thousands of
messages per second.*
