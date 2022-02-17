FROM php:7.4.12-apache
RUN apt-get update \
  && apt-get install -y zlib1g-dev \
  libonig-dev \
  && apt-get install -y zip unzip \
  && apt-get -y install libzip-dev \
  && docker-php-ext-install pdo_mysql mysqli mbstring zip\
  && docker-php-ext-enable mysqli \
  && a2enmod rewrite

# composerのインストール
RUN curl -sS https://getcomposer.org/installer | php \
  && mv composer.phar /usr/local/bin/composer \
  && chmod +x /usr/local/bin/composer

# 上記のコマンドを打つ場所
WORKDIR /var/www/html

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin
# タイムゾーン設定
ENV TZ=Asia/Tokyo