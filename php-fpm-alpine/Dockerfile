FROM alpine

MAINTAINER Amin Keshavarz <ak_1596@yahoo.com>

ENV PHP_INI_DIR /etc/php7
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
        php7-dom \
        php7-xml \
        php7-xmlwriter \
        php7-tokenizer \
        php7-ctype \
        php7-zip && \
        rm -rf /var/cache/apk/*

# ensure www-data user exists
RUN set -eux; \
	addgroup -g 82 -S www-data; \
	adduser -u 82 -D -S -G www-data www-data

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set php7.2-fpm listen to port 9000
#RUN sed -i "s|;*listen\s*=\s*/run/php/php7.2-fpm.sock|listen = 9000|g" $PHP_INI_DIR/php-fpm.d/www.conf && \
#    sed -i "s|;*listen\s*=\s*/||g" $PHP_INI_DIR/php-fpm.conf

VOLUME ["/sys/fs/cgroup", "$PHP_INI_DIR/conf.d", "$PHP_INI_DIR/php-fpm.d"]

RUN rc-update add php-fpm7 default

COPY entrypoint.sh /usr/local/bin/
#ENTRYPOINT  rc-service php-fpm7 restart && /bin/bash
ENTRYPOINT ["entrypoint.sh"]

EXPOSE 9000