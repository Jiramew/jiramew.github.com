---
layout: post
title: "Something about SQL (1)"
description: ""
category: 
tags: [tutorial]
---

This post will show Some __basic knowledge__ about SQL.

1. * A __Database__ is a container that holds tables and SQL structures related to those tables.
   * A __column__ is a piece of data stored by your table. A __row__ is a single set of columns that describe attributes of a single thing. Columns and rows together make up a table.
   * __Field__ and column means the same thing, Also row and __record__ are often used interchangably.


2. * Use `mysql -u root -p` in cmd to launch into the MySQL environment. Or open the cmd with Administrator privileges.
   * `CREATE DATABASE gregs_list;` will create a database called "gregs_list".
   * Then `USE gregs_list;` to actually use the database you just created.
   * Datatypes: CHAR, INT, DEC, VARCHAR, BLOB, DATE, DATETIME, TIMESTAMP.
   * `DESC my_contacts` to show the structural information of the table you just created.
   * `DROP TABLE my_contacts` will deletes all the table and any data in it.
   * Create the table again

```
CREATE TABLE my_contacts(
    last_name VARCHAR(30),
    first_name VARCHAR(20),
    email VARCHAR(50),
    gender CHAR(1),
    birthday DATE,
    profession VARCHAR(50),
    location VARCHAR(50),
    status VARCHAR(20),
    interests VARCHAR(100),
    seeking VARCHAR(100)
);
```
   * Add some data to the table
 
```
INSERT INTO my_contacts(
    last_name,first_name,email,gender,birthday,profession,location,status,interests,seeking)
    VALUES 
    ('Anderson','Jillian','jill_anderson@breakenckpizza.com','F','1980-09-05','Technical Writer','Palo Alto, CA','Single','Kayaking, Reptiles','Relationship,Friends'
);
```
   * `SELECT * FROM my_contacts` to peek at the table.
   * More detail about the data in `CREATE TABLE`
 
|doughnut_cost |DEC(3,2) |NOT NULL          |DEFAULT 1.00         |
|--------------|:-------:|:----------------:|---------------------|
|Column Name   |Data Type|Cannot leave empty|Default value is 1.00|





