## SQL-Queries
https://www.postgresqltutorial.com/wp-content/uploads/2019/05/dvdrental.zip
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
## CREATE UPDATE DELETE
#### 17. test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
```sql
create table employee(
id serial primary key,
name varchar(50) not null,
birthday date,
email varchar(100)
);
```
#### 18. Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
https://www.mockaroo.com
![sql_create](https://github.com/BunyaminOzturk/SQL-queries/assets/59489131/33a888f1-f6c7-4323-a1d0-b297f90e7aac)
```sql
insert into employee (name, birthday, email) values ('Jonie', '1959-01-26', 'jbrisbane0@gnu.org');
insert into employee (name, birthday, email) values ('Ham', '1965-12-26', 'hgidman1@answers.com');
insert into employee (name, birthday, email) values ('Juliane', '1966-09-29', 'jtreneman2@ifeng.com');
insert into employee (name, birthday, email) values ('Cher', '1915-10-18', null);
insert into employee (name, birthday, email) values ('Quinn', '1955-09-01', 'qfishlee4@t-online.de');
insert into employee (name, birthday, email) values ('Dyanne', '1949-11-15', 'dhundy5@about.me');
insert into employee (name, birthday, email) values ('Claretta', '1944-08-05', 'ccorteis6@tinypic.com');
insert into employee (name, birthday, email) values ('Gabby', '1942-01-01', 'gferagh7@harvard.edu');
insert into employee (name, birthday, email) values ('Doralyn', '1920-06-16', 'dlangworthy8@1und1.de');
insert into employee (name, birthday, email) values ('Iormina', '1936-05-14', 'ibenley9@google.co.uk');
insert into employee (name, birthday, email) values ('Algernon', '1995-12-29', 'adefriesa@economist.com');
insert into employee (name, birthday, email) values ('Free', '1926-10-03', 'fmerrigansb@newsvine.com');
insert into employee (name, birthday, email) values ('Darnall', '1948-04-13', 'dcharltonc@ucsd.edu');
insert into employee (name, birthday, email) values ('Elke', '1900-03-14', 'egallimored@un.org');
insert into employee (name, birthday, email) values ('Tyrone', '1918-05-01', 'toflahertye@baidu.com');
insert into employee (name, birthday, email) values ('Sigismundo', null, 'smathenf@miibeian.gov.cn');
insert into employee (name, birthday, email) values ('Cacilia', '1902-02-19', 'cgeertseng@va.gov');
insert into employee (name, birthday, email) values ('Muriel', null, 'mohartnedyh@sfgate.com');
insert into employee (name, birthday, email) values ('Danette', '1929-11-26', 'dkersleyi@pagesperso-orange.fr');
insert into employee (name, birthday, email) values ('Lainey', '1974-03-09', 'lhuygenj@google.es');
insert into employee (name, birthday, email) values ('Fair', '1983-05-24', 'fsexceyk@china.com.cn');
insert into employee (name, birthday, email) values ('Norine', '1990-11-18', 'nbockhl@walmart.com');
insert into employee (name, birthday, email) values ('Roderic', '1962-05-31', 'rbednellm@usnews.com');
insert into employee (name, birthday, email) values ('Fabe', '1905-01-10', 'fbrentn@ca.gov');
insert into employee (name, birthday, email) values ('Vevay', '1965-04-30', 'vmantioneo@shutterfly.com');
insert into employee (name, birthday, email) values ('Normie', null, 'nburchallp@netvibes.com');
insert into employee (name, birthday, email) values ('Valentin', '1969-10-04', null);
insert into employee (name, birthday, email) values ('Ibrahim', '1958-05-18', 'itwittyr@cloudflare.com');
insert into employee (name, birthday, email) values ('Tybie', '1918-10-18', 'ttugwells@toplist.cz');
insert into employee (name, birthday, email) values ('Irena', '1949-09-12', 'irapseyt@usa.gov');
insert into employee (name, birthday, email) values ('Grayce', '1937-05-25', 'glentonu@discovery.com');
insert into employee (name, birthday, email) values ('Nerissa', '1994-05-23', 'ncosynsv@devhub.com');
insert into employee (name, birthday, email) values ('Rudyard', '1919-10-27', 'rfindlayw@virginia.edu');
insert into employee (name, birthday, email) values ('Fiona', '1902-12-11', 'fpassx@smugmug.com');
insert into employee (name, birthday, email) values ('Bambi', '1933-11-15', 'byanshonoky@fotki.com');
insert into employee (name, birthday, email) values ('Ferd', null, 'fjagsonz@biblegateway.com');
insert into employee (name, birthday, email) values ('Cyril', '1999-10-30', 'ctarply10@google.com.br');
insert into employee (name, birthday, email) values ('Ogdon', '1908-11-30', 'odrinkhall11@google.es');
insert into employee (name, birthday, email) values ('Larry', '1940-05-15', 'lswetland12@histats.com');
insert into employee (name, birthday, email) values ('Antons', null, 'ahunday13@macromedia.com');
insert into employee (name, birthday, email) values ('Rena', null, 'rriepel14@cdc.gov');
insert into employee (name, birthday, email) values ('Irma', null, 'imcwhannel15@de.vu');
insert into employee (name, birthday, email) values ('Karissa', '1926-11-17', 'kpauler16@ustream.tv');
insert into employee (name, birthday, email) values ('Giles', '1906-02-23', 'gfirk17@seesaa.net');
insert into employee (name, birthday, email) values ('Kacey', '1911-09-04', 'kjedraszek18@artisteer.com');
insert into employee (name, birthday, email) values ('Engracia', null, 'elafuente19@cyberchimps.com');
insert into employee (name, birthday, email) values ('Antonia', null, 'aprofit1a@ovh.net');
insert into employee (name, birthday, email) values ('Janine', '1907-09-05', 'jkeitley1b@abc.net.au');
insert into employee (name, birthday, email) values ('Gilbert', '1930-02-25', 'groomes1c@gov.uk');
insert into employee (name, birthday, email) values ('Bellina', '1987-11-03', 'brodell1d@bloomberg.com');
```
#### 19. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```sql
update employee
set name = 'Hamburger'
where name = 'Ham';

update employee
set birthday = '1985-03-11'
where id = 16
returning *;

update employee
set name = 'Nena'
where name = 'Rena'
returning *;

update employee
set email = 'test@test.com'
where email = 'jbrisbane0@gnu.org'
returning *;

update employee
set name = 'Updated'
where name = 'Free'
returning *;
```
#### 20. Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```sql
delete from employee
where name = 'Juliane'
returning *;

delete from employee
where email like '%edu'
returning *;

delete from employee
where id < 5
returning *;

delete from employee
where email like 'b%'
returning *;

delete from employee
where length(name) <= 4
returning *;
```
## INNER JOIN
#### 21. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
select city, country 
from city
inner join country
on city.country_id = country.country_id;
```
#### 22. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
select payment_id, first_name, last_name
from customer
inner join payment
on customer.customer_id = payment.customer_id;
```
#### 23. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
select rental_id, first_name, last_name
from customer
inner join rental
on customer.customer_id = rental.customer_id;
```
#### 24. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
```sql
select city, country from city
left join country
on country.country_id = city.country_id;
```
#### 25. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
```sql
select payment_id, first_name, last_name from payment
right join customer
on payment.customer_id = customer.customer_id;
```
#### 26. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
```sql
select rental_id, first_name, last_name from customer
full join rental
on rental.customer_id = customer.customer_id;
```
