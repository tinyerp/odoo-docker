# DOCKER-VERSION 0.11.1
# TO tinyerp/debian-postgresql-9.3
FROM debian:jessie

MAINTAINER Florent Xicluna, @florentxicluna

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
