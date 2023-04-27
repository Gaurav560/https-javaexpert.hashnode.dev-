---
title: "What is String args[] in the main method in Java?"
datePublished: Wed Feb 15 2023 07:33:43 GMT+0000 (Coordinated Universal Time)
cuid: cle5cwzgh000l09mk63yte1bc
slug: what-is-string-args-in-the-main-method-in-java
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1676442683727/90ac496c-520b-4a54-b1da-0f379ad2df5c.png
tags: java

---

# Intro

`public static void main (String args[]){}`

prerequisites: Very basic knowledge of methods, CommandLine, Arrays, and Strings in java.

Have you ever wondered what is String args[ ] in the main method? If yes and you haven't found an answer then you are at the right place.

As we know, any method in Java can take specific inputs as parameters and perform any specific operations with those inputs and return output. The same goes for Java's main method also. String args[ ] is nothing but an array of Strings. the array name itself is args and it takes strings as inputs .and this args[ ] array works as a parameter for taking input to the main method.

### how is input given into the args[ ] array?

There are many ways in which you can send input to your java program such as through different inbuilt or predefined classes such as Scanner class, String buffered reader, etc and you can also give input through the command line. And input in the args\[\] array is also given through the command line and that's why it is also called command line arguments.

`note:the indexing of array args[] starts from 0.`

### what to do with the inputs taken as Strings in args[ ] ?

You can do anything withing with the inputs you have taken from the command line such as for any String operations in your java program or you can convert them from String to any other datatype and use it according to your program.
 ### Learning through the example 
I have made a demo.java file. Now I will compile it and pass the arguments while executing the demo.java file. Here, I have passed Gaurav Sharma as my arguments in the args\[\] array. Now args\[0\] will store Gaurav and args\[1\] will store Sharma.

```
class demo{
    public static void main (String args[]){
        System.out.println("hello my name is gaurav sharma");
        System.out.println("args[0]"+args[0]);
        System.out.println("args[1]"+args[1]);
    }
}
```

`Note: You have to pass arguments while executing the java program and you can only pass arguments through the command prompt while executing the program that's why it is called Command Line Arguments.`

Command Line:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676445463393/feb15c34-7ab1-4393-bfad-993e29fddab7.png align="center")

As in the command line, you can see I have compiled the demo.java and passed gaurav Sharma as arguments while executing the demo class.
`And the output is` :args[0]Gaurav and args[1]Sharma

`Note: Always compile with the file name and execute with the class name of your java program.
There is no compulsion of writing array name as args .you can write any name .it is a general convention we follow in the java community to understand each other code in a much better way .`

#### Subscribe to my newsletter at Hashnode to read more such content. And you can always help by sponsoring my blogs at Hashnode.
