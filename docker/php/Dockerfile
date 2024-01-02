FROM php:8.2-fpm
COPY php.ini /usr/local/etc/php/

RUN apt-get update \
  && apt-get install -y zlib1g-dev mariadb-client vim libzip-dev \
  && docker-php-ext-install zip pdo_mysql

# Composer install
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

WORKDIR /var/www

# Install Laravel
RUN composer create-project --prefer-dist laravel/laravel laravel_project "10.*"

# Change working directory to the Laravel project directory
WORKDIR /var/www/laravel_project

# Laravelの組み込みサーバーをポート9000で起動する
CMD php artisan serve --host=0.0.0.0 --port=9000

# Dockerコンテナがポート9000をリッスンすることを指定
EXPOSE 9000
