FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libonig-dev \
    libzip-dev \
    unzip \
    git \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install pdo_mysql mbstring gd zip

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

COPY ./app/composer.json ./app/composer.lock* /var/www/html/

RUN composer install --no-interaction --optimize-autoloader

COPY ./app /var/www/html

RUN chown -R www-data:www-data /var/www/html && chmod -R 755 /var/www/html
RUN chown -R www-data:www-data /var/www/html/web/assets && chmod -R 777 /var/www/html/web/assets

EXPOSE 9000

CMD ["php-fpm"]
