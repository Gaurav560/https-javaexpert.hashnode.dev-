---
title: "SQL in simplest form"
seoTitle: "SQL"
seoDescription: "simple explanation on SQL"
datePublished: Tue Jan 17 2023 21:13:46 GMT+0000 (Coordinated Universal Time)
cuid: cld0qfvej000009jo8lwjha5m
slug: sql-in-simplest-form
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Y9kOsyoWyaU/upload/2e45cf9892c41bf675afaa65d5141fa1.jpeg
tags: sql-server, databases, sql, sqltutorial

---

in very simple words, it is nothing but a language to interact with data present in databases. Databases are spaces where we keep our data virtually. A database can be of several types depending on the pattern in which data is stored in them and how the data will be fetched when needed.

if the data is stored in the form of tables like in the '80s when we used to store data in a ledger, then that type of database is called a relational database. there are tables for the different sections of data, and here comes SQL. With the help of SQL, we are able to communicate with the data present inside the tables. An example of one such popular database is MySQL.

if the data is not in the form of tables then it can be categorized in many forms such as NoSQL, Centralized, Distributed, etc. Some examples are MongoDB, Cassandra, etc.

NOTE:-SQL language only works for relational databases. For using SQL language on the MYSQL database u have to download the MYSQL workbench and server .server is the database and the workbench is the place where u will write queries for data fetching, updation, deletion, or insertion.

NOTE: with any data, u can do only four operations that are Create, Read, Update, and Delete. In short, these are called CRUD operations .and these operations are done on the data present in the database inside the tables.

There are certain commands one should practice to gain adaptive knowledge of SQL. we will write those commands on MySql Workbench. One should note that SQL is case insensitive language. This means that capital or small letters do not affect the meaning of the command or query. But it is always advisable to write the queries or commands in capital letters as it is standard practice in the coding community.Semicolon(;) should be at the very end of every query.

Some of the commands are:-

1. CREATE DATABASE DATABASE-NAME;
    
    this command will create a database with the required name when u execute it.
    
2. USE DATABASE-NAME;
    
    if u have multiple databases, then this query will be very much helpful in selecting the particular database in which u want to perform operations.
    
3. CREATE TABLE TABLE-NAME;
    
    After selecting the database with which u want to work with, this command will help you to create the table in that database.
    
4. DESC TABLE-NAME;
    
    this command will describe the table.
    
5. INSERT INTO TABLE-NAME(NAME OF COLUMNS) VALUES(VALUE OF COLUMNS);
    
    For inserting the data into the table.
    
6. SELECT \* FROM TABLE-NAME;
    
    it will display all the required information in the table.
    
    KEYS: It is noted that two fields or column values in a table can be the same but it does not remove the redundancy of data which will lead to inconsistency in the real world. There must be a column in each table in the database through which each field can be particularly known. A key called primary key is used for particularly identifying a field. the value of the primary key in the whole table cannot be null and cannot be redundant .it must be just like the roll number of students in a classroom which cannot be duplicated and can be used to find students' information through that roll number.
    
    Another key is the foreign key which I will discuss later.
    
    note: i will update this blog as I read forward .thanks.