# 開発環境
# フロントエンド:react
# バックエンド:laravel
# webサーバー:nginx
# データベース:MySQL with phpMyAdmin

#reactのインストール
node.jsをインストール後に以下のコマンドを実行
> npm install -g create-react-app
> create-react-app react-app
ymlファイルの設定はプロジェクト名が"react-app"になっています。
"react-app"以外のプロジェクト名を利用する際には、ymlファイルを編集してください。

#laravelのインストール
composerをインストール後に以下のコマンドを実行
> composer global require laravel/installer
> laravel new laravel-app
ymlファイルの設定はプロジェクト名が"laravel-app"になっています。
"laravel-app"以外のプロジェクト名を利用する際には、ymlファイルを編集してください。

#ディレクトリ構造
reactとlaravelのインストール後は以下の構造になる
root
├ react-app
├ laravel-app
├ docker
│ ├ db
│ ├ php
│ ├ node
│ └ nginx
└ docker-compose.yml

#laravelのenvファイルの設定
ymlファイルと.envファイルのデータベース情報を同一の情報で設定する

#docker-composeを実行
dockerを起動後、以下のコマンドを実行してdockerコンテナを起動する
> docker-compose up -d --build

#起動後のURL
フロントエンド http://localhost
バックエンド   http://localhost/api
phpMyAdmin     http://localhost:8080

dockerコンポーネントが起動された後、ブラウザからアクセスすると"502 Bad Gateway"が表示されることがあります。
その場合は3分ほど待つとアクセスできるようになります。
