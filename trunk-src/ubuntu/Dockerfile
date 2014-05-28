# DOCKER-VERSION 0.11.1
# TO tinyerp/ubuntu-openerp:8.0
FROM tinyerp/ubuntu-postgresql-9.3

# Install tarball from master branch on GitHub
# Create PostgreSQL user "odoo"
# Untar configuration "/etc/supervisor/conf.d/" and "/etc/odoo/"
RUN export DEBIAN_FRONTEND=noninteractive LANG=en_US.UTF-8 \
 && apt-get install -y --no-install-recommends python-geoip python-gevent \
    python-ldap python-lxml python-markupsafe python-pil python-pip \
    python-psutil python-psycopg2 python-pychart python-pydot \
    python-reportlab python-simplejson python-yaml wget wkhtmltopdf \
 && adduser --system --group --home /var/lib/odoo --shell /bin/sh odoo \
 && pg_ctlcluster 9.3 main start && su - postgres -c "createuser -d odoo" \
 && wget -nv -O- https://github.com/odoo/odoo/archive/master.tar.gz | tar xz \
    -C /opt && mv /opt/odoo-master /opt/odoo && pip install -e /opt/odoo \
 && echo H4sIACwkhVMCA+2XXW+bMBiFueZXoF4nGBM+tEi5qLSuq7QlUqtpF1OFKLjUWrCZDam0X \
 7/XtDQ0omovEtpo73MRwzFWDMfHHy6xDo7neX4chqakcej1yw6L+rOA+jSKAh/0yKex5YTWEdG9SF \
 ceCS6RuZRkLP+ffaIh/2eB0WPqe+j/iP6bn6lmasOUm0lxu/dPEwXBi/7TONj678M4gYswshwL/T8 \
 4v2RVcyn0tZ3mOZRJldZ3zsIhoD8OjYoJpiryUD/ZVjwI0K7kApppfZ9Dw/bWXssiuUtFvmYKtPnF \
 8stqcs/U77+sKeY/Ty+XF8tz20I+QP51U0HuuZaKHC4ab53/w9ijkH8vgALn/7H9NzO/m5P389/3P \
 bP/ozSE5QL9fyf/K6nrQjH9Z72fvcBr63/oRdv8R8b/IITjAa7/Y6z/lZKFSsv51vRrO5NlCYu32Q \
 Y0WpE1v+mNCfLJnZEbLp4kZ/rZIZt08Lky5cKZZo4ZR7xIbvmaLQirs6Hndsed3eh299DJdtrUcJm \
 qGsRaNawVoKIvKZZzxbI60XXOlOrkiufmv80bmZ6qRuz0YGp64MJjNjSUTZ3ADqbfAm77Sel1FWqO \
 eCczlH+zu9vnKeC1/Ach7c3/oNOZH8WY/1Hzb0x/lvzdA8Dj8dCkuU3w4Lmxy6zRbSY2XElRMmHi+ \
 ePq7HJxYipOJt9W58vT72fd7deVuX6aQ1pxz2nvdfRtCe+/2XFHHEEQBEEQBEEQBEEQBEGQ/5R/5/ \
 CeYQAoAAA=                                                                    \
  | base64 -di | tar xz -C /etc

# Declare volumes for PostgreSQL data and logs
VOLUME ["/var/lib/postgresql", "/var/log/postgresql"]

# Expose HTTP port
EXPOSE 8069

# Autostart supervisor daemon
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
