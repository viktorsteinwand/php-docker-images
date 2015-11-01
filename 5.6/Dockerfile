FROM php:5.6-fpm

RUN apt-get update -qq && \
    apt-get -qqy install php5-mysql

COPY php.ini /usr/local/etc/php/php.ini
COPY php-fpm.conf /usr/local/etc/

RUN mkdir /var/log/php-fpm && \
    touch /var/log/php-fpm/access.log && \
    touch /var/log/php-fpm/error.log && \
    chown -R www-data:www-data /var/log/php-fpm
