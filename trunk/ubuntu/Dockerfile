# DOCKER-VERSION 0.11.1
# TO tinyerp/ubuntu-openerp-8.0
FROM ubuntu:14.04

MAINTAINER Florent Xicluna, @florentxicluna

# tinyerp/ubuntu-postgresql-9.3
RUN apt-key adv --keyserver pool.sks-keyservers.net \
    --recv-keys B97B0AFCAA1A47F044F244A07FCC7D46ACCC4CF8 \
 && /bin/mv /etc/apt/sources.list /etc/apt/sources.list.d/ubuntu.list \
 && echo deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main \
    > /etc/apt/sources.list.d/pgdg.list \
 && mv /usr/bin/ischroot /usr/bin/chroot.orig \
 && ln -s /bin/true /usr/bin/ischroot \
 && export DEBIAN_FRONTEND=noninteractive LANG && apt-get update \
 && apt-get install -y --no-install-recommends language-pack-en \
 && update-locale LANG=en_US.UTF-8 && . /etc/default/locale \
 && apt-get install -y postgresql-9.3 postgresql-contrib-9.3 supervisor

# Install "openerp.deb"
# Create PostgreSQL user "openerp"
# Untar configuration "/etc/supervisor/conf.d/"
RUN echo deb http://nightly.odoo.com/trunk/nightly/deb/ ./ \
    > /etc/apt/sources.list.d/openerp-trunk.list \
 && export DEBIAN_FRONTEND=noninteractive LANG=en_US.UTF-8 \
 && apt-get update && apt-get install -y --allow-unauthenticated openerp \
 && apt-get install -y wkhtmltopdf python-geoip \
 && mkdir ~openerp && chown openerp:openerp ~openerp \
 && service postgresql start && su - postgres -c "createuser -d openerp" \
 && echo H4sIAHk6WlMCA+2UTU+DQBCGOfMrNj0LCxSWaNKDiY0e/Eg0noxpKGxxE9jF5eP3OxCq \
 FGvSg5hg5rkA7yztbHee2tSYHAcIg6C7AuNrd+96S495zPfcEHLmstAggTEjxpubCTYtVFmlmpfv \
 mR0ruZvop2G+/+P5Bw6D8/fCIGSeF0Duui4LDGLg+U/OS6FVqqP84msMXs1Y5XkkE7IitC41zcR2 \
 MCX03F7SrZCfEbGuCG2io+vySEhixaSdLJFudiLjK8qr+Ni68SSadck19LCPzaiu4DbSFYSVrnkX \
 QGEYaZ4IzeNqU1YJ13ofFyJpv7vdUdupruWoA6vtwIZlJryo6mqTqXT4BjzSsi64bkSp9LBVqJjG \
 bLGpKrjkuphK/pP8H/7/M/Df8T0H/f9T//sx+CZ/a3pfs8DHBpQEnzuH+3hUPnC3L5lcNkIrmXPZ \
 mvr8tH5cLfra4uz24fr+8m49SG4e2kf6pnK+//TFL+t/2PRp1o82Om/zEQRBEARBEARBEARBEARB \
 EARBEARBkP/EB0y9pT8AKAAA \
  | base64 -di | tar xz -C /etc/supervisor/conf.d

# Expose HTTP port
EXPOSE 8069

# Autostart supervisor daemon
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
