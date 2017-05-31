FROM php:7.1-fpm
MAINTAINER gaopeng<gaopeng@lekee.cc>

RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev libfreetype6-dev \
  && apt-get install zip unzip \
  && rm -rf /var/lib/apt/lists/* \
  && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
  && docker-php-ext-install gd \
  && docker-php-ext-install pdo_mysql \
  && docker-php-ext-install zip \
  && docker-php-ext-install opcache

COPY ./config/php.ini /usr/local/etc/php/conf.d/
COPY ./config/opcache-recommended.ini /usr/local/etc/php/conf.d/
