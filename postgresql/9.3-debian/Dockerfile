# DOCKER-VERSION 0.11.1
# TO tinyerp/debian-postgresql:9.3
FROM debian:jessie

MAINTAINER Florent Xicluna, @florentxicluna

# Install PostgreSQL and Dropbear (SSH server)
# Untar configuration "/etc/supervisor/conf.d/"
RUN apt-key adv --keyserver pool.sks-keyservers.net \
    --recv-keys B97B0AFCAA1A47F044F244A07FCC7D46ACCC4CF8 \
 && echo deb http://http.debian.net/debian jessie main contrib non-free \
    > /etc/apt/sources.list.d/debian-jessie.list \
 && echo deb http://apt.postgresql.org/pub/repos/apt/ sid-pgdg main \
    > /etc/apt/sources.list.d/pgdg.list \
 && /bin/rm /etc/apt/sources.list && echo en_US.UTF-8 UTF-8 > /etc/locale.gen \
 && export DEBIAN_FRONTEND=noninteractive LANG && apt-get update \
 && apt-get install -y --no-install-recommends apt-utils dropbear locales \
    logrotate supervisor && echo "root:password" | chpasswd \
 && update-locale LANG=en_US.UTF-8 && . /etc/default/locale \
 && apt-get install -y postgresql-9.3 postgresql-contrib-9.3 \
 && echo H4sIAFhni1MCA+3U22qEMBAGYK99Cl9gjadaurB3fYtSxENWAmrsmCz07Tva1e3aQi+K \
 BeH/ECR/gkGSmYp0X8ic/FJ3Z2cbAUuTZHqz9TuIg8gJoziJ0pSf1AnCIIkix3P2ZP1zO/HSk64p \
 b4/V9SK8uqVu27yrvJMnpCnFPCHIdm6lSJZG0/t61rWDJA5Ja+Pm1ujB5GQ4MGTlFJC8i0h+fisb \
 TCWJ5phH2pqs0fVZNXLc5cJb81AMtpd0UYOmZVOfc9eBP+j5oGo+mrdmuw7wW/0ncbzU/+MD52EY \
 RCnq/1/r/3YR7jqAHbj6VCFu0+LJj0WhuiXyDs/XKv2+rs1V5x1Kb7xbqs7Gmj5NfeOHdWJ1F+eW \
 Msebt5Uv+6OxAAAAAAAAAAAAAAAAAAAAwG58AAcaT1YAKAAA                             \
  | base64 -di | tar xz -C /etc/supervisor/conf.d

# Declare volume for log files
VOLUME ["/var/log/supervisor"]

# Autostart supervisor daemon
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
