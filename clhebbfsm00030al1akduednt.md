---
title: "new vs newInstance() In Java"
datePublished: Mon May 08 2023 03:58:01 GMT+0000 (Coordinated Universal Time)
cuid: clhebbfsm00030al1akduednt
slug: new-vs-newinstance-in-java
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677070374290/bb5bd907-970c-4c20-84be-0916c3795ee5.png
tags: programming, java, web-development, hashnode, wemakedevs

---

## <mark>Briefing:</mark>

Often we have heard and used new and newInstance() in Java but many of them use it without knowing the actual meaning of both. So In this article, i will try to give you a good understanding of both. First of all, we will know, what is a new keyword and then slowly we move to what problems were faced by developers using a new keyword, then we will talk about the newInstance () method and how the newInstance() method helps to solve a specific type of problem developers faced while only using new operator.

## <mark>Introduction:</mark>

new is a keyword and newInstance is a method of a Class class in Java.

`Note: Class is the name of a predefined class in Java. Just like, String is the name of a predefined class in Java which has several methods. The Scanner is also the name of a pre-defined class in Java that has also several methods. So, a Class is also the name of a predefined class in Java.`

Both new and newInstance() are used for creating objects In java. Let's discuss the new keyword first.

## <mark>new keyword in Java</mark>

### <mark>First of all, What is a keyword?</mark>

There are some special reserved words in Java that one cannot use for naming a variable, class or object. We call these reserved words keywords in Java. Each keyword has a special meaning associated with it. These keywords are given by the Sun MicroSystems team (Developer of Java Language) which is understandable by the Java compiler. When the Java compiler sees these keywords, the compiler understands what task it should perform.

For naming variables, methods and classes in Java, we use identifiers that have some set of conventions.

Now, We have understood the meaning of keywords.

### <mark>So, what does a new keyword do?</mark>

In simple words, a new keyword is used to create an object of a class. But there is a catch and the catch is that information about the class for which you want to create an object should be known to the compiler and JVM in advance. In more simple words, we know for which class we are creating an object before run time.

Let's understand it through the code:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683505776902/cc500211-957f-471f-97bc-bef99344b9c2.png align="center")

here we are trying to create an object of the Player class and the object is p1.

<mark>Behind the scenes:</mark>

1. new keyword will create a memory in the heap area. (Don't panic if you don't know about heap area. It is just an area where objects are created.)
    
2. after new keyword, Player() is written in the code .It means that JVM will start to search the Player.class file in the current working directory. If the .class file is found, then the memory in the heap area which was created previously by new keyword will be assigned to the Player Class object. And if the Player.class file is not found, it will result in an erro called NoClassDefFoundError.
    
    There are many steps behind the scene when u use a new Keyword to create an object. But let's not go in too much depth and try to focus on what new vs newInstance() is.
    

`Note: Java Virtual Machine(JVM) - it executes the code internally line by line`

### <mark>Why newInstance() came into existence?</mark>

When you study further in Java like Web Development, There will be many scenarios where we have to create an object of a class during runtime, as we will not be knowing what is the name of the class for which we want to create an object before runtime. So, Here comes the hero called the newInstance() method of the Class class.

`Note: We can't create object at runtime with the help of a new keyword.`

## <mark>newInstance() method</mark>

This newInstance() method is used to create an object of the class at run time.

Understanding with the help of code:

`Code Written in Editor:`

```java


//Footballer Class
class Footballer{
	
	
}

//main Class 
public class Test1 {

	public static void main(String[] args) throws Exception
	{

//code for object creation at runtime .
		Object o1=Class.forName(args[0]).newInstance();
		


		//it will return the class Name for which object has been created .
System.out.println("Object is created for class ::"+o1.getClass().getName());
	}

}
```

`Command Prompt Code:`

```java
//compiling the Test1.java
javac Test1.java

//executing Test1.class and passing Class name (Footballer ) as an argument  in args[0] at runtime to create new object with newInstance() method
java Test1 Footballer

//output: 
Object is created for class ::Footballer
```

`The code explanation (creating an object at runtime) :`

1. In Java, forName is a method of the Class class
    
2. The main work of Class.forName() is that it loads the class to be executed.
    
3. Thus, we passed the Footballer class name as a string in args\[0\] in the main method parameter section while executing Test1.class.
    
4. Now the Footballer class is loaded at run time so, object creation will also take place at runtime.
    
5. when the newInstance() method will be executed, an object will be created of class Footballer at runtime.
    

## <mark>Some practical scenarios where newInstance() is used</mark>

> 1. `While you read Spring-core, there is a concept of dependency injection in which an object of the dependent class is injected into an object of the Target class. This can be done by Spring Ioc Container called ApplicationContext.In the background, it creates objects at runtime and does the dependency injection. All the headache work is done by spring containers. we just have to configure the XML file and tell which one is the dependent class and which one is the target class.`
>     
> 2. `The second Real scenario is, in Advanced Java, Tomcat Engine or Catalina container creates the object of Servlet class at runtime. Behind the scene,the container doesn't know for which servlet the request will come, so at runtime after fetching the servlet name from the XML file, it uses internally newInstance() to create an object of the Servlet class.`
>     

## <mark>Summary and important points to be taken care of :</mark>

> 1. `If u don't know the class name at the beginning and if the class name is available at run time, then go for the newInstance() method.`
>     
> 2. `Remember, for newInstance() method to execute, there must be a zero-argument constructor present in the class because newInstance() method uses only the zero-arg-constructor internally. If there will not be any zero -arg-constructor present in the class (by default or manually ), it will give InstantionException.`
>     
> 3. `But while creating an object with the new keyword, we can use any no of the parametrized constructor.`
>     
> 4. `If we are creating an object using a new keyword and the class is not present for which we want to create an object, then it will result in a runtime Exception called NoClassDefFoundError.`
>     
> 5. `But if we are creating an object using newInstance() method, and at runtime that class is not present for which object creation is going to take place, then it will result in a run time Exception called ClassNotFound Exception.`
>