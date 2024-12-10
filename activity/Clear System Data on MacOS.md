Investigate:

* `/Library/Logs` & `~/Library/Logs`
* `/Library/Caches`, `~/Libarary/Caches`, & `/System/Library/Caches`
* `~/Library/Application Support/MobileSync/Backup`
* Also in `~/Library`:
	* `Cache`
	* `Containers`
	* `Group Containers`
	* `Logs`
	* `Messages`
	* `Mail`
	* `Screen Recordings
* `tmutil listlocalsnapshotdates` before `tmutil deletelocalsnapshots "xxxxxxx"`
* `diskutil list internal`

Use Shift+Cmd+G in Finder to copy-n-paste paths that might otherwise frustrate or be restricted in a terminal.

Sorting folders by size in Finder doesn't seem to work.

https://www.omnigroup.com/more
OmniDiskSweeper ..works pretty well as a GUI.

Largest was `~/Library/Mobile Documents/com~Apple~CloudDocs` (where iCloud files are synced locally) at 104G.

:

		/private/var     # 3G
		/usr/local       # lots of Homebrew stuff 14G
		/Applications    # 13.5G
		~/Library/Caches # 13G
		~/Library/Application Support  # 