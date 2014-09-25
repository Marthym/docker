# Image bind9

A docker image for build a little DNS server

## Exposes & Volumes

	EXPOSE 53 # DNS Server

## Usage
### Build
	
	# docker build -t marthym/bind9 bind9/
	
### Run

	# docker run -d -p 53:53/udp -p 53:53 marthym/bind9
