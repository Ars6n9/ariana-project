FROM php:8.2-fpm

# Install system dependencies and PHP extensions commonly needed for Laravel apps.
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        unzip \
        libpng-dev \
        libjpeg62-turbo-dev \
        libonig-dev \
        libxml2-dev \
        libzip-dev \
        zip \
    && docker-php-ext-configure gd --with-jpeg \
    && docker-php-ext-install \
        pdo_mysql \
        zip \
        gd \
    && rm -rf /var/lib/apt/lists/*

# Copy Composer from the official image for dependency management.
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

# Use the default php-fpm entrypoint.
CMD ["php-fpm"]
