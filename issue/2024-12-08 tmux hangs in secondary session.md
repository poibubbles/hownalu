Accessing a remote tmux session via SSH in a local tmux window, the following
command froze the remote tmux session until the command completed:
```
# nmcli con up <connection name>
```

Redirecting outputs didn't help:
```
# nmcli con up <connection name> 1>/dev/null
# nmcli con up <connection name> 2>/dev/null
```

Redirections and Ctrl-C didn't work according to:
https://stackoverflow.com/questions/7408068/tmux-hangs-and-do-not-load-and-do-not-respond-to-any-option-command
