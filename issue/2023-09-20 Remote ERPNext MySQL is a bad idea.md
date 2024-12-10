It was a fun idea to support local-hosted [[ERPNext]] instances via cloud-hosted MySQL instances (even though ERPNext wants to use MariaDB).

As of 2021-03, running ERPNext's DB remotely is ["a bad idea"](https://discuss.frappe.io/t/how-to-change-to-mysql-database/72315/4). Regardless, it can be done by editing `frappe-bench/sites/common_site_config.json` and setting `db_host` accordingly.

With respect to MariaDB-MySQL compatibility, see the following:
* https://mariadb.com/kb/en/mariadb-vs-mysql-compatibility/
* https://mariadb.com/kb/en/function-differences-between-mariadb-and-mysql/
* https://mariadb.com/kb/en/mariadb-vs-mysql-features/

In most cases, it seems that "close enough" versions should work. The two DBs apparently leap frog each other, so for the sake of choosing a cloud-based MySQL version I'd err on the side of "last version that the MariaDB version ERPNext wants to use followed."

Encountered during the [[Install ERPNext on Compute Engine]] exercise.