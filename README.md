# README

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|

###Association
- has_many :contents
- has_many :users_cats
- has_many :cats, through: :users_cats
- has_many :users_straycats
- has_many :straycats, through: :users_straycats

## catsテーブル
Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|SEX|string|null: false|
|created-at|string|null: false|


###Association
- has_many :contents
- has_many :users_cats
- has_many :users, through: :users_cats
- belongs_to :likes
- has_many :cats_homes
- has_many :homes, through: :cats_homes

## contentsテーブル
Column|Type|Options|
|------|----|-------|
|text|string|-------|
|photo|image|-------|
|user_id|integer|null: false, foreign_key: true|
|cat_id|integer|null: false, foreign_key: true|

###Association
- belongs_to :user
- belongs_to :cat

## users_catsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|cat_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :cat


## users_straycatsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|straycat_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :straycat

## straycatsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|SEX|string|null: false|
|created-at|---|------|
### Association
- has_many :users
- has_many :users, through: :users_straycats
- has_many :straycat.contents

## straycats.contentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|string|-------|
|photo|image|-------|
|user_id|integer|null: false, foreign_key: true|
|straycat_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :straycat

## likesテーブル
|Column|Type|Options|
|------|----|-------|
|user_like|---|-------|
|cat_like|---|-------|
|created_at|integer|null: false, foreign_key: true|
|updated_|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :cat


## homesテーブル
|Column|Type|Options|
|------|----|-------|
|home|---|-------|

### Association
- has_many :cats
- has_many :cats, through: :cats_homes

## cats_homesテーブル
|Column|Type|Options|
|------|----|-------|
|home_id|integer|null: false, foreign_key: true|
|cat_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :home
- belongs_to :cat