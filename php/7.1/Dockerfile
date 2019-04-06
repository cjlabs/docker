FROM php:7.1.20-fpm


RUN apt-get update && apt-get install -y apt-utils git zip 
RUN apt install --fix-missing

RUN docker-php-source extract \
    && docker-php-ext-install pdo_mysql \
    && docker-php-source delete
RUN pecl channel-update pecl.php.net
RUN pecl install redis\
    && pecl install xdebug \
    && docker-php-ext-enable redis xdebug \
    && docker-php-ext-install mysqli && docker-php-ext-enable mysqli


COPY config/php.ini  /usr/local/etc/php/
#add php user
RUN useradd -ms /bin/bash php

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

USER php

RUN composer global require sebastian/phpcpd && \
    composer global require phpmd/phpmd && \
    composer global require squizlabs/php_codesniffer

EXPOSE 9000


