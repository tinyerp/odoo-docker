# DOCKER-VERSION 0.11.1
# TO tinyerp/ubuntu-odoo
# TO tinyerp/ubuntu-openerp:8.0
FROM tinyerp/ubuntu-postgresql:9.3

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
 && pg_ctlcluster 9.3 main start && su - postgres -c "createuser -d odoo" \
 && wget -nv -O- https://github.com/odoo/odoo/archive/master.tar.gz \
  | tar xz --xform s,^odoo-master,odoo, -C /opt && cd /opt/odoo \
 && ln -s setup/setup.py && pip install -e . \
 && echo H4sIAHVqi1MCA+3V32rCMBQG8F73KfoAav9OQfDCC+eErYJj7GJI6dpYy9qmnKQKe/qd \
 VsecDHYjG8L3u2iaL6S0JCeVqZS25EtfCdoJGiSy2hiX5bBhEHQtO28ddxQYrucH3nDo3Xi+4bie \
 440My7gm5x93JV5krXNZqbUZpym3UR3rrTWxbM67fcE3ohJU24fx3tfAIeB5ZV7xNKX2KU/sumYh \
 s2gbV2khiLPxIrxd9vaC3t5Fk42fp6twEc5NA/6damqu+1xJstvKH6Td2l72FPit/gPns/7doTPi \
 3PXdwEf9/0n91yQzistxu+xrM5FlyWX70wFw/EFY/cSyhU6OY2d/DrNRXcW3uSmqXU6yKkWlOXp6 \
 nK0mbd67X87D6cPs0Llb8p29i8ku8tfueWbcaKl0TO0sTY3oAhLfIhJpTiLRkdKpIPqMuScbHfHx \
 s8kL0X5G92SZ2Scb/fSleQjnEAAAAAAAAAAAAAAAAAAAAFy1D6bmcCMAKAAA                 \
  | base64 -di | tar xz -C /etc

# Declare volumes for data
VOLUME ["/var/lib/odoo", "/var/lib/postgresql"]

# Expose HTTP port
EXPOSE 8069
