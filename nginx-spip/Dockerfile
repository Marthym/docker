FROM marthym/base:latest

RUN dpkg --add-architecture i386 && \
	export DEBIAN_FRONTEND=noninteractive && \
	apt-get -y update && \
	apt-get -y install nginx mysql-server php5-fpm php5-mysql unzip && \
    apt-get clean && \
    apt-get autoclean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \

    echo "\ndaemon off;" >> /etc/nginx/nginx.conf

VOLUME ["/etc/nginx/certs", "/var/log/nginx"]

ADD services /etc/sv

# Install SPIP
RUN wget http://files.spip.org/spip/stable/spip-3.0.zip && \
	unzip spip-3.0.zip && \
	chown -R www-data:www-data spip && \
	chmod -R 550 spip && \
	mkdir -p spip/plugins/auto && \
	chmod -R 750 spip/IMG/ spip/tmp/ spip/local/ spip/plugins/auto/ && \
	mv spip /var/www/ && \
	rm -rf spip

# Expose ports.
EXPOSE 80
EXPOSE 443
