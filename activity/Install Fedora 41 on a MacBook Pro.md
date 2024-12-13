Follow live USB creation steps here:
https://docs.fedoraproject.org/en-US/fedora/latest/preparing-boot-media

Download Fedora Media Writer here:
https://fedoraproject.org/workstation/download

Opening the Media Writer will probably will probably throw a security warning.
If so, go to `System Settings > Privacy and Security` and "Open [it] Anyway".

Checklist:
* `dnf install -y vim-enhanced tmux stow lm_sensors xsensors seahorse upower
  acpi inxi`
* SSH keys for Github
* Clone `dotfiles`.
* Install Bitwarden Flatpak from Flathub via Fedora Apps. Also maybe the CLI
  from the Bitwarden website.
* Install Obsidian Flatpak from Flathub via Fedora Apps.

