# README
## メモ投稿

## 概要
http://contribute-memo.herokuapp.com/

- タイトルと記事を投稿できます。
- 記事へタグ付け、記事のタグをクリックするとタグ検索ができます。
- いいね機能もあります。
- ユーザーページからはユーザーが投稿した記事、ユーザーがいいねした記事を閲覧できます。

## テストアカウント
こちらをご使用ください

- メールアドレス  
test@test

- パスワード  
12345678

## 主な機能
### ユーザー
- ユーザー登録、ログイン、ログアウト

### 記事
- 記事の投稿、記事の編集、削除、タグ付け、タグ別検索、記事へのいいね機能

## データベース

## articlesテーブル
|column|Type|Options|
|------|----|-------|
|title|string|null:false|
|body|text|null:false|
|user_id|references|null:false,foreign_key:true|

### アソシエーション
- BelongsTo:user
- BelongsToMany:likes
- BelongsToMany:tags

## usersテーブル
|column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|mail|string|null: false, unique: true|
|password|string|-----|

### Association
- HasMany:articles
- BelongsToMany:followers
- BelongsToMany:Followings
- BelongsToMany:likes

##  likesテーブル
|column|Type|Options|
|------|----|-------|
|user_id|references|null:false,foreign_key:true|
|article_id|references|null:false,foreign_key:true|

### Association
- BelongsTo:user
- BelongsTo:article

##  tagsテーブル
|column|Type|Options|
|------|----|-------|
|name|string|unique: true|

### Association
- BelongsToMany:articles

##  article_tagテーブル
|column|Type|Options|
|------|----|-------|
|article_id|references|null:false,foreign_key:true|
|tag_id|references|null:false,foreign_key:true|

### Association
- BelongsTo:article
- BelongsTo:tag

##  followsテーブル
|column|Type|Options|
|------|----|-------|
|follower_id|references|null:false,foreign_key:true|
|followee_id|references|null:false,foreign_key:true|

### Association
- BelongsToMany:users