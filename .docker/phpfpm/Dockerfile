FROM php:7.0-fpm

RUN apt-get update && apt-get install -y \
  cron \
  libfreetype6-dev \
  libicu-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng12-dev \
  libxslt1-dev \
  mysql-client \
  zip

RUN docker-php-ext-configure \
  gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install \
  bcmath \
  gd \
  intl \
  mbstring \
  mcrypt \
  opcache \
  pdo_mysql \
  soap \
  xsl \
  zip

ENV PHP_MEMORY_LIMIT 2G
ENV PHP_PORT 9000
ENV PHP_PM dynamic
ENV PHP_PM_MAX_CHILDREN 10
ENV PHP_PM_START_SERVERS 4
ENV PHP_PM_MIN_SPARE_SERVERS 2
ENV PHP_PM_MAX_SPARE_SERVERS 6
ENV APP_MAGE_MODE default

COPY .docker/phpfpm/config/www.conf /usr/local/etc/php-fpm.d/
COPY .docker/phpfpm/config/php.ini /usr/local/etc/php/
COPY .docker/phpfpm/config/php-fpm.conf /usr/local/etc/
COPY .docker/phpfpm/bin/* /usr/local/bin/

RUN chmod +x /usr/local/bin/*

WORKDIR /var/www/html

RUN usermod -u 1000 www-data

CMD ["/usr/local/bin/start"]