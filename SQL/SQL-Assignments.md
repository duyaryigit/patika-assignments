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





