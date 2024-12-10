Used Sequel Pro (free GUI).

With version 11.4.2 on MacOS via Homebrew, there's a likelihood of getting a `[ERROR] InnoDB: Missing FILE_CHECKPOINT` error running MariaDB on MacOS. See https://jira.mariadb.org/browse/MDEV-34422 and https://jira.mariadb.org/browse/MDEV-34689. 

This is somewhat mitigated by:

* https://dba.stackexchange.com/questions/317572/mariadb-missing-file-checkpoint
* https://www.reddit.com/r/mariadb/comments/1ekz4zh/constant_innodb_errors_missing_file_checkpoint/

..and basically using version 10.6 in the meantime. See the links above for a stepwise downgrade from version 11 to 10.11 to 10.6. I just removed everything (including all the database info in `/usr/local/var/mysql/`) and started from scratch with 10.6.

	brew remove mariadb
	brew cleanup
	brew install mariadb@10.6
	brew services start mariadb@10.6
	brew services info --all
	ls /tmp/mysql.sock
	# set path to include /usr/local/opt/mariadb@10.6/bin/
	mariadb < wordpress_export.sql

Auto-starting and stopping a Homebrew installation:

	brew services info --all
	brew services start mariadb
	brew services stop mariadb

Manually start using ``run``::

	brew services run mariadb

More info on Homebrew's service support here: https://thoughtbot.com/blog/starting-and-stopping-background-services-with-homebrew

Check configuration of local installation:

	mariadbd --verbose --help | less

Note default options files, `datadir`, `basedir`, `socket`.

Import SQL:

	mariadb db_name < export.sql

Check authenticated user:

	SELECT CURRENT_USER();
	SELECT USER();

See the difference between the two here: https://dev.mysql.com/doc/refman/8.4/en/information-functions.html#function_current-user


