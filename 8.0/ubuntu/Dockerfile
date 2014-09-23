# DOCKER-VERSION 1.2.0
# TO tinyerp/ubuntu-odoo
# TO tinyerp/ubuntu-openerp:8.0
FROM tinyerp/ubuntu-postgresql:9.4

# Install tarball from master branch on GitHub
# Create PostgreSQL user "odoo"
# Untar configuration "/etc/supervisor/conf.d/odoo.conf"
# and "/etc/odoo/odoo-server.conf"
RUN export DEBIAN_FRONTEND=noninteractive LANG=en_US.UTF-8 \
 && apt-get install -y --no-install-recommends python-geoip python-gevent \
    python-ldap python-lxml python-markupsafe python-pil python-pip \
    python-psutil python-psycopg2 python-pychart python-pydot \
    python-reportlab python-simplejson python-yaml wget wkhtmltopdf \
 && adduser --system --group --home /var/lib/odoo --shell /bin/bash odoo \
 && pg_ctlcluster 9.4 main start && su - postgres -c "createuser -d odoo" \
 && wget -nv -O- https://github.com/odoo/odoo/archive/8.0.tar.gz \
  | tar xz --xform s,^odoo-8.0,odoo, -C /opt && cd /opt/odoo \
 && pip install -e . \
 && echo H4sIAAM2oFMCA+3VzWrCQBQFYNd5ijyAmj/tQnDhwlqhVbCULopImlw1aDLhzkShT9+b \
 0aKVQjfSIpxvkcmcmQkJyZ2oVClPyaGliXfE7UQVy8Z1+eKu07GtuGz9MPAbQRh1fT8K7bwg9CVy \
 G7fk8uFuxJsqTaYKPXfiNJV2UcZm7fZdT3L7XcgJFcSldxhvngYOgazLs0KWab1PZaHtOlu1Wqzj \
 It0SS9YbT+6nzT3x5oOqVe91MJuMJyNnr3hDrGVC6DTgX+iqlLrPtGKvrvx2at/tdXeB3+q/43dO \
 9R9EUv9REHVR/39S/yWrFcd5r37tcydReS5l+9MGcPxBuK3E9cgkx7GLP4dTaVvxde5QsctYFTkV \
 RqKX5+GsX+fNx+loMngaHjoPUznzdjF72+zdXs+JK6O0ibleZbgiGzB9i5jSjCkxC21SYv6Kpacq \
 s5DtZ5ltqX4Me2W18s4+9PObliHsPQAAAAAAAAAAAAAAAAAAAHDTPgGW0D0SACgAAA==         \
  | base64 -di | tar xz -C /etc

# Declare volumes for data
VOLUME ["/var/lib/odoo", "/var/lib/postgresql"]

# Expose HTTP port, and longpolling port
EXPOSE 8069 8072
