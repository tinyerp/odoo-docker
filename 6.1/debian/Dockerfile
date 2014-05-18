# DOCKER-VERSION 0.11.1
# TO tinyerp/debian-openerp-6.1
FROM debian:jessie

MAINTAINER Florent Xicluna, @florentxicluna

# tinyerp/debian-postgresql-9.3
RUN apt-key adv --keyserver pool.sks-keyservers.net \
    --recv-keys B97B0AFCAA1A47F044F244A07FCC7D46ACCC4CF8 \
 && echo deb http://http.debian.net/debian jessie main contrib non-free \
    > /etc/apt/sources.list.d/debian-jessie.list \
 && echo deb http://apt.postgresql.org/pub/repos/apt/ sid-pgdg main \
    > /etc/apt/sources.list.d/pgdg.list \
 && /bin/rm /etc/apt/sources.list && echo en_US.UTF-8 UTF-8 > /etc/locale.gen \
 && export DEBIAN_FRONTEND=noninteractive LANG && apt-get update \
 && apt-get install -y --no-install-recommends apt-utils locales logrotate \
 && update-locale LANG=en_US.UTF-8 && . /etc/default/locale \
 && apt-get install -y postgresql-9.3 postgresql-contrib-9.3 supervisor

# Install "openerp.deb"
# Create PostgreSQL user "openerp"
# Untar configuration "/etc/supervisor/conf.d/"
RUN echo deb http://nightly.odoo.com/6.1/nightly/deb/ ./ \
    > /etc/apt/sources.list.d/openerp-61.list \
 && export DEBIAN_FRONTEND=noninteractive LANG=en_US.UTF-8 \
 && apt-get update && apt-get install -y --allow-unauthenticated openerp \
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

# Declare volumes for PostgreSQL data and logs
VOLUME ["/var/lib/postgresql", "/var/log/postgresql"]

# Expose HTTP port
EXPOSE 8069

# Autostart supervisor daemon
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
