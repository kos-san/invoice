# テーブル設計

## customers テーブル

| Column | Type   | Option      |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :documents

## documents テーブル

| Column         | Type      | Option                           |
| -------------- | --------- | -------------------------------- |
| customer_id    | reference | null: false, foreign_key: true   |
| contract       | boolean   | null: false, default: false      |
| estimate       | date      | null: false, default: Date.today |
| reception_name | string    | null: false                      |
| engineer_name  | string    | null: false                      |

### Association

- belongs_to :customer
- has_many :items

## items テーブル

| Column      | Type      | Options                        |
| ----------- | --------- | ------------------------------ |
| document_id | reference | null: false, foreign_key: true |
| item_name   | string    | null: false                    |
| item_price  | integer   |                                |
| costs       | float     |                                |

### Association

- belongs_to :document