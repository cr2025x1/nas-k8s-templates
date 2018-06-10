FROM php:fpm-alpine

RUN set -ex \
	&& apk --no-cache add \
           diffutils \
           postgresql-libs postgresql-dev \
           freetype libpng libjpeg-turbo freetype-dev libpng-dev libjpeg-turbo-dev \
           pcre-dev \
           icu-dev \
           g++ make autoconf \
           libmemcached-dev zlib-dev \
        && docker-php-ext-configure gd \
           --with-gd \
           --with-freetype-dir=/usr/include/ \
           --with-png-dir=/usr/include/ \
           --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install pgsql gd opcache \
	&& pecl install intl \
	&& pecl install apcu \
	&& pecl install memcached \
	&& docker-php-ext-enable intl apcu memcached \
	&& apk del \
           postgresql-dev \
           freetype-dev libpng-dev libjpeg-turbo-dev \
           pcre-dev \
           icu-dev \
           libmemcached-dev zlib-dev

VOLUME /var/www/html
