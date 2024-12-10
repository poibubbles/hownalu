As of the SCP (protocol) deprecation, here's some alternatives to consider:

	dd if=filename | ssh hostname dd of=filename
	
	tar c | ssh tar x  # good for lots of small files
    ssh tar c /foo | tar x -C /bar
		
	ssh cat /foo/bar > /bar/baz 
	cat file | ssh user@host 'cat >file'
	ssh user@host cat file | cat >file
	ssh user@remote "cat /path/to/target/file" < local file
	tar -cC /source/dir . | ssh rhost tar -xvC /dest/dir

	# rsync and sftp are needed on both sides
	rsync -v -e "ssh -p 1234" SRC user@host:/DST
	rsync --archive --xattrs --acls --progress --rsh=ssh
	sftp

Extra credit:

	dd if=foo | adb shell dd of=/storage/.../foo