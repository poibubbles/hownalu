
## RestartSec vs. RestartUSec
Configuration options vs. properties?

See `man 7 systemd.directives` for an index of stuff like `RestartSec=`.
It'll tell you where to go for the specifics.

`RestartSec` is described in `man 5 systemd.service`. `RestartUSec` isn't.

From `man 5 org.freedesktop.systemd1` on unit properties: "Many properties
shown by systemctl show map directly to configuration settings of the system
and service manager and its unit files. Note that the properties shown by the
command are generally more low-level, normalized versions of the original
configuration settings and expose runtime state in addition to configuration.
For example, properties shown for service units include the service's current
main process identifier as "MainPID" (which is runtime state), and time
settings are always exposed as properties ending in the "...USec" suffix even
if a matching configuration options end in "...Sec", because microseconds is
the normalized time unit used internally by the system and service manager."


