
Get full path names:
```
# explicit
find ./ -name "myfile" -exec readlink -f {} \;

# implicit, Bash-specific, gives absolute path relative to PWD (preserves
# links you've descended into)
find ~+ -name "myfile"
# also, for some other search path $DIR
cd $DIR && find ~+ -name "myfile" && cd -
```


```
find /etc/ -name '*' -type f | xargs grep "127.0.0.1"  2> /dev/null
find / -name "*hosts*" 2> /dev/null
find / -type f -size +100M  # files bigger than 100M
```

The braces are kinda like where the results of the `find -size +1K` goes. And `\;` *closes* the `-exec` statement. Every `-exec` needs its own `\;`.
```
find /etc -size +1k -exec grep -l student {} \;
find /etc -size +1k -exec grep -l student {} \; -exec cp {} find/contents/ \;
# wow
```
