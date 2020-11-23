### TechRecap_Week 10

# Relational Databases

### Database

A structure that stores organized information that it can be easily accessed, managed and updated.

### Components of a database

Schema is the tables, columns and relationships that make up a relational database.

### Relevant terms:

**SQL - Structured Query Language:** a language to extract and organize data stored in the database.

**Statement:** Atomic unit of work. Example: CREATE TABLE movies

**Query:** Request for data or information from a database.

**Database query** can be a select (retrieve data) or an action query (additional operations)

## Create a database

```
CREATE DATABASE <name of the database >;
```

```
SHOW DATABASES;
```

```
USE <dbname>;
```

```
CREATE TABLE movies (
    id INT,
    title VARCHAR(100),
    genre VARCHAR(100),
);
```

### Insert Data

```
INSERT INTO movies (id, title, genre)
    VALUES(0, ‘Matrix’, ‘Science fiction’);
```

### Select ALL

```
SELECT \* FROM movies
```

### Select specific data

```
SELECT title, genre FROM movies
WHERE genre = action
```

### Make changes in the structure of a table

```
ALTER TABLE movies
ADD year INT;
```

```
UPDATE movies SET year = 2012 WHERE id = 0;
```

```
DELETE FROM movies WHERE id = 1;
```

To empty the table data:

```
TRUNCATE TABLE <movies>
```

Delete the table:

```
DROP TABLE <movies>
```

The **LIKE** operator searches a specific pattern of one ( \ \_ ) or multiple characters ( % )

### BETWEEN

```
SELECT _ FROM movies WHERE year BETWEEN 2000 AND 2018 ;
```

### AND and OR

```
SELECT _ FROM movies WHERE year BETWEEN 2000 AND 2018 AND genre = “drama”
```

```
SELECT \* FROM movies WHERE genre = “crime” OR genre = “suspense”
```

### Sorting data

```
SELECT * FROM movies ORDER BY title ASC (ascending)
```

```
SELECT * FROM movies ORDER BY title DESC (descending)
```

### LIMIT

```
SELECT _ FROM movies ORDER BY year DESC LIMIT 4;
COUNT
```

### GROUP BY

```
SELECT campus, COUNT (*) as number_of_movies
FROM movies
GROUP BY genre;
```
