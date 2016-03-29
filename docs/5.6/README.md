# viktorsteinwand/php

This repository contains PHP-FPM 5.6 docker image for Symfony2 applications.

## Using this image with docker-compose

Add these lines to your `docker-compose.yml` to use this image:  

```yml
php-fpm:
  image: viktorsteinwand/php:5.6-fpm-symfony
  volumes:
    - /path/to/php-project:/var/www/html
    - /path/to/logfiles/php-fpm:/var/log/php-fpm
```

## How to enable xdebug in dev environment

The extention `xdebug` is installed, but is disabled by default due to performance if using this image in production environment. To turn xdebug within the development environment perform following steps:  

1. Create new `xdebug.ini` file with content like described below:  

```ini
zend_extension="/usr/lib/php5/20131226/xdebug.so"

xdebug.default_enable=1
xdebug.remote_enable=1
xdebug.remote_handler=dbgp
; This is the default Docker gateway
xdebug.remote_host=172.17.42.1
xdebug.remote_port=9000
xdebug.remote_autostart=1
xdebug.remote_connect_back=1

; Recursion protection
xdebug.max_nesting_level = 250

; display config
xdebug.cli_color=1
xdebug.var_display_max_depth=10

```

2. Map newly created `xdebug.ini` file to the php-fpm `conf.d` folder location:  

```yml
php-fpm:
  ...
  volumes:
    ...
    - /path/to/xdebug.ini:/usr/local/etc/php/conf.d/xdebug.ini
```
