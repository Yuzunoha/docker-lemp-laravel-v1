# docker-lemp-laravel-v1

## 起動手順
1. このリポジトリをcloneして中に入る。自分のLaravelプロジェクトとして使いたい場合は`.git/`以外のファイルをコピーして使う
    ```
    git clone https://github.com/Yuzunoha/docker-lemp-laravel-v1.git
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
- ホスト側で`html`以下のファイルを編集してLaravelを開発する。artisanやcomposerを使いたいときはphpコンテナに接続する
- phpMyAdminはブラウザで http://localhost:10040 にアクセスする
- dockerを終了するコマンド
    ```
    docker-compose down
    ```
