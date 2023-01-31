ARG BASE_IMAGE=alpine

FROM $BASE_IMAGE

LABEL \
  org.opencontainers.image.title="ITSM-NG Github Actions OpenLDAP container" \
  org.opencontainers.image.description="This container is used to run ITSM-NG test suite on Github Actions." \
  org.opencontainers.image.url="https://github.com/itsmng/docker-ci" \
  org.opencontainers.image.source="git@github.com:itsmng/docker-ci"

RUN \
  # Update APK package list.
  apk update \
  \
  # Install openldap.
  && apk add openldap openldap-clients \
  \
  # Clean sources list.
  && rm -rf /var/cache/apk/*

COPY ./files/etc/openldap/slapd.conf /etc/openldap/slapd.conf

HEALTHCHECK --interval=10s --retries=5 --timeout=5s \
  CMD ldapwhoami  -x -H ldap://127.0.0.1:3890/ -D "cn=Manager,dc=itsm,dc=org" -w insecure || exit 1

CMD ["slapd", "-d", "32768", "-h", "ldap://0.0.0.0:3890/"]
 
