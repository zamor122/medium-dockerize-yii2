# Dockerfile for image that hosts application DOES NOT CONTAIN APPLICATION

FROM php:7.3-fpm

# Set working directory
WORKDIR /var/www/

# Install dependencies
RUN apt-get update && apt-get install -y \
        curl \
        libicu-dev \
        libfreetype6-dev \
        libjpeg-dev \
        libpng-dev \
        libxml2-dev \
        libzip-dev \
        zlib1g-dev \
        openssh-client \
        nano \
        unzip \
        libcurl4-openssl-dev \
        sudo \
        libssl-dev \
        cron

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install extensions
RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl opcache intl iconv exif bcmath curl soap
RUN docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/
RUN docker-php-ext-install gd

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer