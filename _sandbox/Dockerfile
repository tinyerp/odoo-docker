# DOCKER-VERSION 0.11.1
# TO tinyerp/sandbox-postgresql
FROM tinyerp/debian-postgresql-9.3

# Create PostgreSQL user "openerp"
# Untar configuration "/etc/supervisor/conf.d/"
RUN export DEBIAN_FRONTEND=noninteractive LANG=en_US.UTF-8 \
 && PGDATA=/etc/postgresql/9.3/main su postgres \
 -c '/usr/lib/postgresql/9.3/bin/pg_ctl -w start && createuser -d openerp' \
 && chown -cR postgres:postgres /var/lib/postgresql/9.3/main

CMD ["/bin/bash"]
