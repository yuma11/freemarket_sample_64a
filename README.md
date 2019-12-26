# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

- Ruby version

- System dependencies

- Configuration

- Database creation

- Database initialization

- How to run the test suite

- Services (job queues, cache servers, search engines, etc.)

- Deployment instructions

- ...

## users テーブル

| Column       | Type   | Options                   |
| ------------ | ------ | ------------------------- |
| nickname     | string | null: false               |
| name         | string | null: false               |
| k-name       | string | null: false               |
| email        | string | null: false               |
| password     | string | null: false               |
| image        | string |
| phone-number | int    | null: false, unique: true |
| items-number | int    | null: false               |
| Earnings     | string | null: false               |
| point        | int    | null: false               |
| birthday     | string | null: false               |

<!-- 外部キー -->

### Association

- has_many :cards
- has_many :addresss
- has_many :sellers
- has_many :buyers
- has_many :comments

## cards テーブル

| Column          | Type | Options                        |
| --------------- | ---- | ------------------------------ |
| number          | int  | null: false                    |
| yaer            | int  | null: false                    |
| moon            | int  | null: false                    |
| security-number | int  | null: false                    |
| user_id         | int  | null: false, foreign_key: true |

### Association

- belongs_to :users

## notices テーブル

| Column  | Type   | Options                        |
| ------- | ------ | ------------------------------ |
| notice  | string | null: false                    |
| user.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :user

## addresss テーブル

| Column       | Type   | Options                        |
| ------------ | ------ | ------------------------------ |
| postal-code  | int    | null: true                     |
| prefucture   | string | null: true                     |
| city         | string | null: true                     |
| city-address | string | null: true                     |
| building     | string | null: true                     |
| user_id      | int    | null: false, foreign_key: true |

### Association

- belongs_to :user

## buyers テーブル

| Column  | Type   | Options                        |
| ------- | ------ | ------------------------------ |
| bnice   | string | null: false                    |
| user.id | int    | null: false, foreign_key: true |
| item.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item

## sellers テーブル

| Column  | Type   | Options                        |
| ------- | ------ | ------------------------------ |
| bnice   | string | null: false                    |
| user.id | int    | null: false, foreign_key: true |
| item.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item

## items テーブル カテゴリ未記述

| Column        | Type   | Options                        |
| ------------- | ------ | ------------------------------ |
| name          | string | null: false                    |
| text          | text   | null: false                    |
| price         | int    | null: false                    |
| browse        | int    | null: false                    |
| user_id       | int    | null: false, foreign_key: true |
| size_id       | int    | null: false, foreign_key: true |
| status_id     | int    | null: false, foreign_key: true |
| burden_id     | int    | null: false, foreign_key: true |
| indication_id | int    | null: false, foreign_key: true |
| area_id       | int    | null: false, foreign_key: true |
| address_id    | int    | null: false, foreign_key: true |
| comment_id    | int    | null: false, foreign_key: true |
| buyer_id      | int    | null: false, foreign_key: true |
| seller_id     | int    | null: false, foreign_key: true |

| category_id | int | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :sizes
- has_many :statuss
- has_many :burdens
- has_many :indications
- has_many :areas
- has_many :addresss
- has_many :sellers
- has_many :buyers
- has_many :comments ,dependent: :destroy
- has_many :images ,dependent: :destroy
- has_many :brands
- has_many :categorys

## images テーブル

| Column  | Type   | Options                        |
| ------- | ------ | ------------------------------ |
| image   | string | null: false                    |
| item.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :item

## areas テーブル

| Column  | Type   | Options                        |
| ------- | ------ | ------------------------------ |
| area    | string | null: false                    |
| item.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :item

## statuss テーブル

| Column  | Type   | Options                        |
| ------- | ------ | ------------------------------ |
| status  | string | null: false                    |
| item.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :item

## indications テーブル

| Column      | Type   | Options                        |
| ----------- | ------ | ------------------------------ |
| indications | string | null: false                    |
| item.id     | int    | null: false, foreign_key: true |

### Association

- belongs_to :item

## brands テーブル

<!-- ここから不明 -->

| Column        | Type   | Options                        |
| ------------- | ------ | ------------------------------ |
| brands        | string | null: true                     |
| item.id       | int    | null: false, foreign_key: true |
| L-category.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :item
- has_many :L-categorys

## L-brands テーブル

| Column        | Type   | Options                        |
| ------------- | ------ | ------------------------------ |
| brands        | string | null: true                     |
| item.id       | int    | null: false, foreign_key: true |
| L-category.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :item
- has_many :L-categorys

## M-brands テーブル

| Column        | Type   | Options                        |
| ------------- | ------ | ------------------------------ |
| brands        | string | null: true                     |
| item.id       | int    | null: false, foreign_key: true |
| L-category.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :item
- has_many :L-categorys

## S-brands テーブル

| Column        | Type   | Options                        |
| ------------- | ------ | ------------------------------ |
| brands        | string | null: true                     |
| item.id       | int    | null: false, foreign_key: true |
| L-category.id | int    | null: false, foreign_key: true |

### Association

- belongs_to :item
- has_many :L-categorys

