# ベースイメージの指定
FROM php:8.2-fpm-buster

EXPOSE 5173
# 作成した設定ファイルをコンテナ内にコピー
COPY ./container/php/php.ini /usr/local/etc/php/php.ini

# パッケージのインストール
RUN apt-get update \
    && apt-get -y install git zip unzip vim

RUN docker-php-ext-install pdo_mysql

RUN curl -sL https://deb.nodesource.com/setup_16.x | bash -
RUN apt-get install -y nodejs

# composerのインストール
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

# コンテナ内で作業する際のカレンとディレクトリの指定
WORKDIR /var/www/html