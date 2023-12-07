---
title: "ProblemDetail Class"
seoTitle: "spring problemdetail class"
seoDescription: "Unlock seamless error handling in Spring with the ProblemDetail Class. Elevate your RESTful API's performance and user experience effortlessly."
datePublished: Thu Dec 07 2023 23:07:17 GMT+0000 (Coordinated Universal Time)
cuid: clpvt5unp000208l1h36q5svp
slug: problemdetail-class
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701973210053/de24150a-4073-448f-80ab-887342dab6ca.png
tags: spring, java, javascript, technology, web-development, hashnode, springboot, spring-framework, spring-security, technical-writing-1, spring-data-jpa

---

## Spring Boot 3 updates over Spring Boot2

### <mark>Introduction</mark>

As we know SpringBoot 3 internally uses Spring 6. In Spring 6, the Spring Committee brought in something called RFC7807, also known as "Problem Details for HTTP APIs.".

This is useful in cases where HTTP status codes are not enough to describe the problem with an HTTP API.

It's like a rulebook that says errors or issues in HTTP APIs should be explained in a specific and more detailed way. ProblemDetail improves error troubleshooting by responding with an error message in a special style using methods like errorType(), errorTitle(), errorDetail(), and many more in JSON format.

### <mark>why it was required to introduce a new class?</mark>

When you're working on a RESTful API, it's super important to handle errors gracefully and give clients clear information when things go wrong.

Spring Boot 3 has this cool thing called the ProblemDetail specification, which helps you create standardized and organized error responses. In this blog post, we're going to deep dive into how to use this feature in our Spring Boot applications.

The advantage is that API designers don't have to devise their own methods for describing problem details.

Creating custom error messages for a customer REST application in a specific JSON format is important. The HTTP status often does not provide enough information for the client. Therefore, more detailed information about the issue must be sent back to the client side.

To accomplish this, previously we had to create our own Error class. It's a common requirement for REST applications to provide detailed error responses. This is where the Problem Details Class for HTTP API specification (code [RFC 7807](https://datatracker.ietf.org/doc/html/rfc7807)) becomes useful.

Its purpose is to define common error formats in HTTP responses, eliminating the need for each application to define its own.

We'll explore how it can make handling exceptions easier and allow you to create custom error responses that make sense for your application.

<mark>Problem Statement:</mark> We will write a rest API method to register the vote of a person. If the person is above 18 years old, that person can vote and we will register his/her vote. If his/her age is less than or equal to 18 we will generate an exception and we will try to handle that generated exception with proper error details sent back to the client side with the help of the ProblemDetail Class object.

<mark>Note:</mark> We will be focusing on generating a custom exception by passing the age value smaller than or equal to 18 and then handling the exception object and providing error details to the client with the help of the ProblemDetail Class.So, that we can understand how ProblemDetail Class works.

### 1st Step:

Creating a rest controller class and defining a controller method named vote to register the vote. If the voter age is less than or equal to 18, this rest controller method i.e. vote, is going to throw an object of a custom-defined exception class called AgeNotValidException, which we will be creating further in this article.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701988958474/73ae17f8-518e-46c0-b54b-4e63dd6e37f9.png align="center")

### Step2

Creating a service class and defining the method registerVote to process the logic of registering votes and passing the age of the voter in the method parameter.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701979346598/e13efa48-2793-41b9-a9f9-823576067a84.png align="center")

### Step3

Creating our custom Exception Class i.e. AgeNotValidException. When the age of the voter is below 19, we will throw an object of this custom-generated exception class which will be further handled by another rest exception controller method.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701979854112/ad78312f-3e9c-445b-a72c-3b5433ec6bfc.png align="center")

### Step4

Creating a rest Controller exception class and naming it GlobalExceptionHandler for intercepting custom exceptions.

When a user enters an age less than or equal to 18, our rest controller method i.e. vote is going to throw an object of this AgeNotValidException class.

We have created another rest controller i.e. GlobalExceptionHandler just to handle custom exception objects thrown by the method i.e. vote present in our primary rest controller class i.e. ControllerClassForProblemClassExplaination.

we have defined a controller method i.e. handleAgeNotValidException for handling AgeNotValidException exception objects thrown by the vote method.

In this handleAgeNotValidException method, we will create an object of the ProblemDetail class and we will inject error details into that object.

ProblemDetail class object has certain methods i.e. setDetail(), setType(), setTitle(), and many more inbuilt methods which can be used to pass more information about the error at the client side.

setDetail() -&gt; This method is used to set details of the error, to have a better understanding of the error at the client side whenever it occurs.

The same goes for setTitle() and many more methods.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701985802252/baa883a4-0482-4f9d-a8d5-0a867f6a0763.png align="center")

Explanation of the above code:

we are not making a custom class to handle the error details.

This ProblemDetail class has static methods for creating objects like forStatus() and forStatusDetail() which we will use for handling and setting error details.

In simpler terms, static methods are invoked using the class name. In this context, we're making an object of the ProblemDetail Class by using the static method forStatus(). Then, we're configuring error details by calling various built-in methods on the ProblemDetail Class object, which we've named "problemDetail." These methods include setDetail(), setTitle(), or setType().

### Step5

we have sent a post request with the age value=11 in the query string with the help of @Requestparam annotation. As the age of the voter is less than 19, it returns the detailed error message instead of generating some random error messages that can't be understood by us.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701986067246/c409c4d9-6f77-4706-bb8d-d757f8bf1c27.png align="center")

Below is the detailed error that is being sent to the client in JSON format using the object of ProblemDetail Class. It has information like error type, title, detail, status code, and path for which the error is generated. This error information can be further used for error-solving much more easily. It can save a lot of time as we don't have to debug much, like from where this error is getting generated in our code.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701986117652/6c97c675-0d92-455d-b747-84368a8655f8.png align="center")

### For more reference

please have a look at the official documentation :

[https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/http/ProblemDetail.html](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/http/ProblemDetail.html)

### Let's Connect:

Linkedin: [https://www.linkedin.com/in/gaurav4044/](https://www.linkedin.com/in/gaurav4044/)

Github: [https://github.com/Gaurav560](https://github.com/Gaurav560)