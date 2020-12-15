FROM php:5.6.22-fpm
RUN apt-get update \
    && apt-get install -y zlib1g-dev libmemcached-dev libmcrypt-dev \
    && pecl install xdebug-2.5.5 \
    && docker-php-ext-enable xdebug \
    && pecl install memcached-2.1.0 \
	&& docker-php-ext-enable memcached \
	&& pecl install memcache-3.0.8 \
	&& docker-php-ext-enable memcache \
	&& docker-php-ext-install mysqli \
	&& docker-php-ext-install pdo_mysql \
	&& docker-php-ext-install bcmath \
	&& docker-php-ext-install zip \
	&& docker-php-ext-install mcrypt
CMD ["php-fpm"]