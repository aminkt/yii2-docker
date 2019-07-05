FROM alpine

MAINTAINER Amin Keshavarz <ak_1596@yahoo.com>

ENV PHP_INI_DIR /usr/local/etc/php
ENV PHP_VERSION 7.3.6

# persistent / runtime deps
RUN apk update && apk add --no-cache \
		ca-certificates \
		bash \
		curl \
		tar \
		xz \
		openrc \
#		nginx \
        # https://github.com/docker-library/php/issues/494
		openssl \
		zip unzip \
		git

# Install dependency packages
RUN apk add --no-cache \
        php7 \
        php7-fpm \
        php7-opcache \
        php7-fpm \
        php7-zlib \
        php7-mysqli \
        php7-intl \
        php7-curl \
        php7-gd \
        php7-mbstring \
        php7-json \
        php7-phar \
        php7-zip && \
        rm -rf /var/cache/apk/*

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set php7.2-fpm listen to port 9000
#RUN sed -i "s|;*listen\s*=\s*/run/php/php7.2-fpm.sock|listen = 9000|g" /etc/php/7.2/fpm/pool.d/www.conf && \
#    sed -i "s|;*listen\s*=\s*/||g" /etc/php/7.2/fpm/php-fpm.conf

# Add working directory and copy files into that.
#WORKDIR /app

# Start application installation by composer update command.
#RUN composer global require fxp/composer-asset-plugin

#RUN rc-update add nginx default
RUN rc-update add php-fpm7 default && rc-service php-fpm7 restart

#ENTRYPOINT   && /bin/bash

# Define mountable directories.
#VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx"]

# Expose ports.
#EXPOSE 80
#EXPOSE 443