FROM php:8.3-fpm

ENV TZ Asia/Tokyo

RUN apt-get update && \
	apt-get install -y git unzip libzip-dev libicu-dev libonig-dev && \
	docker-php-ext-install intl pdo_mysql zip bcmath
		
COPY ./docker/app/php.ini /usr/local/etc/php/php.ini

COPY --from=composer:2.7 /usr/bin/composer /usr/bin/composer

ARG NODE_VERSION=20.x
RUN curl -sL https://deb.nodesource.com/setup_$NODE_VERSION | bash - \
  && apt-get update \
  && apt-get install -y nodejs \
  && apt-get clean \
  && npm install -g npm@10.8.1

EXPOSE 5173

WORKDIR /app