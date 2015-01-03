# Base image

just a base image for other dockers base on debian:jessie

## Contain

 * Some APT tweak
 * Vim for file edition
 * wget for file download
 * runit for service managment

## Build

	docker build -t marthym/base:jessie base/
	
## Changelog

### 2015-01-03

 * Remove alias ll to reduce layers
 * Fix the CMD to avoid timeout wait when stopping the container

