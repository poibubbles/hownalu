Launch a terminal.

Check if an SSH agent is running: ``env | grep SSH_AUTH_SOCK; ssh-add -L``
..if not, start one: ``eval "$(ssh-agent -s)"``
..and add a key: ``ssh-add --apple-use-keychain ~/.ssh/<keyname>

Start ``tmux`` or attach to a running ``tmux`` process: ``tmux at -d``

Start ``fish``.

Start ``edgedb``:

		edgedb instance list --extended
		edgedb instance start -I <name>
		edgedb ui &