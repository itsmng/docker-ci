FROM mysql:latest

ARG CONFIG_DIR=/etc/mysql/conf.d
COPY ./files/etc/mysql/conf.d/custom.cnf $CONFIG_DIR/custom.cnf

HEALTHCHECK --interval=10s --retries=5 --timeout=5s \
  CMD mysqladmin ping
