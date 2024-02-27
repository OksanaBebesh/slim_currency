FROM composer

FROM php:7.4-fpm

COPY --from=composer /usr/bin/composer /usr/local/bin/composer

RUN apt-get update && apt-get install -y curl git && apt-get install -y libcurl4-openssl-dev
RUN docker-php-ext-install mysqli curl pdo pdo_mysql


RUN apt update

RUN apt-get -y install zip git

COPY ./composer.json /var/www/html/

RUN composer install

COPY local.ini /usr/local/etc/php/php.ini

CMD ["docker-php-entrypoint", "php"]