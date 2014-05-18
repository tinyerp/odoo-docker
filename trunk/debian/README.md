Run OpenERP on Debian - May 2014
--------------------------------

*Built with Docker 0.11.1*

Features:

 - Debian Jessie
 - PostgreSQL 9.3
 - OpenERP 7.0 (or trunk)
 - Supervisor

(Ubuntu build : [tinyerp/ubuntu-openerp][1])

Usage:

 - Install Docker: [http://docs.docker.io/][2]
 - Execute
 `docker run -d --name openerp -p 8069:8069 tinyerp/debian-openerp`
 - Browse [http://&lt;your server ip address&gt;:8069/][3]
 - Stop and start again
   - `docker stop openerp`
   - `docker start openerp`

Images available:

 - `tinyerp/debian-openerp:6.1`
 - `tinyerp/debian-openerp:7.0` (same as) `tinyerp/debian-openerp:latest`
 - `tinyerp/debian-openerp:8.0`

Source repository:
 - [https://github.com/tinyerp/odoo-docker][4]

  [1]: https://index.docker.io/u/tinyerp/ubuntu-openerp/
  [2]: http://docs.docker.io/en/latest/ "docs.docker.io"
  [3]: http://127.0.0.1:8069/
  [4]: https://github.com/tinyerp/odoo-docker
