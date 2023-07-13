# SQL-Hw
## Homework1
1)film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

      SELECT title, description FROM film
   
2)film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

    SELECT * FROM film
    WHERE length > 60 AND length < 75;
    
3)film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

    SELECT * FROM film
    WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99;
    
   4)customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
   
    SELECT last_name FROM customer
    WHERE first_name = 'Mary';
    
5)film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

    SELECT * FROM film
    WHERE NOT length>50 AND  NOT (rental_rate = 2.99 OR rental_rate  = 4.99)

## Homework2

1)film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

      SELECT * FROM film
      WHERE replacement_cost BETWEEN 12.99 AND 16.99
            
2)actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

      SELECT first_name , last_name  FROM actor 
      WHERE first_name  IN('Penelope', 'Nick', 'Ed' )

3)film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

      SELECT *  FROM film 
      WHERE rental_rate  IN(0.99, 2.99, 4.99) AND replacement_cost  IN (12.99, 15.99, 28.99)

## Homework3

1)country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.


            SELECT *  FROM country
            WHERE country LIKE 'A%a'

2)country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

            SELECT *  FROM country
            WHERE country LIKE '______%n'

3)film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

            SELECT title  FROM film
            WHERE title ILIKE '%T%T%T%T%'

4)film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

            SELECT *  FROM film
            WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99

## Homework4

1)film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

            SELECT DISTINCT replacement_cost  FROM film

2)film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

            SELECT COUNT (DISTINCT replacement_cost)  FROM film

3)film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

            SELECT COUNT (*)  FROM film
            WHERE title LIKE '%T' AND rating='G'

4)country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

            SELECT COUNT (*)  FROM country
            WHERE country LIKE '_____'

5)city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
            
            SELECT COUNT (*)  FROM city
            WHERE city ILIKE '%R'

## Homework 5

1)film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

            SELECT title, length  FROM film
            WHERE title LIKE '%n'
            ORDER BY length DESC
            LIMIT 5


2)film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

            SELECT title, length  FROM film
            WHERE title LIKE '%n'
            ORDER BY length
            OFFSET 5
            LIMIT 5


3)customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

            SELECT *  FROM customer
            WHERE store_id = 1
            ORDER BY last_name DESC 
            LIMIT 4

## Homework 6

1)film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

            SELECT MIN(rental_rate)  FROM film

2)film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

            SELECT COUNT(*)  FROM film
            WHERE title LIKE 'C%'

3)film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

            SELECT MAX(length)  FROM film
            WHERE rental_rate = 0.99
            
4)film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

            SELECT COUNT(DISTINCT replacement_cost )  FROM film
            WHERE length > 150

## Homework 7

1)film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

            SELECT rating, COUNT (*) FROM film
            GROUP BY rating


2)film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

            SELECT replacement_cost, COUNT (*) FROM film
            GROUP BY replacement_cost
            HAVING COUNT(*)>50


3)customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

            SELECT store_id, COUNT (*) FROM customer
            GROUP BY store_id


4)city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
            
            SELECT country_id, COUNT (*) FROM city
            GROUP BY country_id
            ORDER BY COUNT(*) DESC
            LIMIT 1

## Homework 8
1)test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

            CREATE TABLE employee(
             id INTEGER, name VARCHAR(50), birthday DATE, email VARCHAR(100));

2)Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

            insert into employee (id, name, birthday, email) values (1, 'Kerk', '2004-01-19', 'kbothie0@wired.com');
            insert into employee (id, name, birthday, email) values (2, 'Holly', '1978-05-07', 'hlammin1@digg.com');
            insert into employee (id, name, birthday, email) values (3, 'Dominica', '2014-03-13', 'dsalamon2@storify.com');
            insert into employee (id, name, birthday, email) values (4, 'Roselin', '2011-12-29', 'rtrew3@deliciousdays.com');
            insert into employee (id, name, birthday, email) values (5, 'Con', '1911-10-19', 'cgabe4@ning.com');
            insert into employee (id, name, birthday, email) values (6, 'Birch', '2020-05-06', 'bgauden5@goodreads.com');
            insert into employee (id, name, birthday, email) values (7, 'Aldwin', '1919-08-03', 'asore6@google.com.au');
            insert into employee (id, name, birthday, email) values (8, 'Brinna', '1962-09-07', 'bzorer7@nifty.com');
            insert into employee (id, name, birthday, email) values (9, 'Charin', '1968-03-05', 'cgussin8@thetimes.co.uk');
            insert into employee (id, name, birthday, email) values (10, 'Lionello', '1989-01-10', 'lfowlestone9@hexun.com');
            insert into employee (id, name, birthday, email) values (11, 'Robby', '1940-11-04', 'rshorthousea@ed.gov');
            insert into employee (id, name, birthday, email) values (12, 'Beatriz', '1944-11-10', 'bswindonb@census.gov');
            insert into employee (id, name, birthday, email) values (13, 'Mandie', '1907-12-07', 'mhiggenc@tripod.com');
            insert into employee (id, name, birthday, email) values (14, 'Jamey', '1910-01-23', 'jnicklind@example.com');
            insert into employee (id, name, birthday, email) values (15, 'Guglielmo', '1993-11-09', 'gmcrille@google.ru');
            insert into employee (id, name, birthday, email) values (16, 'Marlena', '1977-08-13', 'mcastagnetof@wufoo.com');
            insert into employee (id, name, birthday, email) values (17, 'Demetris', '2013-06-17', 'dmeatong@intel.com');
            insert into employee (id, name, birthday, email) values (18, 'Friederike', '1902-08-23', 'fciobutaruh@aol.com');
            insert into employee (id, name, birthday, email) values (19, 'Alyson', '2020-10-31', 'acawstoni@china.com.cn');
            insert into employee (id, name, birthday, email) values (20, 'Cointon', '1958-01-19', 'cstacyj@google.com.hk');
            insert into employee (id, name, birthday, email) values (21, 'Dina', '1943-12-20', 'dvassiek@hud.gov');
            insert into employee (id, name, birthday, email) values (22, 'Marcelo', '1960-05-29', 'mpetyaninl@kickstarter.com');
            insert into employee (id, name, birthday, email) values (23, 'Tome', '1957-07-22', 'tlowriem@craigslist.org');
            insert into employee (id, name, birthday, email) values (24, 'Melesa', '1912-09-24', 'mbilbreyn@technorati.com');
            insert into employee (id, name, birthday, email) values (25, 'Tuckie', '2001-10-09', 'tlestrangeo@google.fr');
            insert into employee (id, name, birthday, email) values (26, 'Mal', '2019-04-09', 'mveckp@etsy.com');
            insert into employee (id, name, birthday, email) values (27, 'Dana', '2010-01-31', 'dogilbyq@about.me');
            insert into employee (id, name, birthday, email) values (28, 'Carlynn', '1999-08-03', 'ccraykr@bbb.org');
            insert into employee (id, name, birthday, email) values (29, 'Alwin', '1983-09-17', 'abackwells@theguardian.com');
            insert into employee (id, name, birthday, email) values (30, 'Ellery', '1951-03-09', 'ejohananofft@printfriendly.com');
            insert into employee (id, name, birthday, email) values (31, 'Colene', '1984-11-07', 'cvicku@hostgator.com');
            insert into employee (id, name, birthday, email) values (32, 'Janean', '1960-05-07', 'jpledgev@accuweather.com');
            insert into employee (id, name, birthday, email) values (33, 'Martyn', '1977-11-23', 'mchampew@google.co.uk');
            insert into employee (id, name, birthday, email) values (34, 'Wilmette', '1959-04-07', 'wmoughtinx@state.gov');
            insert into employee (id, name, birthday, email) values (35, 'Vida', '1939-10-03', 'vheildy@buzzfeed.com');
            insert into employee (id, name, birthday, email) values (36, 'Carling', '2011-12-20', 'cchatainz@disqus.com');
            insert into employee (id, name, birthday, email) values (37, 'Barris', '1922-02-19', 'bpinard10@uiuc.edu');
            insert into employee (id, name, birthday, email) values (38, 'Cymbre', '2021-12-07', 'cnewvill11@skyrock.com');
            insert into employee (id, name, birthday, email) values (39, 'Yul', '1911-09-27', 'ytolfrey12@desdev.cn');
            insert into employee (id, name, birthday, email) values (40, 'Gerick', '1985-12-07', 'grhucroft13@goo.gl');
            insert into employee (id, name, birthday, email) values (41, 'Ami', '1911-01-13', 'awarrilow14@jimdo.com');
            insert into employee (id, name, birthday, email) values (42, 'Peirce', '1976-12-03', 'prottcher15@deviantart.com');
            insert into employee (id, name, birthday, email) values (43, 'Dora', '1985-05-22', 'dnaptin16@shareasale.com');
            insert into employee (id, name, birthday, email) values (44, 'Marris', '2007-11-27', 'miowarch17@sohu.com');
            insert into employee (id, name, birthday, email) values (45, 'Lorena', '1945-08-14', 'ldanielski18@merriam-webster.com');
            insert into employee (id, name, birthday, email) values (46, 'Othelia', '1989-01-23', 'obrede19@tamu.edu');
            insert into employee (id, name, birthday, email) values (47, 'Dougy', '1961-05-30', 'dgammidge1a@aol.com');
            insert into employee (id, name, birthday, email) values (48, 'Illa', '1927-08-04', 'icallar1b@reuters.com');
            insert into employee (id, name, birthday, email) values (49, 'Lorenzo', '1980-07-28', 'ldight1c@wisc.edu');
            insert into employee (id, name, birthday, email) values (50, 'Karmen', '1995-06-05', 'kdoerren1d@comsenz.com');

      
3)Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
            UPDATE employee
            SET name = 'Gökçe'
            WHERE id=7;

            UPDATE employee
            SET name = 'Ece', 
                birthday = '2007-07-17'
            WHERE name='Gokce';

            UPDATE employee
            SET name = 'Ahmet'
            WHERE birthday = '2001-10-10';

            UPDATE employee
            SET name = 'Ela',
      	birthday= '2005-09-19',
      	email='ela2005@gmail.com'
            WHERE id=10;

            UPDATE employee
            SET email='ela200509@gmail.com'
            WHERE id=10;
            
4)Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

            DELETE FROM employee
            WHERE name = 'Ela';

            DELETE FROM employee
            WHERE id = 10;

            DELETE FROM employee
            WHERE name LIKE 'C%'

            DELETE FROM employee
            WHERE email LIKE '%sohu.com'

            DELETE FROM employee
            WHERE birthday = '1980-01-01'

 ## Homework 9
 1)city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

            SELECT city, country
            FROM city
            INNER JOIN country
            ON city.city_id = country.country_id

 
 2)customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

            SELECT first_name, last_name, payment_id
            FROM customer
            INNER JOIN payment
            ON payment.customer_id=customer.customer_id;
 
3)customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.  

            SELECT first_name, last_name, rental_id
            FROM customer
            INNER JOIN rental
            ON rental.rental_id=customer.customer_id;

## Homework 10
1)city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

            SELECT city, country FROM city
            LEFT JOIN country ON city.country_id=country.country_id;

2)customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

      SELECT first_name, last_name, payment_id FROM customer
      RIGHT JOIN payment ON payment.customer_id=customer.customer_id;

3)customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

            SELECT first_name, last_name, rental_id FROM rental
            FULL JOIN customer ON rental.customer_id=customer.customer_id;

## Homework 11
1)actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

            (
            SELECT first_name FROM actor
            )
            UNION
            (
            SELECT first_name FROM customer
            );
            
2)actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

            (
            SELECT first_name FROM actor
            )
            INTERSECT
            (
            SELECT first_name FROM customer
            );

3)actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

            (
            SELECT first_name FROM actor
            )
            EXCEPT
            (
            SELECT first_name FROM customer
            );
            
4)İlk 3 sorguyu tekrar eden veriler için de yapalım.

            (
            SELECT first_name FROM actor
            )
            UNION ALL
            (
            SELECT first_name FROM customer
            );
            
            (
            SELECT first_name FROM actor
            )
            INTERSECT ALL
            (
            SELECT first_name FROM customer
            );
            
            (
            SELECT first_name FROM actor
            )
            EXCEPT ALL
            (
            SELECT first_name FROM customer
            );
## Homework 12
1)film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

            SELECT COUNT(length) FROM film
            WHERE length > ANY
            (
            	SELECT AVG(length) FROM film
            )
            
2)film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

            SELECT COUNT(rental_rate) FROM film
            WHERE rental_rate = ALL
            (
            	SELECT MAX(rental_rate) FROM film
            )
            
3)film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

            SELECT (title),(rental_rate),(replacement_cost) FROM film
            WHERE rental_rate=
            (
            	SELECT MIN(rental_rate) FROM film
            )
            AND replacement_cost=
            (
            	SELECT MIN(replacement_cost) FROM film
            );

