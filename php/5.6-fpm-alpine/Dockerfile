FROM php:5.6-fpm-alpine

MAINTAINER Nikita Mosiyash <nikita.mosiyash@gmail.com>

RUN \
    # Install build dependencies \
    apk add --update \
        autoconf file g++ gcc binutils isl libatomic libtool make re2c libstdc++ libgcc binutils-libs mpc1 mpfr3 gmp libgomp \
        coreutils libltdl \
        openssl-dev libmcrypt-dev curl-dev libc-dev musl-dev libxml2-dev icu-dev \
        libedit-dev openssl-dev sqlite-dev imagemagick-dev libjpeg-turbo-dev libpng-dev postgresql-dev freetype-dev libmcrypt-dev \
        icu-dev \
    # Recompile php with mcrypt, gd, pdo-pgsql. \
    # Default configure options is: \
    # 	--with-config-file-path=/usr/local/etc/php \
    # 	--with-config-file-scan-dir=/usr/local/etc/php/conf.d \
    # 	--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data \
    # 	--disable-cgi --enable-mysqlnd --enable-mbstring --with-curl \
    # 	--with-libedit --with-openssl --with-zlib \
    # && cd /usr/src/php \
    # && CONFIGURE_OPTIONS=$(php-config --configure-options) \
    # && ./configure $CONFIGURE_OPTIONS --with-mcrypt --with-gd --with-pdo-pgsql --enable-exif \
    # && make \
    # && make install \
    # Install xhprof \
    && pecl install -f xhprof \
    && docker-php-ext-enable xhprof \
    # Install imagemagick \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    # Install other extensions \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install \
        bcmath bz2 calendar ctype curl dba dom enchant exif fileinfo filter ftp gd gettext gmp hash iconv imap interbase  \
        intl json ldap mbstring mcrypt mssql mysql mysqli oci8 odbc opcache pcntl \
        pdo pdo_dblib pdo_firebird pdo_mysql pdo_oci pdo_odbc pdo_pgsql pdo_sqlite pgsql \
        phar posix pspell readline recode reflection session shmop simplexml snmp soap sockets spl standard \
        sybase_ct sysvmsg sysvsem sysvshm tidy tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zip \
    # Clear apk cache \
    && rm -r /var/cache/apk/*
