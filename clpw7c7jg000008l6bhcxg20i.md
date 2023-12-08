---
title: "Spring Boot 3  updates -JDK 17 and jakarta.* ?"
seoTitle: "spring boot 3"
seoDescription: ""Elevate your coding experience with Spring Boot 3 – the latest evolution in Java development. Streamlined, efficient, and packed with new features for buil"
datePublished: Fri Dec 08 2023 05:44:09 GMT+0000 (Coordinated Universal Time)
cuid: clpw7c7jg000008l6bhcxg20i
slug: spring-boot-3-updates-jdk-17-and-jakarta
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701955564978/c056f42e-d81d-4d84-abe2-be33b0386953.png
tags: spring, programming-blogs, java, javascript, technology, python, web-development, backend, springboot, spring-framework, spring-security, technical-writing-1, spring-data-jpa

---

1. **S**pringBoot uses Spring version 6 and JDK 17(base Jdk).
    
    **<mark>Base JDK Support is 17 for SpringBoot 3. Every three years now a LTS(Long Term Support version will be released).SpringBoot 3 does not support the Jdk version below 17. Jdk 17 and 21 are the current LTS versions.SpringBoot 3 supports Spring 6 and JPA3.</mark>**
    
    `Official Statement :` Spring Boot 3.2.0 requires [Java 17](https://www.java.com/) and is compatible up to and including Java 21. [Spring Framework 6.1.1](https://docs.spring.io/spring-framework/reference/6.1/) or above is also required.
    
    **If you try to run the project with a version down from 17 it will give u error like java.lang.UnsupportedClassVersionError: org/springframework/boot/SpringApplication has been compiled by a more recent version of the Java Runtime (class file version 61.0), this version of the Java Runtime only recognizes class file versions up to 55.0**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701961203568/8e4d7d91-d5a5-48a0-90e7-c9ed2d37bddc.png align="center")
    
    For more reference study the official documentation by clicking the given below link:
    

[SpringBoot 3 System Requirements official Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started.html#getting-started.system-requirements)

1. *javax.\** packages have been removed from Spring Boot 2 and upgraded to jakarta.\* in Spring Boot 3.
    
    In September 2017, Oracle decided to give away the rights for Java EE to the Eclipse Foundation (the language still owned by Oracle).
    
    <mark>I</mark>**<mark>n the past, when Oracle owned Java Enterprise Edition, it was known as Java EE. However, when ownership was transferred to the Eclipse Foundation, the name had to be changed since Java SE (Core Java) is still owned by Oracle. This change was necessary to avoid a naming conflict, as both Java SE and Java EE contain "Java" in their names. As a result, the Eclipse team chose "Jakarta EE" as the new name for Java EE</mark>**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701959000755/4c5c4ae5-48f7-4f7e-9d34-f81adc2f2513.png align="center")
    
    `Official Statement before release of Spring Boot 3:`
    
    The entire Spring team, and many in our community of contributors, are now preparing for the next generation of Spring.
    
    This next major revision will be based on Spring Framework 6.0 and will require Java 17 or above. It will also be the first version of Spring Boot that makes use of Jakarta EE 9 APIs (jakarta.\*) instead of EE 8 (javax.\*).
    
    Since JPA(Java Persistence API) was a part of Java EE and after Java EE was renamed to Jakarta EE .thus as a result of it, Java Persistence API has been renamed to Jakarta Persistence API. So, now classes and interfaces of JPA also come from the name jakarta.\*
    
    in the below image, classes and interfaces are imported from jakarta.\* in a class of spring Boot 3 project.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701961080689/f0ccfb75-0258-4796-977f-7d4797db5794.png align="center")
    
2. Earlier, in Spring Boot 2 it used to import classes from javax.\* packages for Java EE and JPA classes and interfaces as u can see in the below image.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701961644558/58cbf3de-9e1f-459b-9b9f-0bbccdc932cb.png align="center")
    
    For more reference in this context follow the links given below.
    
    [https://spring.io/blog/2022/05/24/preparing-for-spring-boot-3-0](https://spring.io/blog/2022/05/24/preparing-for-spring-boot-3-0)
    
    [https://www.baeldung.com/java-enterprise-evolution](https://www.baeldung.com/java-enterprise-evolution)