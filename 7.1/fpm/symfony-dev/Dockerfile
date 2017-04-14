FROM viktorsteinwand/php:7.1-fpm-symfony

# Install xdebug
RUN mkdir -p /usr/local/lib/php/extensions/ \
    && cd /usr/local/lib/php/extensions/ \
    && wget https://xdebug.org/files/xdebug-2.5.1.tgz \
    && tar -xzf xdebug-2.5.1.tgz \
    && cd xdebug-2.5.1 && phpize && ./configure --enable-xdebug && make \
    && rm -f /usr/local/lib/php/extensions/xdebug-2.5.1.tgz \
    && apt-get purge -y --auto-remove

# Install phpunit
RUN cd /usr/local/bin/ \
    && wget https://phar.phpunit.de/phpunit.phar \
    && mv phpunit.phar phpunit \
    && chmod +x phpunit

COPY xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
