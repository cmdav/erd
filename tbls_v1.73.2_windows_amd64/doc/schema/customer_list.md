# customer_list

## Description

VIEW

<details>
<summary><strong>Table Definition</strong></summary>

```sql
CREATE VIEW customer_list AS (select `cu`.`customer_id` AS `ID`,concat(`cu`.`first_name`,' ',`cu`.`last_name`) AS `name`,`a`.`address` AS `address`,`a`.`postal_code` AS `zip code`,`a`.`phone` AS `phone`,`sakila_db`.`city`.`city` AS `city`,`sakila_db`.`country`.`country` AS `country`,if(`cu`.`active`,'active','') AS `notes`,`cu`.`store_id` AS `SID` from (((`sakila_db`.`customer` `cu` join `sakila_db`.`address` `a` on((`cu`.`address_id` = `a`.`address_id`))) join `sakila_db`.`city` on((`a`.`city_id` = `sakila_db`.`city`.`city_id`))) join `sakila_db`.`country` on((`sakila_db`.`city`.`country_id` = `sakila_db`.`country`.`country_id`))))
```

</details>

## Referenced Tables

- [customer](customer.md)
- [address](address.md)
- [city](city.md)
- [country](country.md)

## Columns

| Name | Type | Default | Nullable | Children | Parents | Comment |
| ---- | ---- | ------- | -------- | -------- | ------- | ------- |
| ID | smallint unsigned | 0 | false |  |  |  |
| name | varchar(91) |  | false |  |  |  |
| address | varchar(50) |  | false |  |  |  |
| zip code | varchar(10) |  | true |  |  |  |
| phone | varchar(20) |  | false |  |  |  |
| city | varchar(50) |  | false |  |  |  |
| country | varchar(50) |  | false |  |  |  |
| notes | varchar(6) |  | false |  |  |  |
| SID | tinyint unsigned |  | false |  |  |  |

## Relations

![er](customer_list.svg)

---

> Generated by [tbls](https://github.com/k1LoW/tbls)
