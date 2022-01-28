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

