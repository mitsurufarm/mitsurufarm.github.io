# MITSURU FARM 圃場記録アプリ

MITSURU FARMで使用する個人向けの圃場・栽培記録アプリ。

圃場・エリア・作物・栽培・作業・収穫・写真を記録し、年度ごとの栽培履歴を検索・参照する。

## システム構成

```text
スマートフォン / PC
        │
        ▼
GitHub Pages
SPA（Webアプリ）
        │
        ▼
Amazon Cognito
認証
        │
        ▼
Amazon API Gateway
        │
        ▼
AWS Lambda
   ┌────┴────┐
   ▼         ▼
DynamoDB   Dropbox
構造化データ  写真
```

## 設計書

| 設計書 | 内容 |
|---|---|
| [システム概要](./システム概要.md) | システムの目的・構成・基本方針 |
| [データ設計](./データ設計.md) | データモデル・各エンティティの定義 |
| [テーブル構成設計](./テーブル構成設計.md) | DynamoDB 1テーブル方式・PK/SK・GSI |
| [DynamoDB詳細設計](./DynamoDB詳細設計.md) | DynamoDBの物理設計・属性・CRUD・削除・採番 |
| [API設計](./API設計.md) | APIエンドポイント・リクエスト・レスポンス |
| [画面設計](./画面設計.md) | SPAの画面構成・画面遷移 |
| [AWS構成](./AWS構成.md) | AWSサービス構成・接続方法 |
| [開発履歴](./開発履歴.md) | 設計・開発の変更履歴 |

## データ構造

```text
FIELD（圃場）
  │
  └─ AREA（エリア）
       │
       └─ CULTIVATION（栽培）
            ├─ WORK_LOG（作業）
            ├─ HARVEST（収穫）
            └─ PHOTO（写真）

CROP（作物マスタ）
  │
  └─ CULTIVATIONから参照

COUNTER
  └─ 各IDの自動採番
```

## 基本方針

- 個人利用を前提とする
- スマートフォンとPCの両方から利用する
- オンライン専用とする
- DynamoDBは1テーブル方式とする
- 作物はCROPマスタで管理する
- 写真本体はDropboxに保存する
- 構造化データはDynamoDBに保存する
- IDはDynamoDBのAtomic Counterで自動採番する
- データ削除は物理削除とする
- 初期版では必要以上に複雑な機能を追加しない

## 現在の設計状況

```text
システム概要       ── 確定
データ設計         ── 確定
テーブル構成設計   ── 確定
DynamoDB詳細設計   ── 確定
API設計            ── 次工程
画面設計           ── 後工程
AWS構成            ── 後工程
開発履歴           ── 継続
```

## 次の工程

次は `API設計.md` を作成し、SPAからAPI Gateway、Lambda、DynamoDB、Dropboxまでの具体的なAPI仕様を定義する。
