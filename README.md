# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| name               | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: :room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |
| guide   | text       |                                |

### Association

- belongs_to :room
- belongs_to :user

# アプリケーション名
family-chat

# アプリケーション概要
家族間でコミュニケーションを取り、毎日のルーティングを円滑にするアプリケーション

# URL


# 利用方法
## チャットルーム作成
1．トップページ（ログインページ）からユーザー登録を行う
2．

###
1．
2．

#### アプリケーションを作成した背景


# 洗い出した要件
https://docs.google.com/spreadsheets/d/1Hre8KForKK4Nl8OQdfSNLvtvdGCQr4Nl56pMJ1Hs5qw/edit?usp=sharing

# 実装した機能についての画像やGIFおよびその説明
・
[![Image from Gyazo](]()
・
[![Image from Gyazo]()]()

# 実装予定の機能
現在、リンク機能を実装中。
今後は、投稿したURLをクリックすると、リンク先に移動できるリンク機能を実装予定。

# データベース設計
[![Image from Gyazo](https://i.gyazo.com/a1cddeffbeda8cf35d93beb6bda50c6d.png)](https://gyazo.com/a1cddeffbeda8cf35d93beb6bda50c6d)

# 画面遷移図
[![Image from Gyazo](https://i.gyazo.com/af9c6e1a27e081ef03b3624cf1c395f7.png)](https://gyazo.com/af9c6e1a27e081ef03b3624cf1c395f7)

# 開発環境
・フロントエンド
・バックエンド

# ローカルでの動作方法
以下のコマンドを順に実行。
% git clone https://github.com/kazu-oku1/recipetweet.git
% cd recipetweet
% bundle install
% yarn install

# 工夫したポイント
レシピサイトのURLを入力することによって、投稿したレシピサイトのURLを検索すれば、
レシピの材料や作り方を入力せずにレシピを投稿できるように工夫をしました。