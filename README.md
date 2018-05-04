# SQL-Markdown-Notes

## Section 1: Introduction and 5 Minutes of SQL

**Step 1.**
```sql
SELECT * FROM customers;
```

**Step 2.**  
```sql
SELECT * FROM orders;
```

**Step 3.**  

```sql
SELECT *
FROM products
ORDER BY Price DESC;
```


**Step 4.**
```sql
SELECT 
customerName,
COUNT(*) AS 'number of orders'
FROM customers
INNER JOIN orders
ON orders.customerID = customers.customerID
GROUP BY customers.customerID;
```

## Section 3: Creating databases and tables

**Create databases:**
1. start the CLI:
`mysql-ctl cli;`
2. List databases:
`show databases;`
3. Create databases:
`CREATE DATABASES database_name;`

**Drop databases:**
Drop a databases:
```sql
DROP DATABASE database_name;
```

**Use database:**
```sql
USE database_name;
```
See the current selected database:
```sql
SELECT database();
```

**Common Data types:**
1. Variable string:
VARCHAR(string_length)
2. Integer:
INT

**Create my own table:**
```sql
CREAT TABLE table_name
(
col_name data_type,
col_name data_type
);
```

Example of cats table:
```sql
CREATE TABLE cats
(
name VARCHAR(100),
age INT
);
```

**Checking tables:**

```sql
SHOW TABLES;
SHOW COLUMNS FROM table_name;
DESC table_name;
```

**Dropping tables:**
```sql
DROP TABLE table_name;
```

## Section 4: Inserting Data
**Insert data**
Generic:
```sql
INSERT INTO table_name(column_name) VALUES (data);
```
Example:
```sql
INSERT INTO cat(name, age)
VALUE('Uni', 1)
```

**Insert Multiple Data**
```sql
INSERT INTO table_name 
            (column_name, column_name) 
VALUES      (value, value), 
            (value, value), 
            (value, value);
```

**View Inserted Data**
```sql
SELECT * FROM cats; 
```

**View Warning**
```sql
SHOW WARNINGS;
```

**Create table with NOT NULL constraints**
```sql
CREATE TABLE cats2
(
  name VARCHAR(100) NOT NULL,
  age INT NOT NULL
);
```

**Create table with NOT NULL constraints and default value**
```sql
CREATE TABLE cats4
(
  name VARCHAR(20) NOT NULL DEFAULT 'unnamed',
  age INT NOT NULL DEFAULT 99
);
```

**Primary Key: a unique identifier**
```sql
CREATE TABLE unique_cats
(
  cat_id INT NOT NULL,
  name VARCHAR(100),
  age INT,
  PRIMARY KEY (cat_id)
);
```

**Adding AUTO_INCREMENT:**
```sql
CREATE TABLE unique_cats2 (
  cat_id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(100),
  age INT,
  PRIMARY KEY (cat_id)
);
```

**More Complex Example**
```sql
CREATE TABLE employees (
  id INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
  first_name VARCHAR(255) NOT NULL,
  last_name VARCHAR(255) NOT NULL,
  middle_name VARCHAR(255),
  age INT NOT NULL,
  current_status VARCHAR(255) NOT NULL DEFAULT 'employed'
);
```
testing:
```sql
INSERT INTO employees(first_name, last_name, age) VALUES
('Dora', 'Smith', 58);
```

## Section 5: CRUD Commands
**CREATE cats table**
```sql
CREATE TABLE cats (
  cat_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  breed VARCHAR(100),
  age INT
);
```

**INSERT cats' data**
```sql
INSERT INTO cats(name, breed, age) 
VALUES ('Ringo', 'Tabby', 4),
       ('Cindy', 'Maine Coon', 10),
       ('Dumbledore', 'Maine Coon', 11),
       ('Egg', 'Persian', 4),
       ('Misty', 'Tabby', 13),
       ('George Michael', 'Ragdoll', 9),
       ('Jackson', 'Sphynx', 7);
```