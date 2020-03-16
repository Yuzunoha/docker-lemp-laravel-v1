# docker-lemp-laravel-v1

## メモ
- laravelインストール済みにしよう

## 起動手順
1. このリポジトリをcloneして中に入る
    ```
    git clone https://github.com/Yuzunoha/docker-lemp-laravel-v1.git
    cd docker-lemp-laravel-v1
    ```
1. phpコンテナ内のuidをhost側のuidに合わせる(Docker for Mac/Windowsの人は不要かもしれない)
    1. host側でidコマンドを実行する
    1. 上記手順で調べたuid=XXXXの値を/php/Dockerfile内の`ARG DOCKER_UID`に設定する
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

## メモ
- htmlディレクトリがnginx/phpコンテナのドキュメントルート`/var/www/html`にマウントされている
- ドキュメントルートにアクセスする方法
  - ブラウザで下記アドレスにアクセスする
      - http://localhost:10080
- phpMyAdminにアクセスする方法
  - ブラウザで下記アドレスにアクセスする
      - http://localhost:10040
