`~/.bash_history`

`HISTSIZE` and `HISTFILESIZE` - later in the demo he uses `HIST_FILE_SIZE`.

`history -w` syncs in-memory history to file.

`history -c` clears history - use `-w` first.

`history -d N` removes line N of history.

Repeating commands from history:

* up arrow
* `Ctrl-r`
* `!a` repeats last command starting with `a`
* `!N` repeats command at `N`