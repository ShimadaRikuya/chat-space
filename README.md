# チャットアプリケーション
http://18.177.230.196/

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

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :users, through: :groups_users
- has_many :group_users
- has_many :messages

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null:false|
|mail|string|null: false|

### Association
- has_many :groups, through: :group_users
- has_many :group_users
- has_many :messages

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group|references|null: false, foreign_key:true|
|user|references|nill: false, foreign_key:true|

### Association
- belongs_to :user
- belongs_to :group
