FROM php:7-fpm
MAINTAINER neo<neo@mailejifen.com>
COPY ext /usr/local/src/
COPY composer.phar /usr/local/bin/composer 
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        supervisor \
        nscd \
        openssl \
        curl \
        pkg-config \
        libssl-dev \
    && docker-php-ext-install -j $(nproc) iconv mcrypt pdo_mysql opcache \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j $(nproc) gd \
    && ( \
       cd /usr/local/src \
       && tar -zxvf mongodb-1.2.9.tgz  \
       && rm -rf mongodb-1.2.9.tgz \
       && cd mongodb-1.2.9 \
       && phpize \
       && ./configure \
       && make -j$(nproc) \
       && make install \
    ) \
    && docker-php-ext-enable mongodb \
    && ( \
       cd /usr/local/src \
       && tar -zxvf yaconf-1.0.5.tgz  \
       && rm -rf yaconf-1.0.5.tgz \
       && cd yaconf-1.0.5 \
       && phpize \
       && ./configure \
       && make -j$(nproc) \
       && make install \
    ) \
    && docker-php-ext-enable yaconf \
    && ( \
       cd /usr/local/src \
       && tar -zxvf redis-3.1.2.tgz  \
       && rm -rf redis-3.1.2.tgz \
       && cd redis-3.1.2 \
       && phpize \
       && ./configure \
       && make -j$(nproc) \
       && make install \
    ) \
    && docker-php-ext-enable redis \
    #&& pecl install channel://pecl.php.net/mongodb-1.2.9 && docker-php-ext-enable mongodb \
    #&& pecl install mongo-1.6.14 && docker-php-ext-enable mongo \
    #&& pecl install channel://pecl.php.net/xdebug-2.5.3 && docker-php-ext-enable xdebug \
    #&& pecl install channel://pecl.php.net/redis-3.1.2 && docker-php-ext-enable redis \
    #&& pecl install channel://pecl.php.net/xhprof-0.9.4 && docker-php-ext-enable xhprof \
    && rm -rf /usr/local/src/* \
    && mkdir -p /var/log/php && touch /var/log/php/errors.log \
    && touch /var/log/php/php-fpm.slow.log \
    && apt-get autoclean \
    && apt-get autoremove \
    && chmod +x /usr/local/bin/composer \
    && usermod -u 1002 www-data
COPY php.ini /usr/local/etc/php/
COPY php-fpm.conf /usr/local/etc/php-fpm.d/www.conf
