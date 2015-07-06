FROM marthym/base:latest

RUN export DEBIAN_FRONTEND=noninteractive && \
	apt-get -y update && \
	apt-get -y install nginx mysql-server php5-cli php5-fpm php5-mysql unzip && \
  apt-get clean && \
  apt-get autoclean && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \

  echo "\ndaemon off;" >> /etc/nginx/nginx.conf

VOLUME ["/etc/nginx/certs", "/var/log/nginx"]

ADD services /etc/sv

# Install SPIP
ADD conf/spip.conf /etc/nginx/sites-available/spip.conf
RUN wget http://files.spip.org/spip/stable/spip-3.0.zip
RUN unzip spip-3.0.zip && \
	mkdir -p spip/plugins/auto && \
	chown -R www-data:www-data spip && \
	chmod -R 550 spip && \
	chmod -R 750 spip/config/ spip/IMG/ spip/tmp/ spip/local/ spip/plugins/auto/ && \
	mv spip /var/www/ && \
	rm -rf spip && \
	ln -s /etc/nginx/sites-available/spip.conf /etc/nginx/sites-enabled/spip.conf


# Expose ports.
EXPOSE 80 443
