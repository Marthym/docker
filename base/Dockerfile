FROM debian:jessie
MAINTAINER marthym@github.com

# Tweak APT
RUN sed -i 's/http.debian.net/ftp.fr.debian.org/g' /etc/apt/sources.list && \
	echo "force-unsafe-io" > /etc/dpkg/dpkg.cfg.d/02apt-speedup && \
	echo "Acquire::http {No-Cache=True;};" > /etc/apt/apt.conf.d/no-cache && \
	echo "APT::Install-Recommends \"0\";" >> /etc/apt/apt.conf.d/99_norecommends && \
	echo "APT::Install-Suggests \"0\";" >> /etc/apt/apt.conf.d/99_norecommends && \
	echo "deb http://ftp.fr.debian.org/debian/ wheezy main contrib non-free" >> /etc/apt/sources.list.d/wheezy.list && \
	echo "deb http://ftp.fr.debian.org/debian/ jessie contrib non-free" >> /etc/apt/sources.list.d/jessie-non-free.list
	
	
# Update dependency
RUN export DEBIAN_FRONTEND=noninteractive && \
	apt-get -y update && \ 
	apt-get -y install runit wget vim-tiny

RUN rm -Rf /etc/sv/*

RUN echo alias ll=\'ls $LS_OPTIONS -l\' >> .bashrc && \
	echo alias ll=\'ls $LS_OPTIONS -l\' >> /etc/skel/.bashrc && \
	echo alias ll=\'ls $LS_OPTIONS -l\' >> /root/.bashrc

CMD /usr/bin/runsvdir -P /etc/sv

# Clean up APT when done.
RUN apt-get clean && \
	apt-get autoclean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
