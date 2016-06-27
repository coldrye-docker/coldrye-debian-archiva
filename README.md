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

The persistent volume must be mounted inside the container on ``/var/storages/maven`` and must have the following layout

```
conf/    // one must copy the configuration files from conf/<VERSION>/* on first installment
data/
groups/
logs/
repositories/
cacerts  // copy over the keystore from /usr/lib/jvm/.../jre/lib/security/cacerts
```

After which the container can be created using

```
docker create -P -v ./maven:/var/storages/maven coldrye/debian-archiva:2-1-1-<jessie|testing>-latest
```

