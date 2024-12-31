
```
dnf repoquery -l package     # list files of uninstalled package

dnf history                  # what's been installed lately

```

Why does `dnf history` have `EE` in the `Altered` column? Probably because
`rpm`, `dnf`, and `yum` consider echoed statements from an RPM script to be a
warning. See https://access.redhat.com/solutions/1134423. See `dnf history
info <package>` to verify a successful installation.

