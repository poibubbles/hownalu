
Output from last `brew` update:

	A "/etc/my.cnf" from another install may interfere with a Homebrew-built
	server starting up correctly.
	
	MySQL is configured to only allow connections from localhost by default
	
	To restart mariadb after an upgrade:
	  brew services restart mariadb
	Or, if you don't want/need a background service you can just run:
	  /usr/local/opt/mariadb/bin/mysqld_safe --datadir\=/usr/local/var/mysql