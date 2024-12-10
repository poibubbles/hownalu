Two `ssh-keygen` commands were copied and pasted from [[Authenticate at Github via SSH key]]. The first worked, the second didn't.

This line (from Github) works via tmux copy/paste:
```
  ssh-keygen -t ed25519 -C "your_email@example.com"
```
This line (from Atlassian) doesn't:
```
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
  zsh: command not found: ssh-keygen -t rsa ...
```
..because the apparent space characters in the line above aren't normal spaces:
```
  32,  Hex 20,  Oct 040, Digr SP
```
Instead, they are the Unicode non-breaking space character (as revealed by ``vim``'s ``:ascii``):
```
  160, Hex 00a0, Oct 240, Digr NS
```
Why would a command on a website be formatted to frustrate copy-n-pasting?

Here's somebody who apparently wants to go the other way: https://stackoverflow.com/q/47135608