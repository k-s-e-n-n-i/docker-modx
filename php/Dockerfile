# Версия php, в нашем случае именно fpm
FROM php:7.3-fpm
# Устанавливаем расшерения
RUN apt-get update && apt-get install -y \
        zip \
        unzip\
        supervisor \
        curl \
        wget \
        git \
        libxslt-dev \
        libicu-dev \
        libmcrypt-dev \
        libwebp-dev \
        libjpeg62-turbo-dev \
        libpng-dev libxpm-dev \
        libfreetype6-dev \
        libzip-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd \
        --with-gd \
        --with-webp-dir \
        --with-jpeg-dir \
        --with-png-dir \
        --with-zlib-dir \
        --with-xpm-dir \
        --with-freetype-dir \
    && docker-php-ext-install \
        iconv \
        gd \
        mysqli \
        pdo \
        pdo_mysql \
        mbstring \
        tokenizer \
        opcache \
        exif \
        zip \
        pcntl

RUN pecl install redis \
    && pecl install xdebug \
    && pecl install mcrypt \
    && docker-php-ext-enable mcrypt \
    && docker-php-ext-enable redis xdebug

# устанавливаем compose, если нужно
RUN curl -sS https://getcomposer.org/installer | \
            php -- --install-dir=/usr/bin/ --filename=composer

CMD ["php-fpm"]