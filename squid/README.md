# Image Docker for Squid Proxy

FROM debian:jessie

Contain a Squid3 Proxy Cache server in version **3.4**
Build from debian Jessie in order to install 3.4 version of Squid need for store_id_program

 * PORTS : [ `3128` ]
 * VOLUMES : [ `/var/spool/squid3` ]
 * CMD : [`/usr/bin/runsvdir`, `-P`, `/etc/sv`]

## Utilisation

This image is configured to proxify docker images build, **don't use for any other purpose !**

Build : 

    sudo docker build -t marthym/squid:latest ./squid
    sudo docker push marthym/squid:latest


Test : 

    sudo docker run -d -p 3128:3128 -v /data/squid:/var/spool/squid3 marthym/squid:latest

## Changelog

### 2015-02-02

 * Update to Squid 3.4
 * Use store_id_program to de-duplication some download file (Ex: Oracle JRE/JDK)
 * Add store_id_db, a StoreId mapping database

### 2015-01-16

 * Create
