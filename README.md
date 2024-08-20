## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Installation

```bash
$ npm install
```

## Running the app

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Test

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```

## Prisma
 - databaseの情報を更新した場合
 `npx prisma migrate dev`
 - seed dataの投入
 `npx prisma db seed`

## ER図
https://drive.google.com/file/d/1xYKaVIECLKaOo0NEShXlshQ16secAAYn/view?usp=sharing

## 各ディレクトリ構成について
 - src/controller
  - ルーティング用のディレクトリ（プレゼンテーション層）
 - src/domain
  - ドメインロジック（ドメイン層）
 - src/middlewre
  - 認証とか
 - src/module
  - 依存関係解決のための定義ファイルInjectionごとにmoduleファイル分けたほうがいいかなー
 - src/repository
  - ブロックチェーンにデータを永続化したり、RDBにデータを永続化したりする
 - src/types
  - 型定義
 - src/usecase
  - ビジネスロジックを作成する
 - peer
  - peerのTLS証明書ファイルを保存する場所
 - user
  - userの公開鍵、秘密鍵を保存する
 - prisma
  - prismaの設定ファイルやマイグレーションファイル
 - test

## blockchain(Hyperledger)
hyperledger fabricのサンプルのネットワークを動かしそこにchaincodeをデプロイしたものを本プロジェクトで呼び出します。
Hyperledger fabricの実行に必要な事前準備やサンプルのダウンロード方法は公式ドキュメントを合わせてご確認ください。
以下はすべて事前準備が完了している前提でHyperleder Fabricのネットワークを構成するサンプルをダウンロードするところからになります。
https://hyperledger-fabric.readthedocs.io/ja/latest/install.html

サンプルのダウンロードからテストネットワーク起動まで
```
curl -sSLO https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh && chmod +x install-fabric.sh

cd fabric-samples/test-network

./network.sh up createChannel -c mychannel -ca

```

chaincodeのデプロイ
```
./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-javascript/ -ccl javascript
```

各種証明書ファイルのコピー

test-network/