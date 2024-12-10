Usability crawled, eventually saw 200-300+% CPU usage by `kernel_task`.

The culprit was probably an `rsync` process copying files to two SD cards, both connected to a single charging+expansion port and causing a heating sensor to complain.

See https://apple.stackexchange.com/q/363337.

By stopping the `rsync` process and then unmounting the SD cards, `kernel_task` went down to 3-6%.

By moving one of the SD cards from the expansion port and plugging it directly in to the computer (so that the copying between SD cards wasn't going back and forth through the same expansion port) and restarting the `rsync`, `kernel_task` hovered at about 10% and two `rsync` processes hovered around 25% each.

`kernel_task` is PID 0, so restarting it isn't really an option.