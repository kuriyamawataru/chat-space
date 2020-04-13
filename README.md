-# chat-space DB設計
## messeageテーブル
|Colum|Type|Option|
|-----|----|------|
|body|text|
|image|string|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
belongs_to :user
belongs_to :group

## usersテーブル
|Colum|Type|Option|
|-----|----|------|
|name|string|null: false, add_index: true|
|email|string|null: false, unique: true|
|password|string|null: false|
### Association
has_many :messages
has_many :groups_users
has_many :groups, through: groups_users


## groupsテーブル
|Colum|Type|Option|
|-----|----|------|
|name|string|null: false, unique: true|
## Association
has_many :users, through: groups_users
has_many :messages
has_many :groups_users

## groups_usersテーブル
|Colum|Type|Option|
|-----|----|------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_keu: true|
## Association
belongs_to :user
belongs_to :group
