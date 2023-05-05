---
title: "Spring  In Java"
datePublished: Fri May 05 2023 23:31:01 GMT+0000 (Coordinated Universal Time)
cuid: clhb6wcut000209mfcvlr7k2i
slug: spring-in-java
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683324155360/b4367afb-8bd3-4a45-a027-def0ea12caf9.webp
tags: java, web-development, hashnode, springboot, wemakedevs

---

To understand Spring, One must know about Language and technologies in Java. In Java, if u have to learn web development, You have to learn it in three stages.

The three stages are as follows:

1. Core Java (J2SE-Java 2 Standard Edition ) is a programming language.
    
2. Advanced Java(J2EE-Java 2 Enterprise Edition ) is a set of different technologies required for web application development which is built on top of core Java.
    
    Example of Java Technologies are JDBC,SERVLET,JSP.
    
3. Framework: It is not a new technology but an abstraction built on top of technologies of Advanced Java. <mark>In the modern development field, the use of technology is very rare. Everyone is tilted towards Framework</mark>. Examples of frameworks In java are Hibernate, Spring etc.
    

`Now the question arises? What was the need for technology and framework when we have Java Language? Can't we make web applications through Only Core Java?`

The simple answer is No. You can not make web applications with only Core Java. For making web applications one must use at least Java technologies if not a framework.

There are three types of applications in development:

1. `Standalone Application`
    
    With the help of Core Java, u can only build console-based standalone applications (without GUI ) which can be run on one server at a time.
    
2. `Web Application`
    
    The applications which are made with the help of Java technologies such as JDBC, JSP, SERVLETS, JSTL and use GUI and can work at multiple servers at a time are web applications. It can only be used by a handful of servers at a time.
    
3. `Enterprise-Level Applications`
    
    Those applications which are used by a thousand or million users at the same time are called enterprise-level applications. And we use frameworks to build these types of very large applications.
    

### <mark>Difference between Java Technologies and Framework.</mark>

The major difference is when we make web application projects using Technologies, we have to write the same code, again and again, several times with only a very small change. These repetitive codes are called Boiler Plate Code. And it is a very tedious task, so these boilerplate codes are handled by the framework. So that we only have to worry about our business logic and not about this extra set of problems.

And another big problem was, We have to write very big-big code for very small features. and we have to change our source code again and again manually which is not the best practice in the industry as performance fluctuates. So to increase performance and reduce boilerplate code, Framework comes in.

Frameworks like Spring and Hibernate just reduce the task of writing boilerplate code, increase performance and automate many code-writing processes which were previously done manually. We just have to provide some configuration files to our project and some mapping with our bean class.

## <mark>Basic Introduction of Spring</mark>

Spring is a framework in Java that is widely used for building web applications. It is open source(open source projects are those projects which can be developed by an entire community and the source code is available for all. Everyone can contribute to any open-source project and if that contribution is accepted by the developer's community, then that feature is merged into the code base ) framework developed by Rod Johnson.

Currently, There are 35 modules in spring. Each module provides a different set of work. The most famous module of Spring Framework is Spring-Boot. But to learn Spring Boot, One must learn Spring -Core. Spring Core is the fundamental of Spring Framework. If u have to learn any module of the Spring framework, Spring core is the basis for all modules. Every part of the web application development process can be handled by different modules of Spring.

`Note: Spring Framework is mainly used for building web applications in Java at the enterprise level.`

We are going to have a brief look at the most often-used modules of the Spring framework :

<mark>Spring Boot:</mark> This module helps to make Web applications and microservices building processes faster and easy as everything is automated in Spring Boot. (Note: Everything is not automated in the Spring basic module, so we use this module ). That's why it is so much famous in the market.

<mark>Spring Data JPA:</mark> It is an advanced version built on top of Hibernate and JDBC to deal with persistence logic in applications more efficiently. It is the hot cake in the market right now to deal with persistence logic(database side). Spring JDBC and Spring Hibernate also do the same but Spring Data Jpa does the best work among the three.

<mark>Spring Core: </mark> This module is the foundation of the Spring framework. To learn any other module, one first learns SPring core, and how dependency injection is performed with the help of Different Spring Ioc Containers such as BeanFactory and Application Context.

<mark>Spring JDBC:</mark> This module is built on top of Jdbc.It internally uses Jdbc to talk with databases and perform SQL queries.

<mark>Spring Mail: </mark> This module is used for sending and receiving emails.

<mark>Spring Security: </mark> This module provides various security features for our application like authentication, and authorization to create a robust application free from various cyber-attacks.

<mark>Spring MVC: </mark> This module is also used for building web applications. The important part of this module is, it follows a very widely used design pattern used for building complex and large web applications i.e. MVC(Model-View-Controller).

Thanks for reading this article.I hope this article gives an overview of the framework and why it is so widely used everywhere around the globe. There are many more modules in spring. I will discuss in detail these modules one by one in upcoming blogs.

Let's connect:

Linkedin:[https://www.linkedin.com/in/gaurav4044/](https://www.linkedin.com/in/gaurav4044/)

GitHub: [https://github.com/Gaurav560](https://github.com/Gaurav560)

Twitter: [https://twitter.com/Sharma1809157](https://twitter.com/Sharma1809157)