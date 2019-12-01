FROM debian:testing-slim
LABEL maintainer="marthym@ght1pc9kc.fr" \
      version="1.5.0"

# Tweak APT
RUN sed -i 's/main/main contrib non-free/g' /etc/apt/sources.list && \
	echo "force-unsafe-io" > /etc/dpkg/dpkg.cfg.d/02apt-speedup && \
	echo "Acquire::http {No-Cache=True;};" > /etc/apt/apt.conf.d/no-cache && \
	echo "APT::Install-Recommends \"0\";" >> /etc/apt/apt.conf.d/99_norecommends && \
	echo "APT::Install-Suggests \"0\";" >> /etc/apt/apt.conf.d/99_norecommends && \
	echo "deb http://deb.debian.org/debian stable main contrib non-free" >> /etc/apt/sources.list.d/stable.list
	
	
RUN touch /etc/inittab

# Update dependency
RUN export DEBIAN_FRONTEND=noninteractive && \
	apt -y update && \ 
	apt -y install runit curl vim-tiny procps && \
	apt clean && \
	apt autoclean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Remove installed runit services
RUN rm -Rf /etc/sv/*

CMD ["/usr/bin/runsvdir", "-P", "/etc/sv"]
