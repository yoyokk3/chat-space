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

## usersテーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false, index: true|
|email|string|null: false, unique: true|
|password|integer|null: false|

### Association
- has_many :groups, through: :groups_users
- has_many :groups_users
- has_many :chats

## groupsテーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false|

### Association
- has_many :chats
- has_many :users, through: :groups_users
- has_many :groups_users

## chatsテーブル
|Column|Type|Option|
|------|----|------|
|text|text||
|image|string||
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
|created_at|integer|null: false|

### Association
- belongs_to :group
- belongs_to :user

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user