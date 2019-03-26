FROM php:7.2.16-apache
MAINTAINER Tobias Nußbaum

ENV PHP_INI_DIR /usr/local/etc/php/

#copy php.ini
COPY php.ini $PHP_INI_DIR

#update
RUN apt-get update

#zip
RUN apt-get install -y libzip-dev zip
RUN docker-php-ext-configure zip --with-libzip && docker-php-ext-install zip

#mysqli
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

#gd
RUN apt-get install -y libpng-dev libjpeg62-turbo-dev libfreetype6-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && docker-php-ext-install gd && docker-php-ext-enable gd


#wget
RUN apt-get install -y wget
