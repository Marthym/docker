# Megadrive Emulator Gens/GS
This docker contain a gens installed inside.

The docker use ssh forwarding for display Gens window so we have no sound.
A VOLUME is share in `/home/gens/roms` and the port 22 is exposed.

User **gens** is accessible through ssh with login and password :
	
	gens / gens

## Build 

	docker build -t marthym/gens:2.16.7 gens/

## Run

	docker run -d -p 22 -v /host/roms/directory:/home/gens/roms marthym/gens:2.16.7

## Use

	docker port <container> 22
	0.0.0.0:49156
	ssh gens@127.0.0.1 -X -p 49156
	gens

