# viktorsteinwand/php

This repository contains PHP docker images for Symfony2 or Symfony3 applications.

## Using this image with docker-compose

Add these lines to your `docker-compose.yml` to use this image:  

```yml
php-fpm:
  image: viktorsteinwand/php:7.1-fpm-symfony
  volumes:
    - /path/to/php-project:/var/www/html
```

## Development environment

The extention `xdebug` and `phpunit` are installed in the Dockerfile for development only. In development environment please use `viktorsteinwand/php:7.1-fpm-symfony-dev`:  

```yml
php-fpm:
  image: viktorsteinwand/php:7.1-fpm-symfony-dev
  volumes:
    - /path/to/php-project:/var/www/html
```

## Blackfire profiler

The extention `blackfire Probe` is installed in the Dockerfile for performance profiling only. Please use `viktorsteinwand/php:7.1-fpm-symfony-blackfire` for such purposes:  

```yml
php-fpm:
  image: viktorsteinwand/php:7.1-fpm-symfony-blackfire
  volumes:
    - /path/to/php-project:/var/www/html
```

Additionally the blackfire service must be added as well to the docker-compose file:

```
blackfire:
  image: blackfire/blackfire
  environment:
    - BLACKFIRE_SERVER_ID=<your-blackfire-server-id>
    - BLACKFIRE_SERVER_TOKEN=<your-blackfire-server-token>
```

For further information see [https://blackfire.io/docs/up-and-running/installation](https://blackfire.io/docs/up-and-running/installation)
