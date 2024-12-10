* [Official GRUB2 documentation](https://www.gnu.org/software/grub/manual/grub/grub.html)
* [Dedoimedo GRUB2 tutorial](https://www.dedoimedo.com/computers/grub-2.html)
* [Grub2 menu that is maintenance free](https://unix.stackexchange.com/questions/673586/grub2-menu-that-is-maintenance-free) - when drives are changed around, UUIDs change during repartitioning, etc..

https://docs.fedoraproject.org/en-US/quick-docs/grub2-bootloader/#_enabling_serial_console_in_grub2

[grubby vs. grub2-mkconfig](https://www.reddit.com/r/linuxadmin/comments/xazart/differences_between_grubby_and_grub2mkconfig/)

What's the difference between writing to `/boot/grub2/grubenv` (via
`grub2-editenv`) and writing to `/boot/grub2/grub.cfg` (via `grub2-mkconfig -o
/boot/grub2/grub.cfg --update-bls-cmdline`)?

And what's with `--update-bls-cmdline`?
