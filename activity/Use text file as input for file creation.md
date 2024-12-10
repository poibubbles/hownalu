There's probably a lot of things that apply here. We're gonna start with..

How to create a bunch of files given one file name per line in a text file, given that each line may not be quoted and may contain confounding characters.

See https://mywiki.wooledge.org/DontReadLinesWithFor.

Ran with: `while read FILE; do touch "${FILE}"; done < input.txt` from https://superuser.com/q/590324.