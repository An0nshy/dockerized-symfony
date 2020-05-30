FROM php:7.4-apache

RUN docker-php-ext-install pdo_mysql

RUN pecl install apcu

RUN apt-get update && \
apt-get install -y \
zlib1g-dev \
libzip-dev

RUN docker-php-ext-install zip
RUN docker-php-ext-enable apcu

# 2. apache configs + document root
ENV APACHE_DOCUMENT_ROOT=/var/www/html/test/public/
#RUN sed -ri -e 's!/var/www/html/test/public/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
#RUN sed -ri -e 's!/var/www/html/test/public/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

# 3. mod_rewrite for URL rewrite and mod_headers for .htaccess extra headers like Access-Control-Allow-Origin-
RUN a2enmod rewrite headers

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --filename=composer \
    && mv composer /usr/local/bin/composer

WORKDIR /var/www/html/

#COPY apps/my-symfony-app /usr/src/app

RUN PATH=$PATH:/usr/src/apps/vendor/bin:bin

#RUN composer create-project symfony/skeleton test