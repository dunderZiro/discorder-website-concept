FROM php:7.4-fpm-alpine as builder

ARG WORDPRESS_VERSION="6.0.2"
ARG WORDPRESS_USER="wp"

# Timezone for correct logs
ENV TZ Europe/London

# Use the default production configuration
RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

RUN docker-php-ext-install mysqli pdo pdo_mysql && docker-php-ext-enable pdo_mysql

WORKDIR /var/www/html

RUN wget https://en-gb.wordpress.org/wordpress-$WORDPRESS_VERSION-en_GB.tar.gz
RUN tar -xvf wordpress-$WORDPRESS_VERSION-en_GB.tar.gz
RUN rm wordpress-$WORDPRESS_VERSION-en_GB.tar.gz

ADD ./Docker/php-fpm/www.conf /usr/local/etc/php-fpm.d/www.conf
RUN addgroup -g 1000 $WORDPRESS_USER && adduser -G $WORDPRESS_USER -g $WORDPRESS_USER -s /bin/sh -D $WORDPRESS_USER
RUN chown -R $WORDPRESS_USER:$WORDPRESS_USER /var/www/html/wordpress

USER $WORDPRESS_USER