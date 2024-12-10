Bash loop:
```
for j in *.md; do mv -v -- "$j" "${j%.md}.txt"; done
```

Fish loops..
..[documented](https://fishshell.com/docs/current/cmds/string-replace.html):
```
for f in *.md; mv $f $(string replace ".md" ".txt" $f); end
```
..formal:
```
for j in *.md
    mv -v -- $j (string replace -r '\.md$' .txt $j)
end
```
..more formal:
```
for file in *.md
    mv "$file" (echo "$file" | sed '$s/\.md$/.txt/')
end
```

Note replacements and regexs are preferable to `basename` because they work better with targets like `/something/**/*.ext`.

Finally used this to convert a bunch of `.opus` to `.mp3`:
```
for file in *.opus
	ffmpeg -i $file (string replace -r '\.opus$' .mp3 $file)
end
```

https://stackoverflow.com/q/38590165
https://superuser.com/q/1709658