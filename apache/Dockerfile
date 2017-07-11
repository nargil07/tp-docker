FROM ubuntu
VOLUME ["/var/www/html"]
RUN \
	apt-get update -y && \
	apt-get install -y --no-install-recommends apache2 libapache2-mod-fastcgi wget

RUN \
	wget --no-check-certificate https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64.deb && \
        dpkg -i dumb-init_*.deb

COPY 000-default.conf /etc/apache2/sites-available/000-default.conf
RUN a2enmod proxy_fcgi

ENTRYPOINT ["/usr/bin/dumb-init", "--"]
CMD /usr/sbin/apache2ctl -D FOREGROUND

