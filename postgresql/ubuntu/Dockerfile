# DOCKER-VERSION 0.11.1
# TO tinyerp/ubuntu-postgresql-9.3
FROM ubuntu:14.04

MAINTAINER Florent Xicluna, @florentxicluna

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
