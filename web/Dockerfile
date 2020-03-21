ARG JITSI_REPO=jitsi
FROM ${JITSI_REPO}/base
SHELL ["/bin/bash", "-c"]
RUN \
	apt-dpkg-wrap apt-get update && \
	apt-dpkg-wrap apt-get install -y build-essential cron nginx-extras curl git && \
	apt-dpkg-wrap apt-get install -y -t stretch-backports certbot && \
	cd /usr/share/   && \
	curl -sL https://deb.nodesource.com/setup_10.x | bash - && \
    apt-get install -y nodejs && \
	apt-cleanup && \
	git clone https://github.com/Mooeeezzzz/jitsi-meet.git && \
	cd /usr/share/jitsi-meet/ && \
	npm i  && \
	make all && \
	rm -f /etc/nginx/conf.d/default.conf && \
	rm -f /usr/share/jitsi-meet/interface_config.js

COPY rootfs/ /

EXPOSE 80 443

VOLUME ["/config", "/etc/letsencrypt"]
