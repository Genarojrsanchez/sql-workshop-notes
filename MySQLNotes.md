*MySQL Bootcamp*

**Lesson Objectives**

1. What is a DB
1. What are the different ways to store data
1. Why do we need SQL
1. Diagram MySQL structure
1. Connect to MySQL
1. Create a DB
1. CRUD
1. LIKE
1. AND/OR
1. ALTER
1. DISTINCT
1. OFFEST/LIMIT
1. ORDER BY
1. GROUP BY

```mysql
SHOW DATABASES;
CREATE DATABASE users;
USE users;
CREATE TABLE employees (NAME VARCHAR(20), age INT);
DESCRIBE employees;

INSERT INTO employees (NAME, age) VALUES ('Matt' , 34);

SELECT * FROM employees;
SELECT age FROM employees;

SELECT * FROM employees WHERE NAME LIKE "%Charlie%" OR age = 80;
SELECT * FROM employees WHERE age > 45;
SELECT * FROM employees WHERE age != 63;

UPDATE employees SET weight = 300 WHERE NAME = 'Bill' LIMIT 1;
UPDATE employees SET dob = NOW() WHERE id = 9;
UPDATE employees SET dob = '2015-06-26 12:04:10' WHERE id = 10;

DELETE FROM employees WHERE NAME = "Bill" AND age = 10;

SELECT * FROM employees ORDER BY age DESC;
SELECT * FROM employees ORDER BY age ASC LIMIT 2;
SELECT * FROM employees ORDER BY age ASC LIMIT 2 OFFSET 1;
SELECT * FROM employees ORDER BY age DESC, NAME ASC;

ALTER TABLE employees ADD COLUMN weight FLOAT;
ALTER TABLE employees DROP COLUMN height;
ALTER TABLE employees ADD COLUMN height FLOAT AFTER NAME;
ALTER TABLE employees MODIFY COLUMN height FLOAT AFTER age;
ALTER TABLE employees ADD COLUMN id INT FIRST;
ALTER TABLE employees ADD COLUMN dob DATETIME;
ALTER TABLE employees CHANGE dob date_of_birth DATETIME;
ALTER TABLE companies ADD COLUMN id INT NOT NULL AUTO_INCREMENT PRIMARY KEY FIRST;

SELECT COUNT(*), age FROM employees GROUP BY age;
SELECT COUNT(*) FROM employees GROUP BY age;
SELECT SUM(age) FROM employees GROUP BY age;
SELECT AVG(age) FROM employees;
SELECT MIN(age) FROM employees;
SELECT MAX(age) FROM employees;
SELECT GROUP_CONCAT(age) FROM employees;

SELECT * from employees FULL JOIN companies;
SELECT * FROM employees JOIN companies ON employees.`employer_id` = companies.`id`;
SELECT * FROM employees RIGHT OUTER JOIN companies ON employees.`employer_id` = companies.id WHERE employees.`employer_id` IS NULL;
SELECT * FROM employees LEFT OUTER JOIN companies ON employees.`employer_id` = companies.id WHERE employees.`employer_id` IS NULL;
SELECT employees.*, companies.`name` FROM employees INNER JOIN companies ON employees.`employer_id` = companies.id;
SELECT e.*, c.name AS company_name FROM employees AS e INNER JOIN companies AS c ON e.employer_id = c.id;
```