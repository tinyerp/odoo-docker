Run PostgreSQL 9.3/9.4 on Ubuntu - September 2014
-------------------------------------------------

Base image is Ubuntu 14.04 LTS (Trusty Tahr)

Content:

* Install Dropbear SSH Server and the rsync utility
* Install PostgreSQL 9.3 or 9.4 beta
* Install Supervisor
* Run SSH server and PostgreSQL server on startup

Images available:

 - `tinyerp/ubuntu-postgresql:9.3` (same as) `:latest`
 - `tinyerp/ubuntu-postgresql:9.4`

Note: the default SSH `root` password is ... `password`.

(these are the base images for `tinyerp/ubuntu-odoo` builds)

Source repository: [https://github.com/tinyerp/odoo-docker][1]

  [1]: https://github.com/tinyerp/odoo-docker
