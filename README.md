# Database design

### usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true, index: true|
|email|string|null: false, unique: true|
|password|string|null: false|
 * the gem `devise` creates email and password

#### Association

- has_many :groups, through: :members
- has_many :members
- has_many :messages

### groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

#### Association

- has_many :user, through: :members
- has_many :members
- has_many :messages

### membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true, index: true|
|group_id|integer|null: false, foreign_key: true, index: true|

#### Association

- belongs_to :user
- belongs_to :group

### messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|integer|null: false, foreign_key: true, index: true|
|user_id|integer|null: false, foreign_key: true, index: true|

#### Association

- belongs_to :user
- belongs_to :group

