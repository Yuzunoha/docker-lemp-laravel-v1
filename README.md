# docker-lemp-laravel-v1

## メモ
- laravelインストール済みにしよう

## 起動手順
1. このリポジトリをzipダウンロード,解凍して中に入る
    ```
    cd docker-lemp-laravel-v1
    ```
1. phpコンテナ内のuidをhost側のuidに合わせる(Docker for Mac/Windowsの人は不要かもしれない)
    ```
    1. host側でidコマンドを実行する 
    2. 上記手順で調べたuid=XXXXの値を当リポジトリのdocker/php/Dockerfile内の`ARG DOCKER_UID`に設定する
    ```
1. Dockerを起動する
    ```
    docker-compose up -d
    ```
1. phpコンテナに接続する
    ```
    docker-compose exec php bash
    ```
1. laravel用のモジュールをインストールする
    ```
    # phpコンテナで
    composer install
    ```
1. migrationを試す
    ```
    # phpコンテナで
    php artisan migrate
    ```
1. ブラウザで http://localhost:10080 にアクセスする

## メモ
- htmlディレクトリがnginx/phpコンテナのドキュメントルート`/var/www/html`にマウントされている
- phpMyAdminにアクセスする方法
  - ブラウザで http://localhost:10040 にアクセスする
