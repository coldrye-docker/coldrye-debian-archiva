# coldrye-debian-archiva

[![coldrye/debian-archiva](http://dockeri.co/image/coldrye/debian-archiva)](https://hub.docker.com/r/coldrye/debian-archiva/)


## Description

This provides Apache Archiva as a containerized service based on coldrye/debian-jetty.


## Image Releases

Images are released for the following debian releases.

- jessie
- testing (stretch)

See https://hub.docker.com/r/coldrye/debian-archiva/tags/ for a complete list.


## Usage

While you can use this as it is and have a working Apache Archiva installation, one might consider that
existing data needs to be stored on a persistent volume.

The persistent volume must be mounted inside the container on ``/var/storages/archiva`` and must have the following layout

```
conf/    // one must copy the configuration files from conf/<VERSION>/* on first installment
data/
groups/
logs/
repositories/
```

After which the container can be created using

```
docker create -P -v ./archiva:/var/storages/archiva coldrye/debian-archiva:2-1-1-<jessie|testing>-latest
```


## TODO

- import remote repository certs into configured keystore
openssl s_client -connect repo.maven.apache.org:443 -showcerts </dev/null 2>/dev/null|openssl x509 -outform der >repo-maven-apache-org.der
keytool -importcert -storepass <secret> -alias repo-maven-apache-org -noprompt -trustcacerts -file /var/archiva/logs/repo-maven-apache-org.der

http://stackoverflow.com/questions/5871279/java-ssl-and-cert-keystore

- optional: extend apache/archiva to permit import of remote repository certificates into configured keystore via web interface or make a feature request

