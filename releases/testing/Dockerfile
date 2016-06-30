FROM coldrye/debian-jetty:9-3-9-testing-latest

MAINTAINER Carsten Klein <trancesilken@gmail.com>

ARG FEATURE_VERSION=
ARG STORAGE_DIR=
ARG DEPLOY_DIR=

RUN test -z "$FEATURE_VERSION" && echo "FEATURE_VERSION missing" && exit 1 || true
RUN test -z "$STORAGE_DIR" && echo "STORAGE_DIR missing" && exit 1 || true
RUN test -z "$DEPLOY_DIR" && echo "DEPLOY_DIR missing" && exit 1 || true

VOLUME ["/var/storages/maven"]

RUN set -x \
    && export ARCHIVA_NAME=apache-archiva-${FEATURE_VERSION} \
    && curl -fSl "http://www-eu.apache.org/dist/archiva/${FEATURE_VERSION}/binaries/${ARCHIVA_NAME}.war" -o ${DEPLOY_DIR}/webapps/archiva.war \
    && mkdir -p ${STORAGE_DIR} \
    && mkdir ${STORAGE_DIR}/data \
    && mkdir ${STORAGE_DIR}/conf \
    && mkdir ${STORAGE_DIR}/temp \
    && mkdir ${STORAGE_DIR}/repositories

ADD ["./etc/default/jetty", "/etc/default/"]
ADD ["./conf/${FEATURE_VERSION}/archiva.xml", "${DEPLOY_DIR}/webapps/"]
ADD ["./conf/${FEATURE_VERSION}/conf/*", "${STORAGE_DIR}/conf/"]
ADD ["./lib/${FEATURE_VERSION}/*.jar", "${DEPLOY_DIR}/ext/"]

