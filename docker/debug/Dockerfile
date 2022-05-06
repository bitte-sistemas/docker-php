# syntax=docker/dockerfile:1.3-labs

FROM php:7.4-apache

RUN apt update

RUN apt install -y libzip-dev zip && \ 
    docker-php-ext-install zip pdo pdo_mysql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN a2enmod rewrite

RUN pecl install xdebug && docker-php-ext-enable xdebug

COPY <<EOF /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
zend_extension=xdebug

[xdebug]
xdebug.mode=develop,debug
xdebug.discover_client_host=1
xdebug.client_port = 9003
xdebug.start_with_request=yes
EOF