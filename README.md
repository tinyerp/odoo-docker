Docker images for Odoo / OpenERP
================================


This repository provides trusted (but unofficial) Dockerfiles for OpenERP.

Built images are uploaded to [index.docker.io][1]


Main images:

 - OpenERP 7.0 on Debian
 - OpenERP 7.0 on Ubuntu
 - OpenERP 6.1 on Debian
 - OpenERP trunk on Debian
 - OpenERP trunk on Ubuntu


PostgreSQL images:
 - PostgreSQL 9.3 on Debian
 - PostgreSQL 9.3 on Ubuntu


Usage:

 - Install Docker: [http://docs.docker.io/][2]
 - Execute
 `docker run -d --name openerp -p 8069:8069 tinyerp/debian-openerp-7.0`
 - Browse [http://&lt;your server ip address&gt;:8069/][3]
 - Stop and start again
   - `docker stop openerp`
   - `docker start openerp`

Other images are listed on [index.docker.io][1]

  [1]: https://index.docker.io/u/tinyerp/
  [2]: http://docs.docker.io/en/latest/ "docs.docker.io"
  [3]: http://127.0.0.1:8069/
