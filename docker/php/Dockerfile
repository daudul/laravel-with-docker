FROM php:8.0-fpm

RUN apt-get update -y
RUN apt-get install -y unzip libpq-dev libcurl4-gnutls-dev
RUN docker-php-ext-install pdo pdo_mysql bcmath

RUN pecl install -o -f redis \
    && rm -rf /tmp/pear \
    && docker-php-ext-enable redis

#WORKDIR /var/www/html

COPY --from=composer:2.3.5 /usr/bin/composer /usr/bin/composer

#php ini file configuration
COPY ./docker/php/conf.d/custom.ini /usr/local/etc/php/conf.d/custom.ini

ENV PORT=8000
#ENTRYPOINT [ "docker/entrypoint.sh" ]