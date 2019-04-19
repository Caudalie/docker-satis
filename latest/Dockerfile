FROM jeremycurny/php:7.1-cli-alpine

MAINTAINER "Jeremy CURNY" <jeremy.curny.pro@gmail.com>

ENV COMPOSER_ALLOW_SUPERUSER=1
ENV COMPOSER_PROCESS_TIMEOUT 600
ENV SATIS_RUN_NGINX=1

ARG DEBIAN_FRONTEND=noninteractive

RUN apk update \
    && apk add --no-cache bash curl gcc git libffi-dev libressl-dev make musl-dev nginx python python2-dev zip \
    && rm -rf /var/cache/apk/* \
    && mkdir -p /run/nginx
    
RUN curl -fsSL https://bootstrap.pypa.io/get-pip.py | python \
    && pip install urllib3===1.22 \
    && pip install awscli docker-compose

RUN rm -rf /var/www/html/*

RUN \
    composer create-project composer/satis:dev-master --no-dev --no-progress /root/satis

EXPOSE 22
EXPOSE 80
