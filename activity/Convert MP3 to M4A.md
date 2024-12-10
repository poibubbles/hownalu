Apparently the problem with naively converting `mp3` to `m4a` is that the `mp3` has embedded artwork that `ffmpeg` interprets as video (incompatible with `ffmpeg` compiled without `libx264`). 

Avoid attempting video conversion with `-vn`:
```
ffmpeg  -i Kalimba.mp3 -c:a aac -vn Kalimba.m4a
```

From https://stackoverflow.com/a/16376637.

#macos