# viktorsteinwand/php

This repository contains PHP docker images for Symfony2 or Symfony3 applications.

## Using this image with docker-compose

Add these lines to your `docker-compose.yml` to use this image:  

```yml
php-fpm:
  image: viktorsteinwand/php:7.0-fpm-symfony
  volumes:
    - /path/to/php-project:/var/www/html
```

## Development environment

The extention `xdebug` and `phpunit` are installed in the dev Dockerfile definitions only. In development environment please use `viktorsteinwand/php:7.0-fpm-symfony-dev` instead:  

```yml
php-fpm:
  image: viktorsteinwand/php:7.0-fpm-symfony-dev
  volumes:
    - /path/to/php-project:/var/www/html
```
