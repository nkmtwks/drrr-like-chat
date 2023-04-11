# Dockerimageの指定 -> FROM [イメージ名]:[タグ名]
FROM php:8.0-fpm
#FROM php:7.4.0-fpm
# ファイルのコピー -> COPY [イメージ内にコピーしたいファイルのパスやURLなど] [コピー先のイメージのパス]
COPY php.ini /usr/local/etc/php/


FROM php:7.4.0-fpm

RUN apt-get update \
#RUN apt update \
    && docker-php-ext-install pdo_mysql

# ADD ./php.ini /usr/local/etc/php/php.ini


# コマンドの実行-> RUN [実行するコマンド]
 # apt-get update:パッケージリストの更新
 RUN apt-get update \
    # apt-get update：パッケージのインストール
    # zlib1g-dev：Zlib形式（gzipとPKZIPで使われているdeflate圧縮法）のデータ圧縮に使用するためのライブラリ
    # mariadb-client：MariaDB（MySQLの派生）を使用するためのライブラリ
    # vim：vimのテキストエディタを使用するためのライブラリ
    # libzip-dev：zipを使用するためのライブラリ
    && apt-get install -y zlib1g-dev mariadb-client vim libzip-dev \
    # docker-php-ext-install：標準PHPの拡張パッケージリストのインストール（今回は zipとpdo_mysqlパッケージ）
    && docker-php-ext-install zip pdo_mysql

    ## Composer install ##
    # コマンドの実行-> RUN [実行するコマンド]
    # composerのインストーラーとセットアップファイルをコピーする
    # php：phpコマンドライン, -r：実行
    # RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    # # composerのセットアップをする
    # RUN php composer-setup.php
    # # composerのセットアップファイルを削除する
    # RUN php -r "unlink('composer-setup.php');"
    # # ファイルを移動する -> mv < 変更前のファイル(ディレクトリ)名 > < 変更後のファイル(ディレクトリ)名 >
    # RUN mv composer.phar /usr/local/bin/composer
    # # コンテナの環境変数設定-> ENV [設定内容]
    # # composerのスーパーユーザー設定：「1」でrootユーザーに指定
    # ENV COMPOSER_ALLOW_SUPERUSER 1
    # # composerのホームディレクトリ設定：composerを指定
    # ENV COMPOSER_HOME /composer
    # # composerのルートPath設定：/composer/vendor/binを指定
    # ENV PATH $PATH:/composer/vendor/bin
    # 作業ディレクトリの設定-> WORKDIR [Paht]
    WORKDIR /var/www
    # Laravelパッケージのインストールを実行する

    # RUN composer global require "laravel/installer"