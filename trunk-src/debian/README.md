Run OpenERP on Debian - June 2014
---------------------------------

*Built with Docker 0.11.1*

Features:

 - Debian Jessie
 - PostgreSQL 9.3
 - OpenERP 7.0 (or trunk)
 - SSH server
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

Manhole access:

 1. `OPENERP_IP=$(docker inspect --format='{{.NetworkSettings.IPAddress}}' openerp)`
 2. `ssh-keygen -R $OPENERP_IP` (because Docker assigns the same IP to different hosts)
 3. `ssh root@$OPENERP_IP -p 22` (default password `password`)

Images available:

 - `tinyerp/debian-openerp:6.1`
 - `tinyerp/debian-openerp:7.0` (same as) `tinyerp/debian-openerp`
 - `tinyerp/debian-openerp:8.0` (same as) `tinyerp/debian-odoo`

Source repository: [https://github.com/tinyerp/odoo-docker][4]

  [1]: https://index.docker.io/u/tinyerp/ubuntu-openerp/
  [2]: http://docs.docker.io/en/latest/ "docs.docker.io"
  [3]: http://127.0.0.1:8069/
  [4]: https://github.com/tinyerp/odoo-docker
