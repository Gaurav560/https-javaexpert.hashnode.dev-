---
title: "Life Cycle Of a Query Execution"
seoTitle: "life Cycle Of A Query in SQL"
seoDescription: "Life Cycle Of A Query In SQL."
datePublished: Sun Feb 19 2023 18:55:11 GMT+0000 (Coordinated Universal Time)
cuid: clebr0quv000h08l4h7u487j0
slug: life-cycle-of-a-query-execution
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1676832787280/1f7671e3-8417-4b43-9e6a-8ed5aa757ea6.png
tags: java, mysql, sql, jdbc, advancejava

---

# Intro

Just like a java code compiles and executes a java program, the same thing happens with a SQL query on the database side. A query also compiles and executes and for compiling and executing it goes under several processes. As we know, JVM compiles and executes the java program, in the same way, The DataBase engine acts as a JVM for a query.DB engine executes, compiles, and sends the query back to the application. We are going to have a detailed look into the life cycle of a query.

## why do you need to know about the life cycle of a query?

On the database side, query compilation and execution is not a lightweight task. It is a very heavy-weight task and during the query compilation, the query goes through many processes, and after then query execution takes place. Heavy-weight means it takes time and resources to execute a single query. Now let's suppose a million queries are coming from an application, so for every query, our database engine will compile, execute and send the query to our application. This will lead to performance issues .so we focus on reducing the compilation and execution time to as minimum as possible to increase the faster performance of our applications.

## Life-cycle

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676830453980/2b911363-9971-4932-a95c-d29d924cd5ac.jpeg align="center")

Now let's understand the diagram :

1. 1st we send the query through our application to the database engine.
    
2. Then, the DB engine sends the query for compilation.
    
3. in compilation query goes under three stages:
    
    1. Tokenization
        
    2. Parsing
        
    3. Query Optimization
        
4. 1. tokenization: a stream of tokens is generated from the SQL query.
        
    2. parsing: a parse tree is generated from those tokens
        
    3. query optimization: optimized query tree is generated when the parse tree is passed through the query optimization process.
        
5. Then the optimized query tree goes to execution and the result is generated in the form of a resultSet object(in case of the search query)or no of rows affected(in case of insertion, deletion, or updation).

## Learning through an example :
Suppose there is an application named BookMySeat where u can book movie tickets, and a movie named JohnWick 4 is released. Naturally, there will be thousands of users trying to book tickets for that movie through the application. Every user is sending a query, and in the backend, If the Database Engine of that application starts to compile every query, then automatically the performance of that application will go down as compilation is a heavy-weight process. Thus we write our source code in such a manner that we have to compile the query only once and with only some change in parameters of the query such as city name, movie name, date, etc we can execute an unlimited query. Thus saving millions of milliseconds in the compilation of queries. This will affect the business quite heavily. Thus, it is very important to understand the life cycle of a query execution to understand where we can save time and provide superfast service to our clients.

`Example:
For a single query(let's suppose): 0.5ms(tokenization time)+0.5ms(parsing time)+0.5ms(query optimization time)+1ms(execution time)+1ms(sending back the query result)=3.5 ms total time for one query life cycle.`

`For 100000 queries =3.5*100000ms=350000ms.
Now, if we understood the life cycle clearly, we can certainly save time in many areas such as compilation, batch queries, connection pooling, etc.
Here if we compile our query only once, we can save almost (0.5+0.5+0.5)*100000=150000ms of time.
This will lead to the fast performance of our application. Therefore,it is good to have an understanding of query life cycle .`

If u are interested in reading my article,u can subscribe to my newsletter. If you think I am doing good for the community, then you can also sponsor me . The sponsor link is present at the bottom of this article . Thanks.

