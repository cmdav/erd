# film

## Description

<details>
<summary><strong>Table Definition</strong></summary>

```sql
CREATE TABLE `film` (
  `film_id` smallint unsigned NOT NULL AUTO_INCREMENT,
  `title` varchar(128) NOT NULL,
  `description` text,
  `release_year` year DEFAULT NULL,
  `language_id` tinyint unsigned NOT NULL,
  `original_language_id` tinyint unsigned DEFAULT NULL,
  `rental_duration` tinyint unsigned NOT NULL DEFAULT '3',
  `rental_rate` decimal(4,2) NOT NULL DEFAULT '4.99',
  `length` smallint unsigned DEFAULT NULL,
  `replacement_cost` decimal(5,2) NOT NULL DEFAULT '19.99',
  `rating` enum('G','PG','PG-13','R','NC-17') DEFAULT 'G',
  `special_features` set('Trailers','Commentaries','Deleted Scenes','Behind the Scenes') DEFAULT NULL,
  `last_update` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`film_id`),
  KEY `idx_title` (`title`),
  KEY `idx_fk_language_id` (`language_id`),
  KEY `idx_fk_original_language_id` (`original_language_id`),
  CONSTRAINT `fk_film_language` FOREIGN KEY (`language_id`) REFERENCES `language` (`language_id`) ON DELETE RESTRICT ON UPDATE CASCADE,
  CONSTRAINT `fk_film_language_original` FOREIGN KEY (`original_language_id`) REFERENCES `language` (`language_id`) ON DELETE RESTRICT ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=[Redacted by tbls] DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci
```

</details>

## Columns

| Name | Type | Default | Nullable | Extra Definition | Children | Parents | Comment |
| ---- | ---- | ------- | -------- | ---------------- | -------- | ------- | ------- |
| film_id | smallint unsigned |  | false | auto_increment | [film_actor](film_actor.md) [film_category](film_category.md) [inventory](inventory.md) |  |  |
| title | varchar(128) |  | false |  |  |  |  |
| description | text |  | true |  |  |  |  |
| release_year | year |  | true |  |  |  |  |
| language_id | tinyint unsigned |  | false |  |  | [language](language.md) |  |
| original_language_id | tinyint unsigned |  | true |  |  | [language](language.md) |  |
| rental_duration | tinyint unsigned | 3 | false |  |  |  |  |
| rental_rate | decimal(4,2) | 4.99 | false |  |  |  |  |
| length | smallint unsigned |  | true |  |  |  |  |
| replacement_cost | decimal(5,2) | 19.99 | false |  |  |  |  |
| rating | enum('G','PG','PG-13','R','NC-17') | G | true |  |  |  |  |
| special_features | set('Trailers','Commentaries','Deleted Scenes','Behind the Scenes') |  | true |  |  |  |  |
| last_update | timestamp | CURRENT_TIMESTAMP | false | DEFAULT_GENERATED on update CURRENT_TIMESTAMP |  |  |  |

## Constraints

| Name | Type | Definition |
| ---- | ---- | ---------- |
| fk_film_language | FOREIGN KEY | FOREIGN KEY (language_id) REFERENCES language (language_id) |
| fk_film_language_original | FOREIGN KEY | FOREIGN KEY (original_language_id) REFERENCES language (language_id) |
| PRIMARY | PRIMARY KEY | PRIMARY KEY (film_id) |

## Indexes

| Name | Definition |
| ---- | ---------- |
| idx_fk_language_id | KEY idx_fk_language_id (language_id) USING BTREE |
| idx_fk_original_language_id | KEY idx_fk_original_language_id (original_language_id) USING BTREE |
| idx_title | KEY idx_title (title) USING BTREE |
| PRIMARY | PRIMARY KEY (film_id) USING BTREE |

## Relations

![er](film.svg)

---

> Generated by [tbls](https://github.com/k1LoW/tbls)
