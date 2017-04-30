FROM marthym/java:8u131
MAINTAINER marthym@github.com

RUN wget -qO- --no-check-certificate "https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.3.2.tar.gz" \
	| tar -xzf - -C /opt && \
	mv /opt/elasticsearch-5.3.2 /opt/elasticsearch

RUN wget -qO- --no-check-certificate "https://artifacts.elastic.co/downloads/kibana/kibana-5.3.2-linux-x86_64.tar.gz" \
	| tar -xzf - -C /opt && \
	mv /opt/kibana-5.3.2-linux-x86_64 /opt/kibana && \
	sed -ri "s!^(\#\s*)?(server\.host:).*!\2 '0.0.0.0'!" /opt/kibana/config/kibana.yml

# Add services
ADD services /etc/sv
RUN chmod +x /etc/sv/**/run

# add user elastic
RUN useradd --no-create-home --system elastic && \
	chown -Rf elastic. /opt/elasticsearch && \
	chown -Rf elastic. /opt/kibana

EXPOSE 9200 
EXPOSE 5601
