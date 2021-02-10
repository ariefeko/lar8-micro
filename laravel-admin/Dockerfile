FROM php:7.3

RUN apt-get update -y && apt-get install -y openssl zip unzip git vim nano
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN docker-php-ext-install pdo mbstring pdo_mysql

RUN groupadd --gid 1000 arief \
    && useradd --uid 1000 -g arief \
    -G www-data,root --shell /bin/bash \
    --create-home arief

WORKDIR /app
COPY . .
RUN composer install

CMD php artisan serve --host=0.0.0.0
EXPOSE 8000

USER arief