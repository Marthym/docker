FROM debian:testing-slim
MAINTAINER marthym@github.com

# Tweak APT
RUN sed -i 's/main/main contrib non-free/g' /etc/apt/sources.list && \
	echo "force-unsafe-io" > /etc/dpkg/dpkg.cfg.d/02apt-speedup && \
	echo "Acquire::http {No-Cache=True;};" > /etc/apt/apt.conf.d/no-cache && \
	echo "APT::Install-Recommends \"0\";" >> /etc/apt/apt.conf.d/99_norecommends && \
	echo "APT::Install-Suggests \"0\";" >> /etc/apt/apt.conf.d/99_norecommends
	
	
RUN touch /etc/inittab

# Update dependency
RUN export DEBIAN_FRONTEND=noninteractive && \
	apt-get -y update && \ 
	apt-get -y install runit wget vim-tiny procps && \
	apt-get clean && \
	apt-get autoclean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Remove installed runit services
RUN rm -Rf /etc/sv/*

CMD ["/usr/bin/runsvdir", "-P", "/etc/sv"]
