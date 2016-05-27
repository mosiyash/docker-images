FROM php:5.6-fpm-alpine

MAINTAINER Nikita Mosiyash <nikita.mosiyash@gmail.com>

RUN apk update \
    # Install build dependencies \
    && apk add gcc libtool openssl-dev libmcrypt-dev curl-dev libxml2-dev libedit-dev openssl-dev sqlite-dev imagemagick-dev libjpeg-turbo-dev libpng-dev postgresql-dev \
    # Recompile php with more extensions. \
    # Default configure options is: \
    # 	--with-config-file-path=/usr/local/etc/php \
    # 	--with-config-file-scan-dir=/usr/local/etc/php/conf.d \
    # 	--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data \
    # 	--disable-cgi --enable-mysqlnd --enable-mbstring --with-curl \
    # 	--with-libedit --with-openssl --with-zlib \
    && cd /usr/src/php \
    && CONFIGURE_OPTIONS=$(php-config --configure-options) \
    && ./configure $CONFIGURE_OPTIONS \
        --with-mcrypt --with-pdo-pgsql --enable-exif \
        --with-gd --with-jpeg-dir --with-png-dir \
    && make \
    && make install \
    && make clean \
    # Install xhprof \
    && pecl install -f xhprof \
    && docker-php-ext-enable xhprof \
    # Install imagemagick \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    # Clear apk cache \
    && rm -r /var/cache/apk/*
