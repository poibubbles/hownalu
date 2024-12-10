
# This worked

From https://sleonproductions.com/how-to-fix-icloud-drive-stuck-at-uploading-in-mac/:

"Have you ever had an issue with your iCloud Drive is stuck uploading and you can see your updated files on your iPhone Files app?"

Short version: delete `~/Library/Application Support/CloudDocs/`

This quickly triggered an iCloud update (pie icon) in Finder and then an uploading status that seemed to be in the process of discovering new files to upload.

# Didn't try this

From https://apple.stackexchange.com/q/264915, several options:

Killing or `renice`-ing `bird`:
```
ps aux | grep bird
ps -fl -C <bird PID>
sudo renice -n -10 -p <bird PID>

# or..

killall bird
```

Updating times on all files that don't match `.icloud` (seems a little major):
```
cd $HOME/Library/Mobile\ Documents/com~apple~CloudDocs
find . ! -path "*.icloud" \( -exec echo {} \; -a -exec touch {} \; \)
```

And some other methods that involved restarting iCloud backups one way or another.

#macos