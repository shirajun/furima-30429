# テーブル設計

## users テーブル
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
- has_many :purchases


## items テーブル
| Column  | Type      | Options                        |
| ------- | --------- | ------------------------------ |
| image   |           | null: false                    |
| name    | string    | null: false                    |
| text    | text      | null: false                    |
| price   | integer   | null: false                    |
| user_id | reference | null: false, foreign_key: true |

### Association

-belongs_to :user
-has_one :purchase

## purchases テーブル
| Column   | Type      | Options                        |
| -------- | --------- | ------------------------------ |
| address  | string    | null: false                    |
| user_id  | reference | null: false, foreign_key: true |
| item_id  | reference | null: false, foreign_key: true |

### Association

-belongs_to :user
-belongs_to :item