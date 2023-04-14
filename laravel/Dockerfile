FROM php:8.1-apache

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        libzip-dev \
        zip \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_mysql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN a2enmod rewrite

RUN cd /var/www/html/laravel && \
    composer install

RUN cd /var/www/html/laravel && \
    php artisan key:generate

RUN apt-get install nodejs npm -y

RUN cd /var/www/html/laravel && \
    npm install && npm run dev

RUN chmod 777 -R -c /var/www/html