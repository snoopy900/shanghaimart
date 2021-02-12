# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null:false, unique: true |
| encrypted_password | string | null: false |
| birthday           | date   | null: false |

- has_many :foods
- has_many :orders

## foods テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |
| content| string | null: false |
| price  | string | null: false |


- belongs_to :user
- has_one    :order

## food_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| food   | references | null: false, foreign_key: true |

- belongs_to :user
- belongs_to :food

## orders テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| user    | references | null: false, foreign_key: true |
| food    | references | null: false, foreign_key: true |

- belongs_to :user
- belongs_to :food
- has_one    :address

## addresses テーブル

| Column        | Type       | Options     |
| ------------  | ---------- | ------------|
| post          | string     | null: false |
| prefecture_id | integer    | null: false |
| city          | string     | null: false |
| address       | string     | null: false |
| building      | string     | null: false |
| phone_number  | string     | null: false |
| order         | references | null: false, foreign_key: true |

- belongs_to : order 