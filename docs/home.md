# 農業記録アプリ

## 農作業・栽培・収穫などを記録・管理する個人用Webアプリケーションです。

### 目次

- システム概要
- [データ設計](https://github.com/mitsurufarm/mitsurufarm.github.io/blob/main/docs/%E3%83%87%E3%83%BC%E3%82%BF%E8%A8%AD%E8%A8%88.md)
- テーブル構成設計
- DynamoDB詳細設計
- API設計
- 画面設計
- AWS構成
- 開発履歴

### システム構成

Android / PC
↓
GitHub Pages
↓
API Gateway
↓
AWS Lambda
↓
DynamoDB

写真はDropboxに保存します。

### データ構造

圃場
↓
エリア
↓
栽培
├ 作業記録
├ 収穫記録
└ 写真

### 基本方針

- 個人利用を前提とする
- 低コストな構成を目指す
- 栽培履歴を年単位で管理する
- 将来の機能追加を考慮しつつ、初期実装はシンプルにする
- 設計変更はdocs以下のファイルに反映する
