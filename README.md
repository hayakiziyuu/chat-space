# chatspace DB設計

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|image|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false, foreign_key: true|

### Association
- has_many :groups_users
- has_many :users, through: groups_users
- has_many :messages

## userテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false, unique: true|
|password|string|null: false|
|username|string|null: false, add_index: true|


### Association
- has_many :groups_users
- has_many :groups, through: groups_users
- has_many :messages

