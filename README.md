# study_vuetify_dotnet

[![LICENSE](https://img.shields.io/badge/license-MIT-green.svg)](./LICENSE)
[![Open in Visual Studio Code](https://img.shields.io/static/v1?logo=visualstudiocode&label=&message=Open%20in%20Visual%20Studio%20Code&labelColor=555555&color=007acc&logoColor=007acc)](https://open.vscode.dev/q23isline/study_vuetify_dotnet)

[![Node.js](https://img.shields.io/static/v1?logo=node.js&label=Node.js&message=v24.5.0&labelColor=555555&color=339933&logoColor=339933)](https://nodejs.org)
[![npm](https://img.shields.io/static/v1?logo=npm&label=npm&message=v11.5.0&labelColor=555555&color=CB3837&logoColor=CB3837)](https://www.npmjs.com/)
[![Vue.js](https://img.shields.io/static/v1?logo=vue.js&label=Vue.js&message=v3.5.18&labelColor=555555&color=4FC08D&logoColor=4FC08D)](https://ja.vuejs.org/)
[![Vuetify](https://img.shields.io/static/v1?logo=vuetify&label=Vuetify&message=v3.9.4&labelColor=555555&color=1867C0&logoColor=1867C0)](https://vuetifyjs.com/ja/)

AWS SAM ( .NET ) と Vuetify の勉強用リポジトリ

[フロントエンド開発ガイドライン](./frontend/README.md)

## 前提

- インストール
  - [Windows Subsystem for Linux](https://learn.microsoft.com/ja-jp/windows/wsl/)
  - [Git](https://git-scm.com/)
  - [Docker Desktop](https://www.docker.com/ja-jp/products/docker-desktop/)
  - [Visual Studio Code](https://code.visualstudio.com/)

## はじめにやること

1. Windows Subsystem for Linux 上でプログラムダウンロード

    ```bash
    git clone 'https://github.com/q23isline/study_vuetify_dotnet.git'
    ```

2. リポジトリのカレントディレクトリへ移動

    ```bash
    cd study_vuetify_dotnet
    ```

3. 開発準備

    ```bash
    cp .vscode/settings.json.default .vscode/settings.json
    ```

4. アプリ立ち上げ

    ```bash
    docker compose build
    docker compose up -d
    # ライブラリインストール
    docker compose exec frontend npm install

    # エディタがライブラリを実行できるように実行権限を含めた全権限を与える
    sudo chmod -R 777 frontend/node_modules
    ```

## 日常的にやること

### システム起動

```bash
# コンテナ起動
docker compose up -d
# フロントエンド起動
docker compose exec frontend npm run dev -- --host
```

### システム終了

```bash
# フロントエンド起動ターミナルで Ctrl + c

docker compose down
```

## 動作確認

### URL

- <http://localhost:3000>

## ログ出力場所

| サービス | ログ出力場所  |
| -------- | ------------- |
| Node.js  | logs/frontend |

## Permission Deniedエラーや VSCode でライブラリが読み込めないエラーが出た時の解決方法

```bash
# プロジェクト全体のファイルすべてに読み込み、書き込み権限を与える
sudo chmod -R ogu+rw ./
# インストールしたライブラリに実行権限を含めた全権限を与える
sudo chmod -R 777 frontend/node_modules
```
