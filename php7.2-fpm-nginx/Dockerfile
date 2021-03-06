FROM ubuntu:18.04

MAINTAINER Amin Keshavarz <ak_1596@yahoo.com>

ENV DEBIAN_FRONTEND=noninteractive


# Install dependency packages
RUN apt-get update && apt-get install -yq --no-install-recommends \
    apt-utils \
    git \
    zip unzip php7.2-zip \
    curl \
    ca-certificates \
    build-essential \
    apt-utils \
    php7.2-fpm php7.2-common php-pear php7.2-dev \
    php7.2-mysql \
    php7.2-intl \
    php7.2-curl \
    php7.2-gd \
    php7.2-mbstring \
    nginx && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set php7.2-fpm listen to port 9000
RUN sed -i "s|;*listen\s*=\s*/run/php/php7.2-fpm.sock|listen = 9000|g" /etc/php/7.2/fpm/pool.d/www.conf && \
    sed -i "s|;*listen\s*=\s*/||g" /etc/php/7.2/fpm/php-fpm.conf

# Add working directory and copy files into that.
WORKDIR /app

# Start application installation by composer update command.
RUN composer global require fxp/composer-asset-plugin


ENTRYPOINT  service php7.2-fpm start && service nginx start && /bin/bash

# Define mountable directories.
VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx"]

# Expose ports.
EXPOSE 80
EXPOSE 443