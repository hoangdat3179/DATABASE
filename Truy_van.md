Câu 1

```sql
SELECT title,description,length,special_features,rating,rental_rate FROM `film`
WHERE rating = 'PG'
AND special_features = 'Deleted Scenes'
AND rental_rate < 2.99
```

Câu 2
```sql
SELECT title,description,length,special_features,rating,rental_rate,(SELECT AVG(rental_rate) FROM film) Trungbinhcong FROM `film`
WHERE rating = 'G'
AND rental_rate > (SELECT AVG(rental_rate) FROM film)
```

Câu 3
```sql
SELECT title,description,length,special_features,rating,rental_rate FROM `film`
WHERE special_features NOT LIKE '%Deleted Scenes%'
```