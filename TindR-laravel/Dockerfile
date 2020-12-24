FROM php:7.4.3-fpm
ENV DB_CONNECTION $(DB_CONNECTION)
ENV DB_HOST $(DB_HOST)
ENV DB_PORT $(DB_PORT)
ENV DB_DATABASE $(DB_DATABASE)
ENV DB_USERNAME $(DB_USERNAME)
ENV DB_PASSWORD $(DB_PASSWORD)
RUN apt-get update -y && apt-get install -y libmcrypt-dev openssl libpq-dev git
RUN docker-php-ext-install pdo pdo_pgsql pgsql
RUN ln -s /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini
RUN sed -i -e 's/;extension=pgsql/extension=pgsql/' /usr/local/etc/php/php.ini
RUN sed -i -e 's/;extension=pdo_pgsql/extension=pdo_pgsql/' /usr/local/etc/php/php.ini
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
WORKDIR /app
COPY . /app
RUN composer install

CMD php artisan serve --host=0.0.0.0 --port=8000
