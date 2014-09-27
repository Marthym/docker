# Base image

just a base image for other dockers base on debian:jessie

## Contain

 * Some APT tweak
 * Vim for file edition
 * wget for file download
 * runit for service managment

## Build

	docker build -t marthym/base:jessie base/
	
