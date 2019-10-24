# README

# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|e-mail|string|null: false, unique: true|
|password|string|null: false|
|create_at|datetime||
|update_at|datetime||
### Association
- has_many :groups
- has_many :posts
- has_many :messages

## posts(users_groups)テーブル
|Column|Type|Options|
|------|----|-------|
|user_id|int|null: false|
|image|text||
|body|text|null: false|
|group_id|integer|foreign_key: true|
|user_id|integer|foreign_key: true|
|create_at|datetime||
|update_at|datetime||
### Association
- belongs_to :user
- belongs_to :message
- has_many :groups

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|text|null: false, unique: true|
|user_id|text|foreign_key: true|
|create_at|datetime||
|update_at|datetime||
### Association
- has_many :posts
- belongs_to :user

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|body|text||
|create_at|datetime||
|update_at|datetime||
### Association
- belongs_to :post
- belongs_to :user

