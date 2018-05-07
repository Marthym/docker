# Base image

just a base image for other dockers base on debian:testing-slim

## Contain

 * Some APT tweak
 * Vim for file edition
 * wget for file download
 * runit for service managment

## Build

	docker build -t marthym/base:1.3.0 base/
	
## Changelog

### 2018-05-07

 * Upgrade debian
 * Replace wget with curl

### 2015-01-03

 * Remove alias ll to reduce layers
 * Fix the CMD to avoid timeout wait when stopping the container
