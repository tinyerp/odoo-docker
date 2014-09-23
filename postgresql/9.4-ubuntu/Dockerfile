# DOCKER-VERSION 1.2.0
# TO tinyerp/ubuntu-postgresql:9.4
FROM ubuntu:14.04

MAINTAINER Florent Xicluna, @florentxicluna

# Install PostgreSQL and Dropbear (SSH server)
# Untar configuration "/etc/supervisor/conf.d/"
RUN apt-key adv --keyserver pool.sks-keyservers.net \
    --recv-keys B97B0AFCAA1A47F044F244A07FCC7D46ACCC4CF8 \
 && /bin/mv /etc/apt/sources.list /etc/apt/sources.list.d/ubuntu.list \
 && echo deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main 9.4 \
    > /etc/apt/sources.list.d/pgdg.list \
 && mv /usr/bin/ischroot /usr/bin/chroot.orig \
 && ln -s /bin/true /usr/bin/ischroot \
 && export DEBIAN_FRONTEND=noninteractive LANG && apt-get update \
 && apt-get install -y --no-install-recommends dropbear language-pack-en \
    rsync supervisor && echo "root:password" | chpasswd \
 && update-locale LANG=en_US.UTF-8 && . /etc/default/locale \
 && apt-get install -y postgresql-9.4 postgresql-contrib-9.4 \
 && echo H4sIADcyi1MCA+3UXWqEMBAHcJ89hRdYEzUILexbb1GK+JGVgBp3kiz09o12Xbu20Iey \
 BeH/ewmZBAfJzDSkx0qWFNd6OAWPwb1ciHn1tivPeBokaSbSPBEizQKecMHzIAr2ZPtzO/E6km6p \
 7J+bayG8hbXu+3JoomPEpK3ZcsDIDWGjSNZW0/v2NHRGkg+S1jYsndXGlmR9wJKTc4DkXYjk57cK \
 YxtJtIT9TjtbdLo9qU5OWS4+td8y40ZJF2U03ZLGPh4G8Aejf6jWP825e9wE+K3/RZat/T/dSxLu \
 xwD6/z/7fy2EuwngjO8+VbH1mD3FglVquIWiw8u1S7/f60s1RIc6mmpLtcXU08d5bvxwj21qcRkp \
 S/jhY+VLfgwWAAAAAAAAAAAAAAAAAAAA2I0Pl2OMiAAoAAA=                             \
  | base64 -di | tar xz -C /etc/supervisor/conf.d

# Declare volume for log files
VOLUME ["/var/log/supervisor"]

# Autostart supervisor daemon
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
