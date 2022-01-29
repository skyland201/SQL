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

