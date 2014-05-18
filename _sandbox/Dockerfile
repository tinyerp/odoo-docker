# DOCKER-VERSION 0.11.1
FROM ubuntu:14.04

RUN mv /usr/bin/ischroot /usr/bin/chroot.orig \
 && ln -s /bin/true /usr/bin/ischroot \
 && export DEBIAN_FRONTEND=noninteractive LANG && apt-get update \
 && apt-get install -y --no-install-recommends language-pack-en \
 && update-locale LANG=en_US.UTF-8 && . /etc/default/locale \
 && apt-get install -y postgresql-9.3

RUN pg_ctlcluster 9.3 main start && pg_ctlcluster 9.3 main stop

CMD ["/bin/bash", "--login"]
