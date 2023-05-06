---
title: "Pojo  Vs  Java Bean In Java"
datePublished: Sat May 06 2023 12:51:48 GMT+0000 (Coordinated Universal Time)
cuid: clhbzi6in000409mw8jfudps3
slug: pojo-vs-java-bean-in-java
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683377492380/e4ad4981-ffcc-4673-bd53-7c6168a70e85.png
tags: java, web-development, hashnode, hashnodebootcamp, wemakedevs

---

So, you have heard these two words if you are in the Java development field, but many of them still don't clearly understand these two concepts or they have a misconception that both are the same.

In this article, I will give you a clear and concise understanding of these two terms in Java.

<mark>First of all, both are classes in Java i.e. POJO Class and Java Bean Class. </mark> Now let me tell you the basic difference between these two in detail.

## POJO Class (plain old Java object)

For any class to be called a POJO class, there are three factors to be considered:

1. <mark>This class should not implement any interface.</mark>
    
2. <mark>This class should not extend to any class.</mark>
    
3. <mark>This class does not have any annotations.</mark>
    

And the object of this class will be called Plain Old Java Object.

`Let me show an example, of what a POJO Class looks like :`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683375009564/c073ca01-b9f0-4f22-ae63-5cb45b806aef.png align="center")

Explaination: The CricketPlayer class is a POJO class because :

it does not extend any class, it implements any interface nor has any annotations present in the class.

`Let me show an example, of what is not a POJO Class` :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683375553582/691f8a41-f0b3-4ed3-8454-e45b395212a7.png align="center")

Explanation: Above class i.e., CricketPlayer1 is <mark>not</mark> a POJO class as it extends Class Player.

## JAVA BEANS CLASS

For a Java Bean Class, One Class should possess four features:

1. <mark>Its variables should be declared private.</mark>
    
2. <mark>Variables getter and setter methods should be public.</mark>
    
3. <mark>The class should have a zero arg constructor (basically by default a Java class has a zero args constructor).</mark>
    
4. <mark>The class must implement a java.io.serializable interface.</mark>
    
    `Let me give an example to have a better understanding of what a Java Bean Class is:`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683376623622/0f441968-1a54-4ebf-9a26-c4c182147d7b.png align="center")
    
    Explanation: The above class is Java Bean as it implements java.io.serializable,it's variables are declared private, it has a zero arg constructor(u can skip it also, as it is by default present in Java Class) and all the getters and setters methods are public.