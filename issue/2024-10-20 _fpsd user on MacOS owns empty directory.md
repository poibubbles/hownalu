Was denied deletion of a `adi/` directory in `users/Shared/` because is was owned by `_fpsd`.

Running `dscacheutil -q user`, found:

	name: _fpsd
	password: *
	uid: 265
	gid: 265
	dir: /var/db/fpsd
	shell: /usr/bin/false
	gecos: FPS Daemon

Also, `dscl . -search /Users name _fpsd` returned:

	_fpsd           dsAttrTypeNative:name = (
    "_fpsd"
    )

And `ps aux | grep _fpsd` returned several processes, of which one was running `/System/Library/PrivateFrameworks/CoreADI.framework/adid`.

From https://macosbin.com/bin/adid:

	The binary is a part of [CoreADI](https://macosbin.com/bin/CoreADI) private framework.

After that I got bored looking for more information on CoreADI.