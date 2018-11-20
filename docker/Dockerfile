FROM php:7.2.12-apache

RUN apt-get update && apt-get install -y libxml2-dev libpng-dev && \
    docker-php-ext-install ctype dom gd iconv posix simplexml xmlwriter zip pdo_mysql

