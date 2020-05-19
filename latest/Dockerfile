FROM php:7.1-cli-alpine

MAINTAINER "Jeremy CURNY" <jeremy.curny.pro@gmail.com>

ENV COMPOSER_ALLOW_SUPERUSER=1
ENV COMPOSER_PROCESS_TIMEOUT 600
ENV SATIS_RUN_NGINX=1

ARG DEBIAN_FRONTEND=noninteractive

RUN apk update \
    && apk add --no-cache bash git nginx rsync tree \
    && apk add --no-cache zlib-dev \
    && rm -rf /var/cache/apk/* \
    && mkdir -p /run/nginx

RUN rm -rf /var/www/html/*

RUN \
  docker-php-ext-install zip

RUN \
    curl -sL -o /usr/local/bin/composer https://getcomposer.org/download/1.10.1/composer.phar \
    && chmod +x /usr/local/bin/composer

RUN \
    composer create-project composer/satis:1.x-dev --no-dev --no-progress /root/satis

EXPOSE 22
EXPOSE 80
