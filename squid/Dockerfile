FROM debian:jessie

RUN echo "force-unsafe-io" > /etc/dpkg/dpkg.cfg.d/02apt-speedup && \
	echo "Acquire::http {No-Cache=True;};" > /etc/apt/apt.conf.d/no-cache && \
    echo "APT::Install-Recommends \"0\";" > /etc/apt/apt.conf.d/no-recommends && \
	echo "APT::Install-Suggests \"0\";" >> /etc/apt/apt.conf.d/no-recommends && \
	echo "Dpkg::Options { \"--force-confdef\"; \"--force-confold\"; }" >> /etc/apt/apt.conf.d/local && \

    export DEBIAN_FRONTEND="noninteractive" && \
    echo "deb http://ftp.fr.debian.org/debian/ unstable main contrib non-free" >> /etc/apt/sources.list.d/unstable.list && \
    apt-get -y update && \
    apt-get -q -y -t unstable install runit vim squid3

ADD conf/ /

CMD ["/usr/bin/runsvdir", "-P", "/etc/sv"]

EXPOSE 3128
VOLUME ["/var/spool/squid3"]
