`chvt <2-6>` where `2` is typically the GUI and `3-6` are the virtual text terminals.

Ever wonder how to stop the cursor from blinking in raw `getty` sessions? Or all over the place?

See  https://unix.stackexchange.com/q/3759 for lots of possible solutions.

This worked for all users when executed by root on RHEL9:

	echo 0 > /sys/class/graphics/fbcon/cursor_blink