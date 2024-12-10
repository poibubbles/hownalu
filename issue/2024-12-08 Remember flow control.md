In Linux, if the terminal is unresponsive, remember that:

* `Ctrl-S` turns off flow control (terminal stops receiving input) and
* `Ctrl-Q` turns it on again - and then whatever input got queued will be
  received (and printed and executed if you hit Enter)
