FROM php:7.0-fpm

# Install tools required to enable installing extensions
RUN apt-get update \
    && apt-get install -y zlib1g-dev libicu-dev g++ wget \
    && apt-get purge -y --auto-remove

# Install extensions required by Symfony
RUN /usr/local/bin/docker-php-ext-install \
    intl \
    opcache \
    pdo_mysql \
    mysqli \
    mbstring \
    hash \
    bcmath \
    json \
    zip

# Install xdebug
RUN mkdir -p /usr/local/lib/php/extensions/ \
    && cd /usr/local/lib/php/extensions/ \
    && wget https://xdebug.org/files/xdebug-2.4.0.tgz \
    && tar -xzf xdebug-2.4.0.tgz \
    && cd xdebug-2.4.0 && phpize && ./configure --enable-xdebug && make \
    && rm -f /usr/local/lib/php/extensions/xdebug-2.4.0.tgz \
    && apt-get purge -y --auto-remove

# Install phpunit
RUN cd /usr/local/bin/ \
    && wget https://phar.phpunit.de/phpunit.phar \
    && mv phpunit.phar phpunit \
    && chmod +x phpunit

COPY php.ini /usr/local/etc/php/php.ini
COPY xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
