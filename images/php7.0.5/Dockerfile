FROM daocloud.io/php:7.0.5-fpm
RUN pecl install xdebug-2.8.1 \
	&& apt-get update \
    && apt-get install -y zlib1g-dev \
	&& docker-php-ext-enable xdebug \
	&& docker-php-ext-install mysqli \
	&& docker-php-ext-install pdo_mysql \
	&& docker-php-ext-install bcmath \
	&& docker-php-ext-install zip
CMD ["php-fpm"]