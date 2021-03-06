## PROJECT EXAMPLE DVDRENTAL:

#### .... HW - 1....

1-) film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

```
-> SELECT title, description FROM film;
```

2-) film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

```
-> SELECT * FROM film WHERE length > 60 AND length < 75;
```

3-) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

```
-> SELECT * FROM film WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
```

4-) customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

```
-> SELECT last_name FROM customer WHERE first_name = 'Mary';
```

5-) film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

```
-> SELECT * FROM film WHERE NOT length > 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);
```

#### .... HW - 2....
1-) film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız 
( BETWEEN - AND yapısını kullanınız.)
```
-> SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```
2-) .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. 
( IN operatörünü kullanınız.)
```
-> SELECT first_name, last_name FROM actor WHERE first_name IN ('Penelope', 'Nick', 'Ed');
```
3-) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. 
( IN operatörünü kullanınız.)
```
-> SELECT * FROM film WHERE rental_rate IN (0.99, 2.99, 499) AND replacement_cost IN(12.99, 15,99, 28.99);
```
#### .... HW - 3....

1-) country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
```
-> SELECT country FROM country WHERE country LIKE 'A%a';
```
2-) country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
```
-> SELECT country FROM country WHERE country LIKE '%_____n';
```
3-) film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
```
-> SELECT title FROM film WHERE title ILIKE '%T%T%T%T'; 
```
4-) film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri 
sıralayınız.
```
-> SELECT * FROM film WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;
```
#### .... HW - 4....
1-) film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
```
-> SELECT DISTINCT replacement_cost FROM film;
```
2-) film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
```
-> SELECT COUNT(DISTINCT replacement_cost) FROM film;
```
3-) film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```
-> SELECT COUNT(title) FROM film WHERE title LIKE 'T%' AND rating = 'G';
```
4-) country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```
-> SELECT COUNT(country) FROM country WHERE country LIKE '_____';
```
5-) city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
```
-> SELECT COUNT(city) FROM city WHERE city ILIKE '%R';
```

#### .... HW - 5....
1-) film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```
-> SELECT * FROM film  WHERE title LIKE '%n'ORDER BY length LIMIT 5;
```
2-) film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
```
-> SELECT * FROM film WHERE title LIKE '%n' ORDER BY length OFFSET 5 LIMIT 5;
```
3-) customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```
-> SELECT * FROM customer WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;
```
#### .... HW - 6....
1-) film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
```
-> SELECT AVG (rental_rate) FROM film;
```
2-) film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
```
->SELECT COUNT(title) FROM film WHERE title LIKE 'C%';
```
3-) film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```
-> SELECT MAX(length) FROM film WHERE rental_rate = 0.99;
```
4-) film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```
-> SELECT COUNT(DISTINCT(replacement_cost)) FROM film WHERE length < 150;
```

#### .... HW - 7....
1-) film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
```
-> SELECT rating, COUNT(*) FROM film GROUP BY rating;
```
2-) film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan 
replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
```
-> SELECT replacement_cost, COUNT(*) FROM film GROUP BY  replacement_cost HAVING COUNT(*) > 50;
```
3-) customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 
```
-> SELECT store_id, COUNT(*) FROM customer GROUP BY store_id;
```
4-) 4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı 
barındıran country_id bilgisini ve şehir sayısını paylaşınız.
```
-> SELECT country_id, COUNT(*) FROM city  GROUP BY country_id ORDER BY MAX(city) DESC LIMIT 1;
```

#### .... HW - 8....
1-) test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
```
-> CREATE TABLE employee(
	ID SERIAL PRIMARY KEY,
	nameandsurname VARCHAR(50) NOT NULL,
	birthday DATE,
	email VARCHAR(100) 
)

SELECT * FROM employee;
```
2-) Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
```
-> --SELECT * FROM employee; 
insert into employee (nameandsurname, birthday, email) values ('Averil', '1918-08-16', 'agrinham0@google.ca');
insert into employee (nameandsurname, birthday, email) values ('Ardra', '1957-05-18', null);
insert into employee (nameandsurname, birthday, email) values ('Emelda', null, 'eloweth2@wufoo.com');
insert into employee (nameandsurname, birthday, email) values ('Mata', '1905-12-25', 'mbushel3@amazon.co.uk');
insert into employee (nameandsurname, birthday, email) values ('Richart', '1933-12-24', 'rpetican4@vk.com');
insert into employee (nameandsurname, birthday, email) values ('Corly', '1955-09-06', 'cocaine5@guardian.co.uk');
insert into employee (nameandsurname, birthday, email) values ('Nap', '1936-09-22', 'ninstone6@virginia.edu');
insert into employee (nameandsurname, birthday, email) values ('Johnna', '1989-11-29', 'jhugenin7@umich.edu');
insert into employee (nameandsurname, birthday, email) values ('Sileas', '1912-07-02', null);
insert into employee (nameandsurname, birthday, email) values ('Cecilio', '1940-04-08', 'ctrenholme9@independent.co.uk');
insert into employee (nameandsurname, birthday, email) values ('Jocelyne', null, 'jplaschkea@nytimes.com');
insert into employee (nameandsurname, birthday, email) values ('Kimbell', null, 'kbowshireb@ocn.ne.jp');
insert into employee (nameandsurname, birthday, email) values ('Puff', '1976-07-09', 'pdellortoc@ed.gov');
insert into employee (nameandsurname, birthday, email) values ('Candy', '1948-09-22', 'clambotd@mediafire.com');
insert into employee (nameandsurname, birthday, email) values ('Jena', '1954-07-17', 'jhintzee@marketwatch.com');
insert into employee (nameandsurname, birthday, email) values ('Vincents', '1941-12-02', 'vparmerf@patch.com');
insert into employee (nameandsurname, birthday, email) values ('Tallie', '1901-03-26', 'tbuckyg@soundcloud.com');
insert into employee (nameandsurname, birthday, email) values ('Maddie', null, 'mhoovarth@google.com.hk');
insert into employee (nameandsurname, birthday, email) values ('Annabal', null, 'aknowlsoni@hostgator.com');
insert into employee (nameandsurname, birthday, email) values ('Sonya', '1951-10-24', 'sitzkovwitchj@hubpages.com');
insert into employee (nameandsurname, birthday, email) values ('Raddy', '1960-01-13', 'roglethorpek@linkedin.com');
insert into employee (nameandsurname, birthday, email) values ('Philippe', '1974-03-21', 'pbrilonl@people.com.cn');
insert into employee (nameandsurname, birthday, email) values ('Tades', null, 'tblanningm@moonfruit.com');
insert into employee (nameandsurname, birthday, email) values ('Martha', '1948-10-10', 'mchestnutn@mtv.com');
insert into employee (nameandsurname, birthday, email) values ('Dietrich', '1938-09-19', 'dofinano@sbwire.com');
insert into employee (nameandsurname, birthday, email) values ('Camey', '2014-05-02', 'ccuffleyp@issuu.com');
insert into employee (nameandsurname, birthday, email) values ('Lyndell', '1994-03-13', 'lbonhommeq@intel.com');
insert into employee (nameandsurname, birthday, email) values ('Lamond', null, null);
insert into employee (nameandsurname, birthday, email) values ('Blake', '1974-10-03', 'bhulless@issuu.com');
insert into employee (nameandsurname, birthday, email) values ('Haywood', '1901-09-19', 'hoganesiant@ebay.co.uk');
insert into employee (nameandsurname, birthday, email) values ('Carmine', '1936-11-18', 'cburberryu@google.co.jp');
insert into employee (nameandsurname, birthday, email) values ('Martainn', '1991-10-08', 'mcruzv@dagondesign.com');
insert into employee (nameandsurname, birthday, email) values ('Osmond', null, 'ofauntw@mail.ru');
insert into employee (nameandsurname, birthday, email) values ('Aili', '1950-01-17', 'acortesx@google.cn');
insert into employee (nameandsurname, birthday, email) values ('Celinda', '1945-05-16', 'cpardony@washingtonpost.com');
insert into employee (nameandsurname, birthday, email) values ('Arlyne', '1907-11-05', 'agrishmanovz@unblog.fr');
insert into employee (nameandsurname, birthday, email) values ('Cortney', null, 'ccamous10@washington.edu');
insert into employee (nameandsurname, birthday, email) values ('North', '1963-11-14', 'nrawlison11@economist.com');
insert into employee (nameandsurname, birthday, email) values ('Anjanette', '1993-11-18', 'atatterton12@istockphoto.com');
insert into employee (nameandsurname, birthday, email) values ('Dominick', '1985-11-28', null);
insert into employee (nameandsurname, birthday, email) values ('Rita', '1904-04-02', 'rhiorn14@flickr.com');
insert into employee (nameandsurname, birthday, email) values ('Clareta', null, 'cvanderhoven15@hugedomains.com');
insert into employee (nameandsurname, birthday, email) values ('Isidor', '1987-11-19', 'ipoad16@about.com');
insert into employee (nameandsurname, birthday, email) values ('Adina', '1911-04-11', 'asayton17@ucoz.com');
insert into employee (nameandsurname, birthday, email) values ('Archibold', '1909-03-20', 'aruprechter18@noaa.gov');
insert into employee (nameandsurname, birthday, email) values ('Norri', '1993-01-05', 'nstelle19@ebay.com');
insert into employee (nameandsurname, birthday, email) values ('Cesare', '1954-09-04', 'cpaulino1a@moonfruit.com');
insert into employee (nameandsurname, birthday, email) values ('Cyril', '1940-06-02', 'ckaemena1b@oracle.com');
insert into employee (nameandsurname, birthday, email) values ('Bud', '1902-05-13', 'bscherer1c@hhs.gov');
insert into employee (nameandsurname, birthday, email) values ('Dulcinea', null, 'dcribbott1d@businessinsider.com');

--SELECT * FROM employee; 
```
3-) Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```
-> UPDATE employee
SET nameandsurname = 'Rebecca',
	birthday = '1991-09-19',
	email = 'rtieman1g@twitpic.com'
WHERE id = 31;

UPDATE employee
SET nameandsurname = 'Elmore',
	birthday = '1984-02-05',
	email = 'ewhitnell1h@baidu.com'
WHERE id = 32;

UPDATE employee
SET nameandsurname = 'Daniela',
	birthday = '1974-07-05',
	email = 'dkerslake1i@histats.com'
WHERE id = 33;

UPDATE employee
SET nameandsurname = 'Felita',
	birthday = '1944-07-15',
	email = 'fkivelle1f@bravesites.com'
WHERE id = 34;

UPDATE employee
SET nameandsurname = 'Rosalinda',
	birthday = '2000-11-18',
	email = 'rosalinda@rosites.com'
WHERE id = 35;

--SELECT * FROM employee;
```

4-) Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```
-> --SELECT * FROM employee;

DELETE FROM employee
WHERE id = 49;

DELETE FROM employee
WHERE id = 48;

DELETE FROM employee
WHERE id = 47;

DELETE FROM employee
WHERE id = 46;

DELETE FROM employee
WHERE id = 45;

--SELECT * FROM employee;
```

#### .... HW - 9....
1-) city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```
-> SELECT city.city, country.country FROM city INNER JOIN country ON city.country_id = country.country_id;
```
2-) customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name 
isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```
-> SELECT payment.payment_id, customer.first_name, customer.last_name FROM customer INNER JOIN payment ON customer.customer_id = payment.customer_id;
```
3-) customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini 
birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```
-> SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer INNER JOIN rental ON customer.customer_id = rental.customer_id;
```

#### .... HW - 10....

1-) city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
```
-> SELECT city, country FROM city LEFT JOIN country ON city.country_id = country.country_id;
```
2-) customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu  yazınız.
```
-> SELECT payment_id, first_name, last_name FROM customer RIGHT JOIN payment ON customer.customer_id = payment.customer_id;
```
3-) customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu 
yazınız.
```
-> SELECT rental_id, first_name, last_name FROM customer FULL JOIN rental ON customer.customer_id = rental.customer_id;
```

#### .... HW - 11....

1-) actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
```
-> (
SELECT first_name FROM actor 
ORDER BY first_name
)
UNION
(
SELECT first_name FROM customer 
ORDER BY first_name
);
```
2-) actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
```
-> (
SELECT first_name FROM actor
)
INTERSECT
(
SELECT first_name FROM customer
);
```
3-) actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
```
-> (
SELECT first_name FROM actor
)
EXCEPT
(
SELECT first_name FROM customer
);
```
4-) İlk 3 sorguyu tekrar eden veriler için de yapalım.
```
-> (
SELECT first_name FROM actor 
ORDER BY first_name
)
UNION ALL
(
SELECT first_name FROM customer 
ORDER BY first_name
);
```
```
-> (
SELECT first_name FROM actor 
ORDER BY first_name
)
INTERSECT ALL
(
SELECT first_name FROM customer 
ORDER BY first_name
);
```
```
-> (
SELECT first_name FROM actor 
ORDER BY first_name
)
EXCEPT ALL
(
SELECT first_name FROM customer 
ORDER BY first_name
);
```

#### .... HW - 12....

1-) film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
```
-> SELECT COUNT(*) FROM film WHERE lenght > (SELECT AVG(length) FROM film);
```
2-) film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
```
-> SELECT COUNT(*) FROM film WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);
```
3-) film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.
```
-> SELECT title, rental_rate, replacement_cost FROM film 
WHERE rental_rate = (SELECT MIN(rental_rate) FROM film) AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);
```
4-) payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
```
-> SELECT customer FROM payment WHERE customer_id = (SELECT MAX(customer_id) FROM payment); 
-> SELECT * FROM customer
 WHERE customer_id =
 ANY
 (
 	SELECT customer_id FROM payment
 	GROUP BY customer_id
 	ORDER BY COUNT(*) DESC
 	LIMIT 1
 );
```
