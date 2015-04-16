FROM tutum/apache-php

ENV TIMEZONE Europe/Paris
ENV MEMORY_LIMIT 256M
ENV MAX_EXECUTION_TIME 180

RUN apt-get update && apt-get -yq install \
        php5-json \
	libapache2-mod-php5 \
	php5 \
	php-apc \
	php5-intl \
	php5-xsl \
	php5-common \
	php5-gd \
	php5-curl \
	php5-dev \
	php5-idn \
	php-pear \
	php5-imagick \
	php5-imap \
	php5-mcrypt \
	php5-memcache \
	php5-mhash \
	php5-ming \
	php5-mysql \
	php5-ps \
	php5-pspell \
	php5-recode \
	php5-snmp \
	php5-sqlite \
	php5-tidy \
	php5-xmlrpc \
	php5-xsl \
	php5-cli \
	imagemagick \
	php5-pgsql

RUN php5dismod snmp
RUN a2enmod ssl
RUN a2enmod rewrite
RUN a2enmod suexec
RUN a2enmod include

# Set timezone
RUN sed -i "s@^;date.timezone =.*@date.timezone = $TIMEZONE@" /etc/php5/*/php.ini

# Set memory limit
RUN sed -i "s@^memory_limit =.*@memory_limit = $MEMORY_LIMIT@" /etc/php5/*/php.ini

# Set Max execution time
RUN sed -i "s@^max_execution_time = .*@max_execution_time = $MAX_EXECUTION_TIME@" /etc/php5/*/php.ini

# Adding vhost conf to apache
RUN service apache2 stop
ADD vhost.conf /etc/apache2/sites-enabled/
RUN service apache2 start
