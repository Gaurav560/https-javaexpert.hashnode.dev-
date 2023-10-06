---
title: "Method Overloading"
seoTitle: "Method Overloading In Java"
seoDescription: "Method Overloading In Java"
datePublished: Thu Oct 05 2023 18:22:46 GMT+0000 (Coordinated Universal Time)
cuid: clndi9a1q000908l207rzg5un
slug: method-overloading
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696500160026/97b6f49a-80c7-4807-9e15-ac1eac2551a9.png
tags: artificial-intelligence, java, javascript, coding, 100daysofcode

---

## Basic Introduction

In a Java class, when there are multiple methods with the same name but different parameters, we refer to them as overloaded functions. This process is called method overloading.

Before delving into this concept, we must first understand the <mark>method signature</mark> in Java.

## Method Signature

It is nothing but a method's name and the type of its parameters. Let's see a method declaration in Java:

```java
public class Football
{
public static void strike(int i)
{
    System.out.println("striking is one way of winning the game");
}
}
```

`explanation:` in the above code, we have declared a method named strike that takes an integer-type parameter and returns void. The method signature is strike(int) i.e. method name with parameter type.

```java
public class Football
{
 public static void defend(String str)
{
    System.out.println("defending is another way of winning the game");
}
}
```

`explanation:` in the above code, the method signature is defend(String) i.e. method name with its parameter type.

<mark>Note</mark>: No two methods in a class can have the same signature. The compiler will check all the methods at compile time and throw a compilation error if two methods of the same signature exist in a single class.

for example:

```java
public class Football{
public static void strike(int i)
{
    System.out.println("striking hard is one way of winning the game");
}
 public static void strike(int j)
{
    System.out.println("tap in strike is another way of winning the game");
}
}
```

The above code throws a compilation error as the two methods have the same signature. The compiler will get confused about which method to call at runtime.

<mark>So, the first condition of method overloading is that in a class two or more methods with the same name must have different method signatures.</mark>

## Understanding through Examples

```java
public class Football
{
public static void main(String[] args)
 {
strike(10);
strike("yay football");
  }
public static void strike(int i)
{
    System.out.println("striking hard is one way of winning the game");
}
 public static void strike(String str)
{
    System.out.println("tap in strike is another way of winning the game");
}
}
```

Now, the above code has different method signatures for the same method. hence we call the strike method an overloaded method. In the main method, we are calling both methods by passing different types of arguments. The Compiler automatically will understand which method has to be called based on the type of input passed in the method argument.

o/p for the above code:

```java
striking hard is one way of winning the game 

tap in strike is another way of winning the game
```

`Some small meanings to keep in mind:`

<mark>Parameters:</mark> During the method declaration, the variables defined after the method name inside the parenthesis with their data types are called parameters.

```java
public static void strike(int i)
{
    System.out.println("striking hard is one way of winning the game");
}
```

in the above code, i is a parameter.

<mark>Arguments:</mark> when we call a function and pass the actual value of the variable defined during the method declaration, then these actual values are called arguments.

```java
public static void main(String[] args) {
    strike(10);
}
```

in the above code, the value 10 is called an argument.

<mark>Method Resolution:</mark> During the method call, the compiler decides which method to call based on the method signature. This process is called Method Resolution.

## Concept of Reference Type and RunTime Object

A very important concept to remember while using method overloading is that when we pass objects as an argument during a method call, the compiler calls and executes the method through object reference type and not run-time object. In method overloading, the run-time object is just a dummy.

Understanding through example:

```java
//Parent class of Ferrari Class
class Car
{
}
//Child Class of Car Class
class Ferrari extends Car
{
}

//Driver Class
public class Test {
//main method
    public static void main(String[] args) 
{

Test t=new Test();

//creating a runtime object of Ferrari class with
// reference type of Car class.
//Note:as in method overloading reference type of object 
//will decides which method will be called.
//here run time object is dummy.
Car c1=new Ferrari();
//so method1 with parameter as a car class object 
//will be called.
t.method1(c1);
    }
    public  void  method1(Car c){
        System.out.println("Car version ");
    }
    public void method1(Ferrari f){
        System.out.println("ferrari version ");
    }

}
```

Explanation of the above code:

* we have created a class called Car and we have created a child class of Car called Ferrari Class.
    
* Now, in the Driver class i.e. Test class, we have created a runtime object of the Ferrari class with reference to its Parent type.
    
* We have overloaded a method named method1 with parameters as an object of the Car class and Ferrari class respectively.
    
* Now, finally, we are calling the overloaded methods with the help of the object of the Test class.
    
* But the catch here is, that the object that is passed has the reference type of Car class and runtime object of Ferrari Class.
    

<mark>Note: Always in method overloading, which overloaded method to be called is done by the compiler based on the reference type of the object passed in the argument and not by the run time object.</mark>

`o/p of the above code:`

```java
Car version
```

## Automatic Promotion Concept In Method Overloading

before learning this concept, we have to keep in mind how the auto-promotion of data types takes place in Java. Let's take a look at this image:

![type promotion](https://n7b3p4s2.stackpathcdn.com/UploadFile/3614a6/type-promotion-in-java/Images/type%20promotion.jpg align="left")

<mark>Explanation: </mark> Small data types can be auto-converted into large data types.

* byte can be auto-prompted to short or if short is not present then int or long, float, or double whichever gets first by the compiler.
    
* Similarly, short can be converted automatically to int, long float, or double.
    
* Similarly, char can be converted to int, or if int is not present then long float, or double.
    
* High data type to lower data type auto promotion is not possible. example: Double cannot be converted to Float in auto promotion.
    
* Similarly, float into double.
    
* Similarly, long into a float or double whichever compiler gets.
    

### Theory:

* In Method Overloading, if during method resolution the compiler does not find the exact method signature within the class, then the Compiler will not immediately throw a compile time error but the compiler will do the auto-promotion of the argument data type of method call and check if such a method signature exists or not in the class.
    
* It will keep promoting the argument data type of method call and keep checking all the method signatures that can match the resolution.
    
* If the compiler still does not find the method signature that matches the method resolution, then it will throw a compilation error.
    

Now, let's understand this concept with a simple example.

```java
public class Test {

//overloaded method m1 with parameter type int
    public void m1(int i)
    {
        System.out.println("int-arg method");
    }

//overloaded method m1 with parameter type double
    public void m1(double d)
    {
        System.out.println("double-arg method");
    }

//main method
    public static void main(String[] args) {

        Test t = new Test();
t.m1(10);// exact match  o/p->int-arg method
        
 t.m1(10.5); //exact match  o/p-->double-arg method
        
 t.m1('a'); 
 //no exact match as argument is of char type
 //and we don't have any method m1 which takes parameter as char type.
 //thus ,the compiler will do the auto promotion of char into int and 
 //check if there is any method m1 with parameter type int .
 //if yes,compiler will execute that method.
 // o/p-->int-arg method
    }

}
```

o/p for the above code:

```java
int-arg method
double-arg method
int-arg method
```

* `The compiler checks the method call and matches it with method signatures present in the class body. If the method call matches with method signatures present in the class then it will compile successfully otherwise it will throw a Compilation error. All this is done by the compiler at compile time.`
    

## Some Important Cases to keep in mind:

### Case1

* while method resolution in overloaded methods, exact match will always get the highest priority.
    
* If two overloaded method matches with the required parameter during method resolution, and parameter objects have a relation of parent and child class, then the method having child class parameter will get the highest priority.
    

Understanding through code:

```java
public class Test {

public void m1(Object o){
    System.out.println("Object version");
}
public void m1(String s){
    System.out.println("String version");
}
    public static void main(String[] args) {

        Test t = new Test();
        t.m1(new Object());//   o/p-->Object version
        t.m1("Gaurav");  //  o/p-->String version


        t.m1(null);
//keep utmost care of this method call as argument satisfies
//both the method signatures present in the class .
//null can be satisfied in the place of String object 
//as well as Object class.

    }

}
```

<mark>Explanation of the above code:</mark> the first two method calls are pretty straightforward and match the exact method signatures present in the class but the last method calls in which argument is passed as null.it is dangerous as it passes both method signatures i.e. Object as well as String. But as we know highest priority will be given to the child class parameter and we know that the String class is the child class of the Object class.

### Case2

* if there are two or more overloaded methods and objects of different classes have been passed as parameters and those classes don't have a relation between them, and if this type of scenario occurs during a method call where null is passed as an argument then, the Compiler will get confused about which method will be given priority to execute as null satisfies all class object parameter values. Therefore it will throw a Compile Time Error.
    
* Understanding it through a simple code:
    
    ```java
    
    public class Test {
    
    public void m1(StringBuffer stringBuffer){
        System.out.println("String Buffer version");
    }
    public void m1(String s){
        System.out.println("String version");
    }
        public static void main(String[] args) {
    
            Test t = new Test();
            t.m1(new StringBuffer("Sharma"));
            t.m1("Gaurav");
    
            t.m1(null);
    //in the above liner of code ,null argument will satisfies
    //both overloaded parameters i.e. String and String Buffer.
    //so compiler will get confuse and throw COmpilation Error
    //i.e. ambiguous call.
        }
    
    }
    ```
    
    o/p of the above code:
    
    ```java
    java: reference to m1 is ambiguous
      both method m1(java.lang.StringBuffer) in JavaGeneralQuestion.Test and method m1(java.lang.String) in JavaGeneralQuestion.
    Test match
    ```
    

## Advantages of Method Overloading:

* Reduces the complexity of code as we don't have to remember many names for every function. One method with different parameters can do many works.
    
* Increase the readability and cleanliness of the code.
    

## Some Important points to always keep in mind when using method overloading.

* The method signatures of two or more methods can't be the same in a class.
    
* During method resolution, when an object is passed as an argument, only its reference type matters and not the runtime object so whatever reference type will be of that argument, the method resolution acts accordingly and executes the method that matches the parameter with reference type of argument.
    
* Auto-type promotion of arguments will always take place if there is no exact match during method resolution.
    
* If the method call has an exact match with the method signature present in the class and also matches with another method with parameters in the form of Varargs, then Varargs will be given the least priority.
    
* if during method resolution, the argument matches with two method signatures and has parameters as objects of Parent and Child class, then the method with child class parameter will execute.
    
* position of parameters and passing of arguments in those parameters play a crucial role in which method will get executed by the compiler.
    

## Connect with me for more such articles:

* Linkedin
    
    [https://www.linkedin.com/in/gaurav4044/](https://www.linkedin.com/in/gaurav4044/)
    
* Twitter
    
    [https://twitter.com/Sharma1809157](https://twitter.com/Sharma1809157)
    
* Github
    
    [https://github.com/Gaurav560](https://github.com/Gaurav560)