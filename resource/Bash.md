`Ctrl +`:

* c quits current interactive process
* d end-of-file character (normally exits)
* a start of current line
* e end of current line
* r reverse search
* l clear screen

`Alt +`:

* b moves cursor one word backward
* f ..................... forward

From `man bash` (`<<<`):

	   Here Strings
       A variant of here documents, the format is:
         <<<word
       The word is expanded and supplied to the command on its standard input.

## Globbing and expansion

* `ls *`
* `ls a?*`
* `ls [a-e]?*`
* `ls [A,E]?*`
* `touch file{1..9}` - brace expansion
* `useradd {lisa,lina,anna}`
* `~`
* `ls -l $(which ls)` - command substitution
* `echo $PATH` - variable substitution