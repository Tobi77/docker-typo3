FROM php:7.2.16-apache

#copy php.ini
COPY php.ini /usr/local/etc/php/

#copy apache config
COPY apache.conf /etc/apache2/sites-available/000-default.conf

#update packaging tool
RUN apt-get update

#install php zip
RUN apt-get install -y libzip-dev zip
RUN docker-php-ext-configure zip --with-libzip && docker-php-ext-install zip

#install php mysqli
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

#install php opcache
RUN docker-php-ext-install opcache && docker-php-ext-enable opcache

#install php gd
RUN apt-get install -y libpng-dev libjpeg62-turbo-dev libfreetype6-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && docker-php-ext-install gd && docker-php-ext-enable gd

#install wget
RUN apt-get install -y wget

#download composer
RUN curl -sSk https://getcomposer.org/installer | php -- --disable-tls && mv composer.phar /usr/local/bin/composer

#enable xDebug
RUN pecl install xdebug; \
    docker-php-ext-enable xdebug; \
    echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.default_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=1" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_connect_back=0" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.max_nesting_level=400" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_host=docker.for.mac.host.internal" >> /usr/local/etc/php/conf.d/xdebug.ini
