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









