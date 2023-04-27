---
title: "CRUD Operations In SQL"
seoTitle: "Crud operations in simplest way"
seoDescription: "this blog will explain you crud operations in SQL in the simplest way possible."
datePublished: Thu Jan 19 2023 12:55:53 GMT+0000 (Coordinated Universal Time)
cuid: cld33jai9000408mcf7vzgzbi
slug: crud-operations-in-sql
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1674112838702/25526bac-9d65-4423-a127-162599c6703e.png
tags: sql-server, java, mysql, sql, crud

---

*<mark>INTRO</mark>*

In MySql database, data is stored within tables and there are many tables as per requirement. Within a table, with any data, we can do basic four operations. Like we can insert new data into a table, read data from tables, update data in tables, and delete data from a table. These four basic operations are called CRUD operations in SQL. All four operations are covered in an easy-to-understand manner one by one.

Before knowing CRUD operations one must know how to create a database and in that database how to create a table. One must practice the example given below steps on the MySql workbench to get the concepts clearly.

1\. Let us create a database for a school named VIDYAPEETH (<mark>query:</mark> CREATE DATABASE VIDYAPEETH;).Now a database is created for the school.

2\. As in MySql there can be many databases present .so to keep the VIDYAPEETH database in focus for performing crud operations we implement the following(<mark>query: </mark> USE VIDYAPEETH;).Now VIDYAPEETH database is selected.

1. Now we have to create a table for keeping students' general information. (<mark>query:</mark>
    
    Now we will see all four basic operations :
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674129477613/62260af6-ccc6-4f63-8aa7-6d0c4a98e859.png align="center")
    
2. We have created a database name Vidyapeeth and created a table named student with some columns named id, first name, last name, age, city, and number(phone) inside the Vidyapeeth database. We will use this database and table in the entire blog to understand crud operations.
    
    <mark>NOTE: SQL is a case-insensitive language.</mark>
    
    Here come the crud operations :
    
    ### *<mark>CREATE OPERATION(used for inserting data )</mark>*
    
    The very first thing is to create a database and afterward create a table. After creating a table, now we can insert data into tables. Data in the table is stored in form of columns and rows in MySql.The query for the insertion of data is as:
    
    *<mark>Query:</mark>*
    
    INSERT INTO TABLE\_NAME(COLUMN\_NAMES) VALUES(VALUES\_OF\_COLUMNS);
    

Example: for Inserting data in table students we can write as follows:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674129931007/6610ee74-6898-4e87-865b-9b1dfc580f54.png align="center")

Now, data is inserted with four rows. Now here comes the Read Operation.

### *<mark>READ OPERATION(for reading data from the table)</mark>*

If we have to read the whole data we have inserted in the table, then we use the following (<mark>query:</mark> SELECT \* FROM STUDENTS;)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674130294299/d0b82d84-63e9-4925-859d-9d5340e0cdff.png align="center")

important: In crud operations WHERE clause is very important .it helps to make choices such as from which condition u have to read, update, delete, etc.

eg: like I wish to read all the data of students above 21, then we can write (<mark>query: </mark> SELECT \* FROM STUDENTS WHERE AGE&gt;21;)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674130702030/1781d62e-dcbc-49e4-af2e-b8d7946debf0.png align="center")

### *<mark>UPDATE OPERATION (for updation of data)</mark>*

Whenever it is required to update the data in the table, we use the update operation. The query is very simple (query: UPDATE TABLE\_NAME SET(WHATEVER U WANT TO UPDATE) WHERE ID=?;)

NOTE: in the where clause always try to use the column which has the primary key .it is easy to use in this way as the primary key is unique in a table and easy to find.

Example: Suppose in the 2nd row we want to update the city name from "Ranchi" to "Bengaluru".The query is (<mark>query:</mark> UPDATE STUDENTS SET CITY="BENGALURU" WHERE ID=2;)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674131589553/29af8370-174a-4b7c-9ab7-0f3c42bb7c92.png align="center")

### *<mark>DELETE OPERATION(for deletion of data )</mark>*

Delete command or query is used to delete all the rows or a specific row/record from the table.

1. To delete all the rows from the table use :
    

<mark>Query: </mark> DELETE FROM STUDENTS;(this query will delete all the rows from the table.)

1. to delete a particular record from the table we use the WHERE clause.
    
    <mark>Query: </mark> delete from students where id=2;(we are deleting 2nd row in our example)
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1674132547860/60e062ce-ad9d-4d82-be74-5d6ef22d61c5.png align="center")

<mark>NOTE:</mark> Once you get a command of these queries written in this blog, it will be a cakewalk to understand the rest of all the modifications done on queries to get the desired data.