FROM php:8.0-cli-alpine

RUN apk update && apk upgrade && apk add --no-cache bash

RUN apk --no-cache add --virtual .build-dependencies \
        autoconf \
        g++ \
        make \
        libzip-dev \
        zip \
    && docker-php-ext-install zip \
    && pecl install xdebug-3.0.0 \
    && docker-php-ext-enable xdebug

## We are using an older version of xdebug as we need PHP 8.0 due to vendor packages constraints (managed with composer)

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
COPY xdebug.ini ${PHP_INI_DIR}/conf.d/xdebug.ini

VOLUME /opt/project
WORKDIR /opt/project
