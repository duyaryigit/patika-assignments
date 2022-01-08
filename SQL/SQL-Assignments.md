### Patika SQL Assignments:
---
- Assignment 1

1. Sort the data in the title and description columns in the film table.

```
SELECT title, description FROM film;
```

2. Sort the data in all columns in the film table with the film length greater than 60 AND less than 75.

```
SELECT * FROM film
WHERE length > 60 AND length < 75;
```
3. Sort the data in all columns in the film table with rental_rate 0.99 AND replacement_cost 12.99 OR 28.99.

```
SELECT * FROM film
WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
```

4. What is the value in the last_name column of the customer whose value is 'Mary' in the first_name column in the Customer table?

```
SELECT last_name FROM customer
WHERE first_name = 'Mary'
```

5. Rank the data in the film table that DOES NOT have a length greater than 50, but also a rental_rate of 2.99 or 4.99.

```
SELECT *FROM film
WHERE NOT (length > 50 OR rental_rate = 2.99 OR rental_rate = 4.99);
```
---

- Assignment 2

1. Provided that the replacement cost value in all columns in the film table is greater than 12.99, equal and less than 16.99.

```
SELECT * FROM film 
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```

2. The data in the first_name and last_name columns in the Actor table have the values of first_name 'Penelope' or 'Nick' or 'Ed'

```
SELECT first_name, last_name FROM actor 
WHERE first_name IN('Penelope', 'Ed', 'Nick');
```
3. Sort the data in all columns in the film table with rental_rate 0.99, 2.99, 4.99 AND replacement_cost 12.99, 15.99, 28.99.

```
SELECT * FROM film
WHERE (rental_rate IN(0.99,2.99,4.99)) AND (replacement_cost IN(12.99,15.99,28.99))
```
---

- Assignment 3

1. List the country names in the country column of the country table, starting with the 'A' character and ending with the 'a' character.

```
SELECT country FROM country
WHERE country LIKE 'A%a';
```

2. List the country names in the country column of the country table, consisting of at least 6 characters and ending with the 'n' character.

```
SELECT country FROM country
WHERE country LIKE '%_____n';
```
3. Containing at least 4 'T' characters from the film names in the title column of the film table, regardless of upper or lower case letters.

```
SELECT  title FROM film
WHERE title ILIKE '%T%T%T%T%';
```
4. From the data in all the columns in the movie table, sort the data that starts with the title 'C' character, has a length greater than 90 and a rental_rate of 2.99.

```
SELECT * FROM film
WHERE title ILIKE 'C%' AND length > 90 AND rental_rate = 2.99;
```
---
- Assignment 4

1. List the different values in the replacement_cost column in the film table.

```
SELECT DISTINCT(replacement_cost) FROM film
ORDER BY replacement_cost ASC;
```

2. How many different data are there in the replacement_cost column in the film table?

```
SELECT COUNT(DISTINCT(replacement_cost)) FROM film;
```
3. How many of the film titles in the movie table start with the character T and at the same time the rating is equal to 'G'?

```
SELECT COUNT(title) FROM film
WHERE title ILIKE 'T%' AND rating = 'G';
```
4. How many of the country names (country) in the country table consist of 5 characters?

```
SELECT COUNT(*) FROM country 
WHERE country ILIKE '_____';
```
5. How many of the city names in the City table end with the character 'R' or r?

```
SELECT COUNT(*) FROM city
WHERE city ILIKE '%r';
```
---
- Assignment 5

1. List the 5 longest (length) films in the film table and the film title (title) ends with the 'n' character.

```
SELECT title, length FROM film
WHERE title LIKE '%n'
ORDER BY length DESC, title ASC
LIMIT 5;
```

2. List the second 5 shortest (length) films in the film table and the film title (title) ends with the 'n' character.

```
SELECT title, length FROM film
WHERE title LIKE '%n'
ORDER BY length ASC, title ASC
OFFSET 5
LIMIT 5;
```
3. Sort the first 4 data, provided that store_id is 1 in descending order according to the last_name column in the Customer table.

```
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```
---

- Assignment 6

1. What is the average of the values in the rental_rate column in the film table?

```
SELECT ROUND(AVG(length),4) AS Average FROM film;
```

2. How many of the films in the film table start with the 'C' character?

```
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%'
```
3. Among the films in the movie table, how many minutes is the longest (length) film with a rental_rate equal to 0.99?

```
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99
```
4. How many different replacement_cost values are there for the films in the film table that are longer than 150 minutes?

```
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150
```
---

- Assignment 7

1. Group the movies in the movie table according to their rating values.

```
SELECT rating, COUNT(*) FROM film
GROUP BY rating;
```

2. When we group the films in the film table according to the replacement_cost column, list the replacement_cost value with more than 50 films.

```
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50
ORDER BY replacement_cost;
```
3. What are the customer numbers corresponding to the store_id values in the Customer table?

```
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id
ORDER BY store_id;
```
4. After grouping the city data in the City table according to the country_id column, share the country_id information and the number of cities that contain the highest number of cities.

```
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
```
---

- Assignment 8

1. Let's create a table in your test database with employee name column information id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100).

```
CREATE TABLE employee(
	id INTEGER,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(100)
);
```

2. Let's add 50 pieces of data to the employee table we created using the 'Mockaroo' service. (three examples)
```
insert into employee (id, name, email, birthday) values (1, 'Elizabeth Jessen', 'ejessen1@xinhuanet.com', '1984-07-27');
insert into employee (id, name, email, birthday) values (2, 'Mahala Bleier', 'mbleier0@artisteer.com', '1967-12-16');
insert into employee (id, name, email, birthday) values (3, 'Lorenzo Marchington', 'lmarchington9@utexas.edu', '1975-05-01');
```
3. Let's do 5 UPDATE operations that will update the other columns according to each of the columns.

```
UPDATE employee                                                       
SET name = 'Emmett Robert',
	email = 'emmett@robert.com',
	birthday = '1989-04-05'
Where id = 25
RETURNING *;

UPDATE employee
SET name = 'Brian Lorry',
	id = '11',
	email = 'brian@lorry.com'
WHERE birthday = '1992-11-20'
RETURNING *;

UPDATE employee
SET id = 88,
	birthday = '1996-10-04',
	email = 'robert@berkeley.com'
WHERE name = 'Robert Berkeley'
RETURNING *;

UPDATE employee
SET name = 'Lucius Malfoy',
	birthday = '1994-05-11',
	email = 'lucius@malfoy.edu'
WHERE id = 67
RETURNING *;

UPDATE employee
SET id = 103,
	name = 'Zachary Allson',
	birthday = '1988-08-11'
WHERE email = 'zachary@allson.edu'
RETURNING *;
```
4. Let's do 5 DELETE operations that will delete the relevant row according to each of the columns.

```
DELETE FROM employee
WHERE id = 88
RETURNING *;

DELETE FROM employee
WHERE name = 'Ferdinand Cornwall'
RETURNING *;

DELETE FROM employee
WHERE birthday = '1982-07-11'
RETURNING *;

DELETE FROM employee
WHERE email = 'abriggg@huffingtonpost.com'
RETURNING *;

DELETE FROM employee
WHERE id = 247
RETURNING *;
```
---

- Assignment 9

1. Write the INNER JOIN query where we can see the city and country names in the city table and the country table together.

```
SELECT t1.city, t2.country
FROM city AS t1
INNER JOIN country AS t2
ON t1.country_id = t2.country_id;
```

2. Write the INNER JOIN query where we can see the customer table and the payment_id in the payment table and the first_name and last_name names in the customer table together.

```
SELECT t1.payment_id, t2.first_name, t2.last_name  
FROM payment AS t1
INNER JOIN customer AS t2
ON t1.customer_id = t2.customer_id;
```
3. Write the INNER JOIN query where we can see the names of the customer table and the rental_id in the rental table and the first_name and last_name in the customer table together.
```
SELECT t1.first_name, t1.last_name, t2.rental_id
FROM customer AS t1
INNER JOIN rental AS t2
ON t1.customer_id = t2.customer_id;
```
---

- Assignment 10

1. Write the LEFT JOIN query where we can see the city and country names in the city table and the country table together.

```
SELECT t1.country, t2.city
FROM country AS t1
LEFT JOIN city AS t2
ON t1.country_id = t2.country_id
```

2. Write the RIGHT JOIN query where we can see the customer table and the payment_id in the payment table and the first_name and last_name names in the customer table together.

```
SELECT t1.first_name , t1.last_name, t2.payment_id
FROM customer AS t1
RIGHT JOIN payment AS t2
ON t1.customer_id = t2.customer_id;
```
3. Write the FULL JOIN query where we can see the names of the rental_id in the customer table and the rental table, and the names of first_name and last_name in the customer table together.
```
SELECT t1.first_name , t1.last_name, t2.rental_id
FROM customer AS t1
FULL JOIN rental AS t2
ON t1.customer_id = t2.customer_id;
```
---


- Assignment 11

1. Let's sort all the data for the first_name columns in the actor and customer tables.

```
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);
```

2. Let's sort the intersecting data for the first_name columns in the actor and customer tables.

```
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);
```
3. For the first_name columns in the actor and customer tables, let's sort the data in the first table but not in the second table.
```
(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM customer);
```
4. Let's also do the first 3 queries for repeating data.
```
--UNON
(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);

--INTERSECT
(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM customer);

--EXCEPT
(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);
```
---

- Assignment 12

1. In the film table, the film length is shown in the length column. How many films are longer than the average film length?

```
SELECT COUNT(*) FROM film
WHERE length > (SELECT AVG(length) FROM film)
```

2. How many films have the highest rental_rate in the film table?

```
SELECT COUNT(*) FROM film
WHERE rental_rate = (SELECT MAX(rental_rate) FROM film)
```
3. In the movie table, list the movies with the lowest rental_rate and the lowest replacement_cost values.
```
SELECT title FROM film
WHERE rental_rate = (SELECT MIN(rental_rate) FROM film) AND replacement_cost = (SELECT MIN(replacement_cost) FROM film)
```
4. Rank the customers who make the most purchases in the payment table.
```
- 1
SELECT first_name, last_name FROM customer
WHERE customer.customer_id = ANY
(SELECT customer_id FROM payment
GROUP BY customer_id
ORDER BY COUNT(*) DESC
LIMIT 5);

- 2
SELECT DISTINCT(customer.customer_id), first_name, last_name FROM customer
INNER JOIN payment
ON customer.customer_id = payment.customer_id
WHERE customer.customer_id IN (SELECT customer_id FROM payment
GROUP BY customer_id
ORDER BY COUNT(*) DESC
LIMIT 5);

```
---




