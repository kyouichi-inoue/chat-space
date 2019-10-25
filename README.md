# README

# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|e-mail|string|null: false, unique: true|
|password|string|null: false|
|create_at|timestamps||
|update_at|timestamps||
### Association
- has_many :groups
- has_many :posts
- has_many :groups, through: :groups_users

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|foreign_key: true|
|group_id|integer|foreign_key: true|
|image|string||
|body|text|null: false|
### Association
- belongs_to :user
- belongs_to :group


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|user_id|integer|foreign_key: true|
|create_at|timestamps||
|update_at|timestamps||
### Association
- has_many :posts
- has_many :users
- has_many :users, through: :groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|foreign_key: true|
|group_id|integer|foreign_key: true|
### Association
- belongs_to :post
- belongs_to :user

