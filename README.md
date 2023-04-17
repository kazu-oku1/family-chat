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
家族間で連絡や予定などを共有するアプリケーション

# URL
https://family-chat.onrender.com

# 利用方法
## メッセージ投稿
1．トップページ（ログインページ）からユーザー新規登録を行う

2．チャット作成ボタンからチャットルーム名を決定し、チャットしたい相手を選択する

3．チャットルームをクリックし、メッセージの内容（メッセージ、URLリンク、画像）を入力し、投稿する

4．チャットを終了する場合は、チャット終了ボタンを押す

### 投稿したURLのリンク先に飛ぶ
1．投稿したURLをクリックすると、そのリンク先に新しいページで開く

2．料理のリクエストや共有したいURLがあれば、料理サイトのURLなどと共にチャットメッセージを送るなどを行う

#### アプリケーションを作成した背景
母に家事の課題をヒアリングし、「日々多忙な家族の予定がわからないため、予定を立てれないまたは、料理の献立決めに迷う」という課題を抱えていることが判明した。課題を分析した結果、「家族の予定や連絡を手軽に連絡する場」が無いということが真因であると仮説を立てた。同様の問題を抱えている方も多いと推測し、家族同士のコミュニケーションを手軽に行えるチャットアプリケーションを開発することにした。

# 洗い出した要件
https://docs.google.com/spreadsheets/d/1Hre8KForKK4Nl8OQdfSNLvtvdGCQr4Nl56pMJ1Hs5qw/edit?usp=sharing

# 実装した機能についての画像やGIFおよびその説明
・チャット作成ボタンをクリックすると、新規チャットルームが表示される。チャットルーム名を作成し、チャットメンバーを選択する。
[![Image from Gyazo](https://i.gyazo.com/77c8d9f2347cfe8fcc33edffe8cb4cfe.gif)](https://gyazo.com/77c8d9f2347cfe8fcc33edffe8cb4cfe)
・チャットルームのフォームからメッセージ、または画像、任意としてURLリンクを投稿できる。URLをクリックするとリンク先に飛ぶことができる。
[![Image from Gyazo](https://i.gyazo.com/4270868e9e156def0287ffbae2eb6081.gif)](https://gyazo.com/4270868e9e156def0287ffbae2eb6081)

# 実装予定の機能
今後は、コミュニケーションを活性化するために、メンバー全員とチャットできる機能や、フォロー機能といいねを実装予定。
ユーザー情報の写真を追加予定。

# データベース設計
![画像の説明](https://github.com/kazu-oku1/family-chat/commit/166d0b7b4af62b8c5560e58d7c5b6780e22bdf87#diff-6ce1801b745715af6f19c5b1380c1f4b70f31e754ad95f4f4ba6f2006c1eca87)

# 画面遷移図
![画像の説明](https://github.com/kazu-oku1/family-chat/commit/166d0b7b4af62b8c5560e58d7c5b6780e22bdf87#diff-2293bd87dc17ab9342a6c74d0ec86fd6c81fe0babc3c5a343aae05229d5ea174)

# 開発環境
・フロントエンド

・バックエンド

# ローカルでの動作方法
以下のコマンドを順に実行。

% git clone https://github.com/kazu-oku1

% cd family-chat

% bundle install

% yarn install

# 工夫したポイント
投稿したURLを開くと、そのリンク先に新しいタブで開くように実装しました。