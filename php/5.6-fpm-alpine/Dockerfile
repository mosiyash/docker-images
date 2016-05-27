FROM alpine:3.3

MAINTAINER Nikita Mosiyash <nikita.mosiyash@gmail.com>

#  Ensure www-data user exists
RUN set -x \
	&& addgroup -g 82 -S www-data \
	&& adduser -u 82 -D -S -G www-data www-data \
    apk update \

RUN apk add --update \
        php-dev php-cli php-opcache php-wddx php-pdo_dblib php-mssql php-zlib \
        php-xml php-xmlreader php-xmlrpc php-xsl php-zip php-sysvmsg php-sysvsem \
        php-sysvshm php-soap php-sockets php-sqlite3 php-shmop php-snmp  php-posix \
        php-pspell php-pdo_sqlite php-pgsql php-phar php-pdo_odbc php-pdo_pgsql \
        php-pdo php-pdo_mysql php-openssl php-pcntl php-mysql php-mysqli php-odbc \
        php-ldap php-mcrypt php-intl php-json php-gmp php-iconv php-imap php-gd \
        php-gettext php-enchant php-exif php-ftp php-curl php-dba php-dom php-calendar \
        php-ctype php-bcmath php-bz2 php-pear php-phpdbg php-embed php-cgi \
        php-fpm php-common php-doc php-dbg php-memcache \
    # Clear apk cache \
    && rm -r /var/cache/apk/*

EXPOSE 9000
CMD ["php-fpm"]
