FROM php:7.2.8-fpm
#add php user

RUN docker-php-source extract \
    && docker-php-ext-install pdo_mysql \
    && docker-php-source delete

RUN pecl install redis\
    && pecl install xdebug \
    && docker-php-ext-enable redis xdebug

# COPY config/php.ini  /usr/local/etc/php/
RUN apt-get update && apt-get install -y apt-utils git zip 
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


USER www-data
EXPOSE 9000

