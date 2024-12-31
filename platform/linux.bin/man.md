Important sections see `man man`:
* 1 executables or shell commands
* 5 file formats and conventions
* 8 sytem administration commands

Use `man N intro` for an introduction to the section `N`.

```
man hier
man 7 file-hierarchy
man -f something
man -k something
```

`man` pages are all indexed in `mandb`.

`man -k|-f` or `apropos` may not work on a fresh system because the scheduled
task to build the database may not have run. Either wait for the scheduled task to build the database or kick it off a root: `sudo mandb`

Search using `/`.

Ever wonder why the name of the command in man pages is in caps (on the top left of the man
page)? Because: Respect for history.
