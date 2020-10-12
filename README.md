# テーブル設計

## Users テーブル
| Column           | Type    | Options                        |
| ---------------- | ------- | ------------------------------ |
| nickname         | string  | null: false                    |
| email            | string  | null: false                    |
| password         | string  | null: false                    |
| family_name      | string  | null: false                    |
| first_name       | string  | null: false                    |
| family_name_kana | string  | null: false                    |
| first_name_kana  | string  | null: false                    |
| birthday         | integer | null: false                    |

### Association

- has_many :items
- has_one :purchases
- has_one :order

## Items テーブル

| Column          | Type      | Options                        |
| --------------- | --------- | ------------------------------ |
| name            | string    | null: false                    |
| text            | text      | null: false                    |
| price           | integer   | null: false                    |
| user            | reference | null: false, foreign_key: true |
| category        | string    | null: false                    |
| condition       | string    | null: false                    |
| shipping_format | string    | null: false                    |
| day             | string    | null: false                    |
|prefecture       | string    | null: false                    |

### Association

- belongs_to :user
- belongs_to_active_hash :category
- belongs_to_active_hash :condition
- belongs_to_active_hash :shipping_format
- belongs_to_active_hash :day
- belongs_to_active_hash :prefecture
- has_one :purchase

## Orders テーブル

| column  | Type      | Options                        |
| --------| --------- | ------------------------------ |
| address | string    | null: false                    |
| number  | integer   | null: false                    |
| item    | reference | null: false, foreign_key: true |
| price   | reference | null: false, foreign_key: true |
| user    | reference | null: false, foreign_key: true |

### Association

- belongs_to :item
- belongs_to :price
- belongs_to :user


## Purchases テーブル

| Column   | Type      | Options                        |
| -------- | --------- | ------------------------------ |
| user     | reference | null: false, foreign_key: true |
| item     | reference | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item