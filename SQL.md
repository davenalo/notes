Language that comunicates with datebases

Structure Query Language

Tabular form: storage is in tables, it is columns and rows. Thses values can be associated with others, with the id uses, in other tables (relational).

Is an declarative programming language.

>select * from employees;
>semicolon works for use two or more SQL functions in the same file, is not needed everytime, but better do if we do it this way.
>As a consens, SQL language will be writed in caps, and the name of tables and other things related to the data, in lowercase
>SELECT * FROM employees;

- Create

```SQL

CREATE DATABASE nameofthedatabase;

DROP DATABASE dbtodelete;

--


--


CREATE DATABASE test;
USE test; --we say to sql that we want to work with that db (create tables, for example)

CREATE TABLE tabletest (
	testcolumn1 INT
);


ALTER TABLE tabletest -- works for alterate some table, same way as USE with atabase

ADD another_column VARCHAR (60);

-----



```

```SQL

CREATE DATABASE bands;
USE bands;

CREATE TABLE bands (
	id INT NOT NULL AUTO_INCREMENT,
	name VARCHAR (60) NOT NULL,
	PRIMARY KEY (id)
	
);

-- you can say too:

CREATE TABLE employee (
	id BIGSERIAL NOT NULL PRIMARY KEY,
	name VARCHAR (50) NOT NULL,
	date_of_birth DATE NOT NULL
);

--declare PRIMARE KEY at the same creation column text


```


### Set relations between one table and another:

```SQL

CREATE DATABASE discografica;
USE discografica;
CREATE TABLE bands (
	id INT NOT NULL AUTO_INCREMENT,
	name VARCHAR (255) NOT NULL,
	PRIMARY KEY (id) -- here
);

CREATE TABLE albums (
	id NOT NULL AUTO_INCREMENT,
	name VARCHAR (255) NOT NULL,
	release_year INT,
	band_id INT NOT NULL
	PRIMARY KEY (id)
	FOREIGN KEY (band_id) REFERENCES discografica(id) --AND HERE
);

```

### Insert info

```SQL

INSERT INTO discografica (name)
VALUES ('Extremoduro'), ("Extrechinato");

-- in this case we only have une column, because the "id" one is autoincrementing

SELECT * FROM discografica;

SELECT * FROM discografica LIMIT 1; -- ONLY the first one

SELECT id AS "IDENTIFICADOR" --AS works as an alias for the column title

SELECT * FROM discografica ORDER BY name DESC --ASC is the default




INSERT INTO albums (name, release_year, band_id);
VALUES ("Poesía Básica", NULL, 2);

SELECT DISTINCT name FROM albums --DISTINCT is for not to have duplicates



```

### edit

```sql

UPDATE album

SET release_year = 2001 WHERE id = 1;



---

SELECT * FROM discografica JOIN albums ON discografica.id = album.band_id -- la fórmula .id hace referencia a la columna
```

### conditions
```sql

SELECT * FROM albums WHERE name LIKE "%er%"; --% means any amount of characters, iLIKE case sensitive, workds with <, > =, OR, NOT, IS NULL...

SELECTN * FROM albums WHERE release_year BETWEEN 2000 AND 2002;



```

### delete

```sql


DELETE FROM albums --this delete all

DELETE FROM albums WHERE id = 1


```

```sql



SELECT * FROM discografica JOIN albums ON discografica.id = album.band_id -- la fórmula .id hace referencia a la columna

INNER JOIN --ONLY RETURN VALEUS THAT HAVE A MATCH
LEFT JOIN --join even if there's nothing to join (por ejemplo, un valor de una tabla que no tiene asociado otro valor en la otra)
RIGHT JOIN --confuso


```


### functions

```sql

SELECT Avg(release_year) FROM database; --hace la operación de año medio de lanzamiento de los discos, por ejemplo;

otras funciones: SUM() COUNT()...

SELECT band_id, COUNT(band_id) FROM discografica; -- nos devolverá cuantos albums tiene cada banda.

SELECT band_id, COUNT(band_id) FROM discografica GROUP BY band_id;


--
SELECT d.name, COUNT(a.id) AS num_albums
FROM discografica AS d
LEFT JOIN albums AS a ON d.id = a.band_id
WHERE d.name = "Extrechinato"
GROUP BY d.id
HAVING num_albums = 1;

--having works as where but when the count is already done.




```






