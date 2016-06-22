FROM coldrye/debian-jetty:9-testing-latest

MAINTAINER Carsten Klein <trancesilken@gmail.com>

ARG ARCHIVA_VERSION=2.2.1

ENV ARCHIVA_NAME=apache-archiva-${ARCHIVA_VERSION}

RUN set -x \
    && export ARCHIVA_TMP=$(mktemp -d) \
    && curl -fSl "http://www-eu.apache.org/dist/archiva/${ARCHIVA_VERSION}/binaries/${ARCHIVA_NAME}-bin.tar.gz" -o ${ARCHIVA_TMP}/${ARCHIVA_NAME}-bin.tar.gz \
    && tar xzf ${ARCHIVA_TMP}/${ARCHIVA_NAME}-bin.tar.gz -C ${ARCHIVA_TMP}/ \
    && mv /${ARCHIVA_TMP}/${ARCHIVA_NAME} /var/archiva \
    && rm -Rf ${ARCHIVA_TMP}

EXPOSE 8080

CMD ["/var/archiva/bin/archiva", "console"]

