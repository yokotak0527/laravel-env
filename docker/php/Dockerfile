FROM php:7.2-fpm-alpine
LABEL maintainer="yokotak0527 <454935+yokotak0527@users.noreply.github.com>"

# ユーザー追加
ARG USER_NAME
ARG USER_UID

RUN adduser ${USER_NAME} -u ${USER_UID} -D

# 一時ファイル追加
COPY tmp/* /tmp/

# intファイル追加
COPY php.ini /usr/local/etc/php/php.ini

# リモートリポジトリのアップデート
RUN apk update --no-cache

# サーバータイムゾーン変更
RUN apk add --no-cache tzdata && \
    ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# 必要なパッケージのインストールとエクステンション追加
RUN apk --no-cache add \
        gettext \
        bash \
        git \
        sudo \
        curl \
        libxml2-dev \
        openssl-dev \
        libpng \
        libpng-dev \
        libjpeg-turbo-dev \
        libwebp-dev \
        zlib-dev \
        libxpm-dev && \
    docker-php-ext-install pdo pdo_mysql mbstring gd zip && \
    apk del libpng-dev

# php-fpm設定追加
RUN envsubst < /tmp/zzz-docker.conf > /usr/local/etc/php-fpm.d/zzz-docker.conf

# Composer install
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer && \
    composer self-update

# laravel/installerのインストール
RUN sudo -u ${USER_NAME} composer global require laravel/installer
ENV PATH $PATH:/home/${USER_NAME}/.composer/vendor/bin

WORKDIR /var/www/html

