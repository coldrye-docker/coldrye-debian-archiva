# vim: noexpandtab:ts=4:sw=4

provider = coldrye
os = debian
release = testing
feature = archiva
feature_version = 2.2.1
tag := $(shell date +"%Y%m%d%H%M%S")
image = $(os)-$(feature)
storage_dir = /var/storages/maven
deploy_dir = /var/lib/jetty

include ../../Makefile.war.in

