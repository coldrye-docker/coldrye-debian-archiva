FROM coldrye/debian-jetty:9-testing-latest

MAINTAINER Carsten Klein <trancesilken@gmail.com>

ARG ARCHIVA_VERSION=2.2.1

ENV DEPLOY_DIR=/var/lib/jetty
ENV ARCHIVA_STORE=/var/storages/maven
RUN set -x \
    && export ARCHIVA_NAME=apache-archiva-${ARCHIVA_VERSION} \
    && curl -fSl "http://www-eu.apache.org/dist/archiva/${ARCHIVA_VERSION}/binaries/${ARCHIVA_NAME}.war" -o ${DEPLOY_DIR}/webapps/archiva.war \
    && mkdir -p ${ARCHIVA_STORE} \
    && mkdir ${ARCHIVA_STORE}/data \
    && mkdir ${ARCHIVA_STORE}/conf \
    && mkdir ${ARCHIVA_STORE}/temp \
    && mkdir ${ARCHIVA_STORE}/repositories

ADD ["./etc/default/jetty.extra", "/etc/default/"]
ADD ["./conf/${ARCHIVA_VERSION}/archiva.xml", "${DEPLOY_DIR}/webapps/"]
ADD ["./conf/${ARCHIVA_VERSION}/conf/*", "${ARCHIVA_STORE}/conf/"]
ADD ["./lib/${ARCHIVA_VERSION}/*.jar", "${DEPLOY_DIR}/ext/"]

VOLUME ["/var/storages/maven"]

EXPOSE 8080

