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

### 