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

## DB

以下コマンドによりMySQLが立ち上がる

```bash
$ docker compose up -d
```

## Prisma

- databaseのschema情報を更新した場合
  `npx prisma migrate dev`
- seed dataの投入
  `npx prisma db seed`
  このseedデータの投入によりユーザーの公開鍵、秘密鍵やTSL証明書のファイルパス情報などを投入しています。
  IDは固定しているので、そのまま利用可能です

### **各ディレクトリ構成について**

```markdown
- src/controller
  - ルーティング用のディレクトリ（プレゼンテーション層）
- src/domain
  - ドメインロジック（ドメイン層）
- src/middlewre
  - 認証とか
- src/module
  - 依存関係解決のためのmoduleシステム
  - 循環参照防止のためInjection毎に1module作っている
- src/repository
  - ブロックチェーンにデータを永続化したり、RDBにデータを永続化したりする
- src/types
  - 型定義
- src/usecase
  - ビジネスロジックを作成する
- prisma
  - prismaの設定ファイルやマイグレーションファイル
- test
```
