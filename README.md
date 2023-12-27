## SQL-Queries
#### 1. film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
```sql
SELECT DISTINCT(replacement_cost) FROM film;
````
#### 2. film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
```sql
SELECT COUNT(DISTINCT(replacement_cost)) FROM film;
```
#### 3. film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```sql
SELECT COUNT(*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
```
#### 4. country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```sql
SELECT COUNT(*) FROM country
WHERE LENGTH(country) = 5;
```
#### 5. city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
```sql
SELECT COUNT(*) FROM city
WHERE city ILIKE '%R';
```
#### 6. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```sql
select * from film
where title like '%n'
order by length desc
limit 5;
```
#### 7. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız
```sql
select * from film
where title like '%n'
order by length asc
offset 5
limit 5
```
#### 8. customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```sql
select * from customer
where store_id = 1
order by last_name desc
limit 4
```
#### 9. film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
```sql
select round(avg(rental_rate), 2) from film
```
#### 10. film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
```sql
select count(*) from film
where title like 'C%'
```
#### 11. film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```sql
select max(length) from film
where rental_rate = 0.99
```
#### 12. film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```sql
select count(distinct(replacement_cost)) from film
where length > 150
```
#### 13. film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
```sql
select rating from film
group by rating;
```
#### 14. film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
```sql
select replacement_cost, count(*) from film
group by replacement_cost
having count(*) > 50;
```
#### 15.  customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 
```sql
select store_id, count(*) from customer
group by store_id
```
#### 16. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
```sql
select country_id, count(*) from city
group by country_id
order by count(*) desc
limit 1;
```
