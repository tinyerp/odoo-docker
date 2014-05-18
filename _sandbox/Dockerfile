# DOCKER-VERSION 0.11.1
# TO tinyerp/sandbox-postgresql
FROM tinyerp/debian-postgresql-9.3

# Create PostgreSQL user "openerp"
# Untar configuration "/etc/supervisor/conf.d/"
RUN export DEBIAN_FRONTEND=noninteractive LANG=en_US.UTF-8 \
 && pg_ctlcluster 9.3 main start && su postgres -c 'createuser -d openerp' \
 && pg_ctlcluster 9.3 main stop

CMD ["/bin/bash"]
