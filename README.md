Docker images for Odoo / OpenERP
================================


This repository provides ~~trusted~~ Dockerfiles for Odoo (formerly OpenERP).

Built images are uploaded to [index.docker.io][1]


Main images:

 - OpenERP 7.0 on Debian/Ubuntu
 - OpenERP 6.1 on Debian only
 - Odoo trunk on Debian/Ubuntu


PostgreSQL images:
 - PostgreSQL 9.3 on Debian/Ubuntu


Usage:

 - Install Docker: [http://docs.docker.io/][2]
 - Execute
 `docker run -d --name odoo -p 8069:8069 tinyerp/debian-odoo`
 - Browse [http://&lt;your server ip address&gt;:8069/][3]
 - Stop and start again
   - `docker stop odoo`
   - `docker start odoo`

Other images are listed on [index.docker.io][1]

Note: no trusted images because of [Docker bug #5892][4]

  [1]: https://index.docker.io/u/tinyerp/
  [2]: http://docs.docker.io/en/latest/ "docs.docker.io"
  [3]: http://127.0.0.1:8069/
  [4]: https://github.com/dotcloud/docker/issues/5892
