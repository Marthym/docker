FROM marthym/java
MAINTAINER marthym@github.com

RUN wget --no-check-certificate "https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.3.2.tar.gz" && \
	mkdir -p /opt/elasticsearch && \
	tar -xf elasticsearch-5.3.2.tar.gz -C /opt/ && \
	mv /opt/elasticsearch-5.3.2 /opt/elasticsearch

# Add services
ADD services /etc/sv
RUN chmod +x /etc/sv/**/run

# add user elastic
RUN useradd elastic --home /home/elastic/ && \
	echo 'elastic:elastic' |chpasswd && \
	mkdir -p /home/elastic/.ssh && \
	chmod 755 /home/elastic/.ssh && \
	chown -Rf elastic. /home/elastic && \
	chown -Rf elastic. /opt/elasticsearch && \
	mkdir -p /home/elastic/roms

EXPOSE 3128