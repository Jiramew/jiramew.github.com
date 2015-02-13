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
   * `DROP TABLE my_contacts`
   * 
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





