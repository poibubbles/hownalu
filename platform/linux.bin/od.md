Octal, decimal, hex, ASCII dump.

Interesting that `vim` and even `echo` add a newline (`0x0a`):

	echo 'a' | od -h
	00000000    0a61
	
	echo -n 'a' | od -h
	00000000    0061

	echo 'a' > a ; ls -l a