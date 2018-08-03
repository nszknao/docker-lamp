FROM php:7.2-apache

# 設定ファイル
COPY ./php.ini /usr/local/etc/php/

# docker公式にあるcore extention
RUN apt-get update && apt-get install -y --no-install-recommends apt-utils\
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

# PHP7からはmysql_関数が使えなくなっている
# Wordpressでmysql_関数を使っている
RUN docker-php-ext-install mysqli
