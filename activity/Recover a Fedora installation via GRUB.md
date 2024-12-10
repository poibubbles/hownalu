At the GRUB prompt `grub>`:

	set pager=1
	ls
	
Step through the devices to see if you can see anything.

	ls (hd1,gpt2)   # shows filesystem type (if recognized)
	ls (hd1,gpt2)/  # shows files (if recognized)

*Gave up at this point trying to work with the partitions found on the MacBook and decided to try a live USB installer. Found the Fedora Media Writer installation at (hd0).*

	ls (hd0)/
	cat (hd0)/boot/grub2/grub.cfg

Where you want to go:

	set prefix=(hd0)/boot/grub2
	set root=(hd0)
	insmod normal
	normal
	insmod linux  <- Here's where a GRUB menu appeared!

The following is an example of what I expected to have to do:

	linux /boot/vmlinuz-1.13.0-10-generic root=/dev/sda1
	initrd /boot/initrd.img-1.13.0-10-generic
	boot