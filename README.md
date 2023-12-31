# Patika SQL Eğitimi


<img align="left" alt="PNG" src="https://github.com/mehmetdurankaya/SQL/blob/master/Assets/sqllogo.png" width="450" height="250"/>

# [ödev-1](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-1) 
# [ödev-2](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-2) 
# [ödev-3](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-3) 
# [ödev-4](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-4) 
# [ödev-5](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-5) 
# [ödev-6](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-6) 
# [ödev-7](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV%20-7) 
# [ödev-8](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-8)
# [ödev-9](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-9)
# [ödev-10](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-10)
# [ödev-11](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-11)
# [ödev-12](https://github.com/mehmetdurankaya/SQL/blob/master/ODEV-12)


### ÖDEV-1
<div>
<span font-size:20px>
--Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

	SELECT * FROM film;
	
-- film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

	SELECT title, descriptilon FROM film;
	
-- film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
	
	SELECT * FROM film
	WHERE length > 60 
	AND length < 75;
-- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
	
	SELECT * FROM film
	WHERE rental_rate=0.99 
	AND replacement_cost=12.99 
	OR replacement_cost= 28.99;
	
-- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
	
	SELECT last_name  from customer WHERE first_name= 'Mary';
	
-- film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
	
	SELECT * FROM film 
	WHERE NOT length<= 50
	AND NOT rental_rate=2.99 
	OR rental_rate =4.99;



### ÖDEV 2

-- 1- film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
	
	SELECT * FROM film 
	WHERE   replacement_cost 
	BETWEEN 12.99  AND 16.99;

-- 2- actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
	
        SELECT first_name, last_name FROM actor
	WHERE first_name IN('Penelope','Nick','Ed');

-- 3- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
	
        SELECT * FROM film 
	WHERE rental_rate IN (0.99,2.99,4.99)
	AND replacement_cost IN (12.99,15.90,28.99);

 
 ### ÖDEV 3

-- 1- country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
	
	SELECT 
	country 
	FROM country
	WHERE country LIKE 'A%a';

-- 2- country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
	
	SELECT
	country 
	FROM country 
	WHERE length(country) >= 6 AND RIGHT(country,1)='n';

-- 3- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
	
	SELECT title 
	FROM film 
	WHERE length(title) >= 4 AND title ILIKE '%T%'; 


-- 4- film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
	
	SELECT * 
	FROM film 
	WHERE title LIKE 'C%' AND length > 90 AND rental_rate=2.99;
 
### ÖDEV 4
-- 1- film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

	SELECT DISTINCT replacement_cost from film

-- 2- film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

	SELECT COUNT(DISTINCT replacement_cost) from film

-- 3- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

	SELECT COUNT(*) AS count_start_T_and_G
	FROM film
	WHERE title LIKE 'T%' AND rating = 'G';


-- 4- country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

	SELECT COUNT(*) FROM country 
	WHERE LENGTH(country)=5;

-- 5- city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

	SELECT COUNT(*)
	FROM city
	WHERE city LIKE '%R' OR city LIKE '%r';

### ÖDEV 5
--1- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

	SELECT title, length
	FROM film
	WHERE title LIKE '%n'
	ORDER BY length DESC
	LIMIT 5;

--2- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
	
 	SELECT title, length
	FROM film
	WHERE title LIKE '%n'
	ORDER BY length ASC
	OFFSET 5
	LIMIT 5;

--3- customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

	SELECT last_name, store_id FROM customer
	WHERE store_id=1
	ORDER BY last_name DESC 
	LIMIT 4;

 
### ÖDEV 6
 --1- film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
	
 	SELECT ROUND(AVG(rental_rate),3)
  	FROM film;


--2- film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

	SELECT COUNT(*) FROM film
 	WHERE  title LIKE 'C%';

--3- film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

	SELECT title, length
 	FROM film 
	WHERE
 	rental_rate =0.99 ORDER BY length DESC LIMIT 1; 

--4- film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

	SELECT COUNT(DISTINCT replacement_cost) FROM film
 	WHERE length > 150;
### ÖEDEV 7 



--1- film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

	SELECT rating, COUNT(*) 
	FROM film
	GROUP BY rating;

--2- film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

	SELECT replacement_cost, COUNT(*)
	FROM film
	GROUP BY replacement_cost
	HAVING COUNT(*) > 50
	ORDER BY COUNT(*) DESC;

--3- customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

	SELECT country_id, COUNT(*) as city_count
	FROM city
	GROUP BY country_id
	ORDER BY city_count DESC
	LIMIT 1;

   </span>
</div>
