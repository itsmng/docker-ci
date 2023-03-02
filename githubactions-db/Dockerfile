ARG BASE_IMAGE=mysql:latest

FROM $BASE_IMAGE

LABEL \
  org.opencontainers.image.title="ITSM-NG Github Actions database container" \
  org.opencontainers.image.description="This container is used to run ITSM-NG test suite on Github Actions." \
  org.opencontainers.image.url="https://github.com/itsmng/docker-ci" \
  org.opencontainers.image.source="git@github.com:itsmng/docker-ci"

ARG CONFIG_DIR=/etc/mysql/conf.d
COPY ./files/etc/mysql/conf.d/custom.cnf $CONFIG_DIR/custom.cnf

HEALTHCHECK --interval=10s --retries=5 --timeout=5s \
  CMD mysqladmin ping
