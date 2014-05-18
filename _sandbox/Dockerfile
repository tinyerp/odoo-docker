# DOCKER-VERSION 0.11.1
# TO tinyerp/sandbox-postgresql
FROM tinyerp/debian-postgresql-9.3

# Create PostgreSQL user "openerp"
# Untar configuration "/etc/supervisor/conf.d/"
RUN export DEBIAN_FRONTEND=noninteractive LANG=en_US.UTF-8 \
 && service postgresql start && su - postgres -c "createuser -d openerp" \
 && service postgresql stop

CMD ["/bin/bash"]
