FROM php:8.0.2-fpm

# Arguments defined in docker-compose.yml
ARG user
ARG uid
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash 
RUN apt-get update && apt-get install -y nodejs

# update packages
# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip\
    libzip-dev


COPY package.json package-lock.json ./

# Install deps
RUN npm install -g npm@latest
RUN npm install

# Build assets
# RUN npm run dev

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd pcntl exif zip

#Install ext-php
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && sync && \
    install-php-extensions http

# install cron
RUN apt-get update && apt-get -y install rsyslog

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# COPY ./php.ini "$PHP_INI_DIR/php.ini"
# Create system user to run Composer and Artisan Commands
RUN useradd -G www-data,root -u $uid -d /home/$user $user
RUN mkdir -p /home/$user/.composer && \
    chown -R $user:$user /home/$user


COPY ./docker-entrypoint.sh /docker-entrypoint.sh
RUN chmod +x /docker-entrypoint.sh

# Set working directory
WORKDIR /var/www

ENTRYPOINT ["bash","docker-entrypoint.sh"]

EXPOSE 9000

USER $user