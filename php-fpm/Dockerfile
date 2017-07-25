FROM php:fpm-alpine

# PHP
RUN apk update && \
    apk add  --no-cache git mysql-client curl libmcrypt libmcrypt-dev \
    libxml2-dev freetype-dev libpng-dev libjpeg-turbo-dev g++ make autoconf zlib && \
    docker-php-source extract && \
    pecl install xdebug && \
    docker-php-ext-enable xdebug && \
    docker-php-source delete && \
    docker-php-ext-install pdo_mysql zip

# wkhtmltopdf
RUN apk add --no-cache qt5-qtbase-dev ttf-dejavu ttf-droid ttf-freefont ttf-liberation ttf-ubuntu-font-family
COPY wkhtmltopdf /bin

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Cleanup
RUN rm -rf /tmp/*

COPY php.ini /usr/local/etc/php/php.ini

WORKDIR /var/www
