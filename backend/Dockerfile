FROM php:8.2-fpm-alpine

# System deps
RUN apk add --no-cache \
    bash \
    curl \
    git \
    unzip \
    libpng-dev \
    oniguruma-dev \
    icu-dev

# PHP extensions
RUN docker-php-ext-install pdo pdo_mysql intl

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www

COPY . .

RUN composer install --no-dev --optimize-autoloader

RUN chown -R www-data:www-data storage bootstrap/cache

EXPOSE 9000

CMD ["php-fpm"]
