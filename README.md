# SQL Ödevler ve Pratikler
## Ödev1
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
- film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
> Select title,
> description
> from film
> order by title asc;
- film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
> Select *
> from film
> where film.length >60 and film.length<75;
- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
> Select *
> from film
> where film.rental_rate=0.99 and (film.replacement_cost=12.99 or film.replacement_cost=28.99);
- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
Last Name=Smith
- film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
> Select * from film where film.length <50 and (film.rental_rate<>2.99 and film.rental_rate<>4.99 );
## Ödev2
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
- film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
> Select * from film where replacement_cost between 12.99 and 16.98;
- actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
> Select first_name,last_name from actor where first_name in( 'Penelope', 'Nick','Ed' );
- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
> Select * from film where rental_rate in( 0.99, 2.99, 4.99) and replacement_cost in (12.99, 15.99, 28.99) order by rental_rate ;
## Ödev3
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
- country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
> SELECT country
FROM country
WHERE 
country LIKE 'A%a';
- country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
> SELECT country
FROM country
WHERE 
country LIKE '_____%n';
- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
> SELECT title
FROM film
WHERE 
title ILIKE '%t%%t%%t%%T%' ;
- film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
> SELECT *
FROM film
WHERE 
title LIKE 'C%' and film.length > 90 and rental_rate=2.99 ;
## Ödev4
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
- film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
>SELECT DISTINCT replacement_cost 
FROM film
;
- film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
>21
- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
> SELECT COUNT (title)
FROM film
WHERE title like 'T%' and rating='G'
;

>Cevap= 9
- country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
>SELECT count(country)
FROM country
WHERE country like '_____'
;

>Cevap=13
- city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
> SELECT count(city)
FROM city
WHERE city like 'R%' or city like  '%r'
;

> Cevap = 45
## Ödev5
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
> SELECT title
FROM film
WHERE title like '%n'
Order by
film.length DESC
limit 5
;
- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
> SELECT title from film
WHERE title ILIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5;
- customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
> SELECT * from customer
WHERE store_id=1
ORDER BY last_name
LIMIT 4;
## Ödev6
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
- film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
>SELECT AVG(rental_rate) from film
;

> Cevap=2.98
- film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
>SELECT COUNT(title) from film
WHERE title LIKE 'C%';

>Cevap=92
- film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
> SELECT length from film where rental_rate=0.99
order by film.length
desc
limit 1
;

> Cevap=184
- film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
>SELECT count(distinct replacement_cost) from film where film.length>150
;

>Cevap=21
## Ödev7
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
- film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
> SELECT rating, count(*)  from film group by rating
;
- film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
> SELECT replacement_cost, count(*)  from film group by replacement_cost having count(replacement_cost)>50
;
- customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
>SELECT store_id, count(customer_id)  from customer group by store_id 
;

>Cevap:326
       273
- city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
>SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;

>Cevap=44	60
## Ödev8
-test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
>CREATE TABLE employee (
  id Serial PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(100),
  birthday DATE
);
- Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
>insert into employee (id, name, email, birthday) values (1, 'Modesta', 'msquibbs0@tinypic.com', '2002/01/06');
insert into employee (id, name, email, birthday) values (2, 'Arden', 'abeckey1@wordpress.org', '2020/06/08');

> veri eklendi
- Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
> Update 1
>UPDATE employee 
>SET name = 'Hüseyin'
>WHERE id = 1;

> Update 2
>UPDATE employee 
>SET email = 'test@test.com'
>WHERE birthday > '1996-03-16';

> Update 3
UPDATE employee 
SET birthday = '1992-11-14'
WHERE name ILIKE 'H%';

>Update 4
UPDATE employee 
SET email = 'update4@gmail.com'
WHERE id > 45
RETURNING *;

>Update 5
UPDATE employee 
SET name = CONCAT(name,' GMAIL')
WHERE email LIKE '%@gmail.com'
RETURNING *;
- Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

-- DELETE 1
DELETE FROM employee
WHERE email LIKE '%@java.com'
;

-- DELETE 2
DELETE FROM employee
WHERE id IN(16,17,18)
;

-- DELETE 3
DELETE FROM employee
WHERE id BETWEEN 5 AND 12
;

-- DELETE 4
DELETE FROM employee
WHERE birthday < '"2000-06-08"'
;

-- DELETE 5
DELETE FROM employee
WHERE name LIKE 'ınge%'
;
## Ödev9
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
- city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
> SELECT city.city, country.country
FROM city
INNER JOIN country ON city.country_id =country.country_id;
- customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
> SELECT first_name, last_name,payment_id
FROM customer  
INNER JOIN payment  ON payment.customer_id =customer.customer_id;
- customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
> SELECT rental_id,first_name,last_name
FROM customer  
INNER JOIN rental  ON rental.customer_id =customer.customer_id;
## Ödev10
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.
- city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
> SELECT city, country
FROM city
LEFT JOIN country
ON city.country_id = country.country_id;
- customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
> SELECT payment_id,first_name,last_name
FROM payment
RIGHT JOIN customer
ON payment.customer_id =customer.customer_id;
- customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
> SELECT rental_id,first_name,last_name
FROM customer  
FULL JOIN rental  ON rental.customer_id =customer.customer_id;
