# Node.js 18バージョンのイメージをベースにする
FROM node:18 AS build

# 作業ディレクトリを/appに設定する
WORKDIR /app

# 依存パッケージをインストールする
COPY ./react-app/package*.json ./
RUN npm install

# すべてのファイルをコンテナの/appディレクトリにコピーする
COPY ./react-app .

# ホットリロードを有効にするために必要な設定を追加する
RUN echo "CHOKIDAR_USEPOLLING=true" >> .env

# アプリケーションをビルドする
RUN npm run build

# アプリケーションが使用するポートをDockerに通知する
EXPOSE 3000

# アプリケーションを起動する
CMD ["npm", "start"]
