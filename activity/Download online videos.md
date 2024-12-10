* [yt-dlp](https://github.com/yt-dlp/yt-dlp) - A [youtube-dl](https://github.com/ytdl-org/youtube-dl) fork based on the now inactive [youtube-dlc](https://github.com/blackjack4494/yt-dlc).
* [cs-dlp](https://github.com/raffaem/cs-dlp) - A fork of [coursera-dl](https://github.com/coursera-dl/coursera-dl) that actually worked.

Both `cs-dlp` and `yt-dlp` installed in a virtual environment:
```
python -m venv venv
. venv/bin/activate

pip install yt-dlp cs-dlp 

yt-dlp -ci -a file-of-urls

deactivate
```

Installed `youtube-dl` via [Homebrew](https://brew.sh/) for MacOS: `brew install youtube-dl`