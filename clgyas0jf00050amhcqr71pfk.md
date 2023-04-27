---
title: "Understanding Jvm / Jre / Jdk  in Java"
datePublished: Wed Apr 26 2023 22:58:36 GMT+0000 (Coordinated Universal Time)
cuid: clgyas0jf00050amhcqr71pfk
slug: understanding-jvm-jre-jdk-in-java
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682457961196/a543b7f9-0a84-48c4-98a7-f35158cfc984.png
tags: java, web-development, backend, hashnode, wemakedevs

---

# JVM(Java Virtual Machine)

Jvm stands for Java Virtual Machine.It is the heart of the Java ecosystem. Through this only, Java programs are called WORA(Write Once Run Anywhere) programs which made Java so popular across the globe for writing code.

> A <mark>virtual machine </mark> is just a virtual representation of a Physical computer. We run this virtual machine on some physical machine or computer. this physical computer is called the Host machine and the virtual machine is called the guest machine.
> 
> <mark>WORA</mark>\-Write Once Use Anywhere. It means when you write any Java code and compiles it, the compiler converts the .java file into a .class file (byte-code ).and this .class file, you can share with anybody and they can run this file on their machine with their respective operating system Jre(Don't worry,u will understand this line later in the article). But it is not possible with other languages such as c or C++. Thus, Java programs are called WORA.

Now, Here comes in Picture, Jvm. Jvm takes the .class file (also called byte code ) and starts to execute the program line by line. This Java virtual machine internally uses an Interpreter and executes the Java code line by line. If any error exists in any line, then after that line remaining code will not be executed.

> note: JVM only by itself cannot execute a Java program .it needs the help of some inbuilt files called library files and an environemnt to execute the program. Here comes in picture, Java Runtime Environment. Sun MicroSystems(the creator of Java ) provides another technology called Jre(Java runtime environment) to help JVM execute the program.

There is much more to JVM, but we will not deep dive too much into that.

# JRE(Java Runtime Environment)

Java Runtime Environment is a program used to communicate with our operating system. Communication with the operating system is required as our program or code needs memory access to store variables or object data or to execute code. Our programs also need different system resources like program files and some additional files to execute the program smoothly.

### `why Jre?`

Any program you execute needs a runtime environment. Earlier, when Java Runtime Environment was not there, the Operating system acted as a run time environment for the programs.

But using the operating system as a runtime environment tightly binds our code. For differnet operating systems, you have to write different codes to run the same program.

And as always tightly binding is not a good practice in Java. we always want our programs to be loosely bounded. So, Here Java team comes up with a solution to make Developer's life easy and made different Jre for different operating systems,so developers don't have to write code again and again for different operating systems. This also made Java very Popular as it also supports the WORA feature of Java.

### `Now you ask what is the runtime environment.`

Runtime Environment is a virtual environment in which programs that are to be executed will be provided with memory access by communicating with the operating system and also be provided with some library classes, program files etc which are needed for smooth execution of a program.

> Note: <mark>JRE </mark> is a <mark>battlefield</mark> whereas <mark>JVM </mark> is our <mark> weapon </mark> to execute the Java program on the battlefield.
> 
> If you want to <mark>only run</mark> the Java program,u need to only install JRE on your machine. JRE consists of <mark>Jvm+Library Files</mark>.

# JDK(Java Development Kit)

As the name suggests, Jdk is a technology given by the creators of Java i.e. Sun MicroSystems.It is used by developers to develop Java applications. Developers need to write the Java program, then compile the program and then finally run or execute the program. All this process i.e. compilation, and execution of the program is done by Jdk. Jdk is nothing but an extension of Jre. If you add development tools into Jre, then Jdk will be created.

> <mark>Jdk</mark> is a whole package that consists of <mark>Jvm+jre +devlopement tools</mark>. If u want to <mark>develop, compile and run the application</mark>, then you need to install JDK on your local machine. Right Now, JDK 8 is the most stable version in the world. Many softwares had been built on this version.

## One image to understand it all.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682548533200/fbeb788b-26ba-48c6-bc97-91d12348f39a.png align="center")

### `Explanation of image:`

Inside Jdk -&gt;Jre+Developement tools

Inside Jre-&gt;Jvm+Library Classes and other files

---

Connect with me for more such content:

`Github:`[https://github.com/Gaurav560](https://github.com/Gaurav560)

`Linkedin:`[https://www.linkedin.com/in/gaurav4044/](https://www.linkedin.com/in/gaurav4044/)

`Twitter:`[https://twitter.com/Sharma1809157](https://twitter.com/Sharma1809157)