---
title: "Stored Procedure In SQL"
seoTitle: "Stored Procedure in SQL"
seoDescription: "Stored Procedure in SQL"
datePublished: Mon Feb 20 2023 00:47:00 GMT+0000 (Coordinated Universal Time)
cuid: clec3l6xy000409jehkuk5xhy
slug: stored-procedure-in-sql
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1676835771727/5a2f8cae-bb29-433d-a598-80de75a2aba6.png
tags: sql-server, java, mysql, sql, jdbc

---

# What is Stored Procedure?

A set of SQL queries is called a stored procedure. Whenever we need one set of SQL statements to use again and again in our database program, then we write those SQL statements together and store them inside a procedure(called Stored Procedure). The stored procedure is saved permanently in the database. It has a special syntax. It is just like a method in any language. We use a method so that we don't have to write the method definition again and again and we can call it just by its name whenever we want and use them accordingly. In the same way, we can also call Stored Procedure just by its name. And just like the method accepts parameters and can return values, a Stored procedure also accepts parameters and can return values according to its body definition.

## Syntax

### Stored Procedure without Parameter

```
DELIMITER $$

CREATE PROCEDURE <ProcedureName>
   
	BEGIN
sql Statements
	END$$

DELIMITER ;
```

`Note: In MySQL, we use a CALL statement to call a stored procedure.`

Learning through an example:

We have created a table named funcinemaranchi in a database name juniorg.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676847183039/e18f8fa0-8367-4163-80f9-e8734c420f90.png align="center")

Now, we have created a stored procedure named selectByTheater in juniorg database and stored two SQL statements.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676846398332/283f9930-c474-40bf-b67d-d9d00082e95c.png align="center")

Now, we are calling the selectByTheater stored Procedure which should return 1st and 3rd Screen Theaters and its show. (Call Statement in MySQL is necessary to show results of stored procedures)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676847306154/baae7dd1-f494-4a65-81cd-b8c718a64054.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676847328686/afb98f7e-f3e5-49b8-8d02-c4b753df2fe5.png align="center")

## Stored Procedure with Parameters()

We use three types of parameters in the Stored procedure

1. IN Parameter
    
2. OUT Parameter
    
3. INOUT Parameter
    
We basically use only in and out parameters on daily basis. So, we are going to see only those two.

Explaining one by one with examples:

we have taken the same database, table, and stored procedure that we have used in the above example. we will use in parameter to search theaters with their number.

### IN PARAMETER SYNTAX(WITH EXAMPLE)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676850664560/dc681ebf-e626-4438-a757-2b592668a38b.png align="center")

In the above picture, we have altered the existing stored procedure and used the parameter screenNo to find the theaters.

Now, calling the stored procedure (selectByTheater) with input passed as a parameter.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676850953807/6bbd9b00-90e0-4674-a075-e08fbb0a376d.png align="center")

You can see all TheaterScreenNo with 1.

### OUT PARAMETER

This parameter is used to store the results, the query has given.

For example, we have created a new Stored Procedure by the name getTotalMoviesByScreenNo.This procedure throws no of movies running on a particular Screen In the Cinema Hall by giving the screen number as in the parameter. We are using the same database as used in the above examples with the same table.

Stored procedure for out parameter:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676852097775/5c8ded41-3db4-49f5-8ac6-a6a6665c60d7.png align="center")

Now, we are calling that store procedure with in parameter as 2 and storing the output in res parameter(u can give any name for the out parameter. don't forget to use @ before the out parameter). I named the out parameter as res and later changed it to noOfMovies.And at last use select query as it will show the count of movies running in the screen2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676852403123/ad2e04e7-6607-4c3b-ba1e-f7851de74d44.png align="center")

`Important: If there is more than one parameter in the stored procedure then, Give the inputs for the parameters in sequence in the call statement  as u have given in the stored procedure, or if u don't want to follow the sequence of the input for a parameter then execute the call statement with parameter and argument as key-value pair .`

`Important: You cannot understand it properly unless writing the code yourself and get your hands dirty. So please, write the code and practice to understand this article properly. This article is mainly practically based, with very little scope of the theory. but I have tried to make you understand all the concepts with examples.`

If you are enjoying the content, please subscribe to my newsletter to get more such articles and kindly sponsor my work (if you can). The subscription and sponsor link is on the bottom page of this article.