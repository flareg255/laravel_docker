# laravel_docker

nginx の default.conf の root を書き換える
例
/var/www/app/public
app は laravel のプロジェクト名、public までパスを書く

docker compose up -d
を実行

docker exec -it app bash
を実行し、コンテナの中に入る

コンテナの中で
composer create-project "laravel/laravel=11.\*" app --prefer-dist
を実行し、laravel をインストール

インストール後に
cd app
chmod -R guo+w storage
php artisan storage:link
を実行

.env を書き換える
DB_CONNECTION=mysql
DB_HOST=DB のコンテナの名前を書く
DB_PORT=3306
DB_DATABASE=dev
DB_USERNAME=root
DB_PASSWORD=root

php artisan migrate
を実行する
