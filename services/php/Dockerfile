FROM php:8.2-fpm

# Установка зависимостей и расширений PHP
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo pdo_mysql

# Копируем наш конфигурационный файл php.ini
COPY ./php.ini /usr/local/etc/php/conf.d/custom-php.ini

WORKDIR /var/www/html

# Опционально: Если есть необходимость в Composer или других инструментах, установите их здесь