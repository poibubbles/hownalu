Short version: updating `iTerm2` toBuild 3.4.21 seems to have worked. Updated using the builtin "Check For Updates..." option in the running app.

Long version:

In fullscreen mode on MacOS, both `iTerm2` and the builtin `Terminal` occasionally flicker a white line across the top of the screen.

Hilariously, for `iTerm2` there's this option: `Preferences > Advanced > Work around Big Sur bug where a white line flashes at the top of the screen in full screen mode`

Unfortunately toggling that setting and restarting `iTerm2` didn't work.

There's also:
* `Preferences -> Appearance -> Windows -> Show line under title bar when the tab bar is not visible`
* `Preferences > Advanced > Draw outline around underline and vertical bar cursors using background color.`

More insights:
* https://gitlab.com/gnachman/iterm2/-/issues/9372
* https://gitlab.com/gnachman/iterm2/-/issues/9199