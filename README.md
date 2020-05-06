# ChatSpace DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false,add_index: true|
|email|string|null: false, unique: true|
|password|string|null: false|
|password confirmation|string|null: false|
### Association
- has_many :messages
- has_many :groups, through: :groups_users
- has_many :groups_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|integer|null:false, foreign_key: true|
|user_id|integer|null:false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, uniqur: true|

### Association
has_many :groups_users
has_many :users, through: :group_users
has_many :messages

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
