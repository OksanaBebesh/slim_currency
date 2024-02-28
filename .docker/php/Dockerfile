FROM php:8.1-fpm

WORKDIR  /var/www/html

RUN apt-get update && apt-get install -y curl git && apt-get install -y libcurl4-openssl-dev
RUN docker-php-ext-install mysqli curl pdo pdo_mysql

RUN apt update

RUN apt-get -y install zip

COPY local.ini /usr/local/etc/php/php.ini

COPY ./composer.json /var/www/html/

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

RUN composer self-update

RUN composer install \
    && composer clearcache

RUN composer dump-autoload --optimize

CMD ["docker-php-entrypoint", "php-fpm"]

EXPOSE 9000