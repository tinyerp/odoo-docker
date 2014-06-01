Run PostgreSQL 9.3/9.4 on Debian - June 2014
--------------------------------------------

Base image is Debian Jessie

Content:

* Install Dropbear SSH Server
* Install PostgreSQL 9.3 or 9.4 beta
* Install Supervisor
* Run SSH server and PostgreSQL server on startup

Images available:

 - `tinyerp/debian-postgresql:9.3` (same as) `:latest`
 - `tinyerp/debian-postgresql:9.4`

Note: the default SSH `root` password is ... `password`.

(these are the base images for `tinyerp/debian-odoo` builds)

Source repository:
 - [https://github.com/tinyerp/odoo-docker][1]

  [1]: https://github.com/tinyerp/odoo-docker
