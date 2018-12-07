FROM aminkt/yii2-php-fpm:7.2

MAINTAINER Amin Keshavarz <ak_1596@yahoo.com>



# Install dependency packages
RUN apt-get update && apt-get install -yq --no-install-recommends \
    php7.2-mongodb && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install mongodb driver
RUN pecl install mongodb
#RUN echo "extension=mongodb.so" >> /etc/php/7.2/fpm/php.ini
#RUN echo "extension=mongodb.so" >> /etc/php/7.2/cli/php.ini