# DOCKER-VERSION 0.11.1
# TO tinyerp/debian-postgresql:9.4
FROM debian:jessie

MAINTAINER Florent Xicluna, @florentxicluna

# PostgreSQL 9.4 beta1 on Debian/Ubuntu
#   http://www.postgresql.org/about/news/1524/

# Install PostgreSQL and Dropbear (SSH server)
# Untar configuration "/etc/supervisor/conf.d/"
RUN echo deb http://http.debian.net/debian jessie main contrib non-free \
    > /etc/apt/sources.list.d/debian-jessie.list \
 && echo deb http://http.debian.net/debian experimental main contrib \
    > /etc/apt/sources.list.d/debian-experimental.list \
 && /bin/rm /etc/apt/sources.list && echo en_US.UTF-8 UTF-8 > /etc/locale.gen \
 && export DEBIAN_FRONTEND=noninteractive LANG && apt-get update \
 && apt-get install -y --no-install-recommends apt-utils dropbear locales \
    logrotate supervisor && echo "root:password" | chpasswd \
 && update-locale LANG=en_US.UTF-8 && . /etc/default/locale \
 && apt-get install -yt experimental postgresql-9.4 postgresql-contrib-9.4 \
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
