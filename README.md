Docker images for Odoo / OpenERP
================================


This repository provides ~~trusted~~ Dockerfiles for Odoo (formerly OpenERP).

Built images are uploaded to [hub.docker.com][1]


Main images:

 - OpenERP 7.0 on Debian/Ubuntu (./7.0/)
 - OpenERP 6.1 on Debian only (./6.1/)
 - Odoo trunk on Debian/Ubuntu (./trunk-src/)


PostgreSQL images:

 - PostgreSQL 9.3 on Debian/Ubuntu (./postgresql/)
 - PostgreSQL 9.4 beta on Debian (./postgresql/)


Usage:

 - Install Docker: [docs.docker.com][2]
 - Execute
 `docker run -d --name odoo -p 8069:8069 tinyerp/debian-odoo`
 - Browse [http://&lt;your server ip address&gt;:8069/][3]
 - Stop and start again
   - `docker stop odoo`
   - `docker start odoo`

Other images are listed on [hub.docker.com][1]

Note: no trusted images because of [Docker bug #5892][4]

  [1]: https://registry.hub.docker.com/repos/tinyerp/
  [2]: https://docs.docker.com/ "docs.docker.com"
  [3]: http://127.0.0.1:8069/
  [4]: https://github.com/dotcloud/docker/issues/5892
