FROM marthym/base:1.3.0

RUN export DEBIAN_FRONTEND=noninteractive && \
	apt -y update && \ 
	apt -y install build-essential hugo && \
	apt clean && \
	apt autoclean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN curl -o /tmp/node-10.0.0-linux-x64.tar.xz "http://nodejs.org/dist/v10.0.0/node-v10.0.0-linux-x64.tar.xz" && \
	tar -C /opt -Jxf /tmp/node-10.0.0-linux-x64.tar.xz && \
	mv /opt/node-v10.0.0-linux-x64 /opt/nodejs && \
	ln -s /opt/nodejs/bin/node /usr/local/bin/node && \
	ln -s /opt/nodejs/bin/npm /usr/local/bin/npm && \
	rm -rf /tmp/node-10.0.0-linux-x64.tar.xz

RUN npm -g install gulp && \
	ln -s /opt/nodejs/bin/gulp /usr/local/bin/gulp
