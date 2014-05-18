Run OpenERP on Ubuntu - April 2014

*Built with Docker 0.11.1*

Features:

 - Ubuntu 14.04 LTS (Trusty Tahr)
 - PostgreSQL 9.3
 - OpenERP 7.0 (or trunk)
 - Supervisor

(Debian build : [tinyerp/debian-openerp][1])

Usage:

 - Install Docker: [http://docs.docker.io/][2]
 - Execute
 `docker run -d --name openerp -p 8069:8069 tinyerp/ubuntu-openerp-7.0`
 - Browse [http://&lt;your server ip address&gt;:8069/][3]
 - Stop and start again
   - `docker stop openerp`
   - `docker start openerp`

Images available:

 - `tinyerp/ubuntu-openerp-7.0`
 - `tinyerp/ubuntu-openerp-8.0`

  [1]: https://index.docker.io/u/tinyerp/debian-openerp-7.0/
  [2]: http://docs.docker.io/en/latest/ "docs.docker.io"
  [3]: http://127.0.0.1:8069/
