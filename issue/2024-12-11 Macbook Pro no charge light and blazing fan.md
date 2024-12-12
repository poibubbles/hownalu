## What worked

What worked: SMC reset. See https://support.apple.com/en-us/102605. Turned
computer off. Held Left Shift + Left Ctrl + Left Option + Power for 10
(actually a bit more) seconds. Then powered on. Charging light came on and fan
was quiet. And all the battery commands worked.

## The problem

After the first installation of Fedora 41, I screwed up something in the EFI,
like maybe telling it to boot first from the `redhat` option which didn't have
its expect boot loader. But before that it worked fine.

After the second installation of Fedora 41, the fan started blazing and I
couldn't get the charging cable LED to light up. It didn't seem to be a Fedora
issue as the blazing fan and missing charge light were present at the Mac boot
screen as well.

No battery information showed up in Fedora.

* No battery indicator on the deskop.
* No output for `acpi -b`.
* No output for `inxi -B`.
* No `/sys/class/power_supply/BAT*`.

Issues might be:

* Bad outlet - tried many.
* Bad power adapter or charging cable.
* SMC (System Management Controller) might need a reset.
  * https://support.apple.com/en-us/102605
* Battery might have to drain to save life. Most interesting.
