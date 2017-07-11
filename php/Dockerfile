FROM ubuntu

RUN \
	apt-get update -y && \
	apt-get install -y php7.0 git wget

VOLUME ["/var/www/html"]
EXPOSE 9000

RUN \
        wget https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64.deb && \
        dpkg -i dumb-init_*.deb

COPY conf/php.ini /etc/php/7.0/lib/php.ini
COPY conf/www.conf /etc/php/7.0/fpm/pool.d/www.conf
COPY conf/php-fpm.conf /etc/php/7.0/fpm/php-fpm.conf

ENTRYPOINT ["/usr/bin/dumb-init", "--"]
CMD /usr/sbin/php-fpm7.0 --nodaemonize
