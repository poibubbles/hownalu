To switch from GUI to CLI: systemctl isolate multi-user.target

To switch from CLI to GUI: systemctl isolate graphical.target

To set the CLI as a default runlevel (target in systemd terminology):
systemctl set-default multi-user.target.

Analogously for GUI: systemctl set-default graphical.target
