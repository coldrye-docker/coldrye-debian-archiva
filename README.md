
# coldrye-debian-archiva

See https://hub.docker.com/r/coldrye/debian-archiva/ for more information.


## Description

This provides apache-archiva as a containerized service.


## Image Releases

Images are released for the following debian releases.

- jessie
- testing (stretch)

See https://hub.docker.com/r/coldrye/debian-archiva/tags/ for a complete list.


## TODO

Currently just packages apache-archiva-bin and uses the bundled jetty.
Need to deploy the war instead and use the jetty version that comes with
the base image.

Configuration:

- repository storage / volume
- default users
- default repositories local / remote
- import remote repository certs into keystore /etc/ssl/certs/java/cacerts
    openssl s_client -connect repo.maven.apache.org:443 -showcerts </dev/null 2>/dev/null|openssl x509 -outform der >repo-maven-apache-org.der
    keytool -importcert -storepass <secret> -alias repo-maven-apache-org -noprompt -trustcacerts -file /var/archiva/logs/repo-maven-apache-org.der
- ...

