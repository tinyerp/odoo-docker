# DOCKER-VERSION 1.2.0
# TO tinyerp/ubuntu-openerp:7.0
FROM tinyerp/ubuntu-postgresql:9.3

# Install "openerp.deb"
# Create PostgreSQL user "openerp"
# Untar configuration "/etc/supervisor/conf.d/openerp.conf"
RUN echo deb http://nightly.odoo.com/7.0/nightly/deb/ ./ \
    > /etc/apt/sources.list.d/openerp-70.list \
 && export DEBIAN_FRONTEND=noninteractive LANG=en_US.UTF-8 \
 && apt-get update && apt-get install -y --allow-unauthenticated openerp \
 && mkdir ~openerp && chown openerp:openerp ~openerp \
 && service postgresql start && su - postgres -c "createuser -d openerp" \
 && echo H4sIACx6i1MCA+3SwUrDQBAG4JzzFHkA66ZN2oLQg4eiB7WgeBIpMZnWQLMTZnfz/E5j \
 Ipi7YOH/Lsv8P1kysNySJWmvS7aH6I+kapXn/ammZ5pnaTRfZPlitc7Xy2WUztNM6yS6JNPlLsRb \
 K3yUornh74fwHpfcNIWtkk1ighPzUVszdDNH0pEkszIx5MsxntT9U4qDDnrFUMVku1rYNmS9pq8v \
 2+fNUF097O6ebh+3P/P9TgfzyQ2NF8dF8Ox8IedvvQTqA6FfkVBVC5V+73xFImOsEwe/P/HxUJ/o \
 vFRXiNHRuNDq/9aOZbqAtnEEAAAAAAAAAAAAAAAAAAAAAADwz30BmbMKRgAoAAA=             \
  | base64 -di | tar xz -C /etc/supervisor/conf.d

# Declare volumes for data
VOLUME ["/var/lib/openerp", "/var/lib/postgresql"]

# Expose HTTP port
EXPOSE 8069
