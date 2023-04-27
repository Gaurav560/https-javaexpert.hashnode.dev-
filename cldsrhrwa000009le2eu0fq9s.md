---
title: "Path vs ClassPath in Java"
seoTitle: "path variable vs classpath variable in java"
seoDescription: "this article describes what is path and classpath variable and how to setup both in java ."
datePublished: Mon Feb 06 2023 12:00:48 GMT+0000 (Coordinated Universal Time)
cuid: cldsrhrwa000009le2eu0fq9s
slug: path-vs-classpath-in-java
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1675607785841/7d4c5109-9b42-44f6-9039-58a7321395dd.png
tags: java, mysql, jdbc, path-variable, classpath

---

Intro:
We all know that our operating system is nothing but a software with a GUI interface where we can do most of our normal tasks. but if we have to give the command to our operating system without a graphic user interface to do certain tasks then we have to tell it through Command Prompt or terminal.

## *1.  Path in Java*
------------------------------
Now, let's suppose we installed java from oracle and have written some program in notepad or any code editor and tried to compile and run that program directly in the command prompt or editor without setting the path of java executable files, then that program will not execute and it will give you an **error** like javac or java is not recognized as an internal or external command.
![java is not recognised as an internal or external command](https://itknowledgeexchange.techtarget.com/coffee-talk/files/2022/06/java-not-recognized.jpg)
As we have already  installed java on our computer but then also we are not able to compile and run the java program we have written because :

**The problem is that we have to explicitly tell our operating system software where the executable java files( .exe files-the files which will execute our java program and gives result) are present in our computer so that the operating system can tell the executable files to execute those java programs. By this,  the concept of the path is required. we tell the path of our executable files to our operating system.**

#### *How to Set the path variable in our computer*
-------------------------------------------------------
prerequisite: Download the java file(JDK lastest or JDK 8) from Oracle
Step 1: Go to the directory where you downloaded java and open the bin folder 
Step 2: Copy the path of the bin folder 
![](https://3.bp.blogspot.com/-gVnbMUPgyLI/W2mSjefqd7I/AAAAAAAAIZg/PN84Tqx7hYgUUqXSFwwp_xBr7DVWBQjwwCLcBGAs/s1600/6.jpg)
Step 3: go to System Properties->advanced->environmental variables->userVariables
![](https://www.imatest.com/wp-content/uploads/2017/02/EnvVars_SystemProperties.png)
Step 4: click on new and then give the Variable name as Path
![](https://helpdeskgeek.com/wp-content/pictures/2012/09/environment-variables-dialog.png)
Step 5: Give the variable path as the path which u have copied from the bin folder.
Step 6: Click on ok and then close.
Hooray! your path variable is set.
Now you're ready to run your java program on the terminal or any editor.

## *2. ClassPath In Java*
-----------------------------------------
This classpath variable is used to tell Java or JVM where our user-defined classes or packages are present inside the computer so that JVM can execute those class file. 
Example: Suppose we have a class file named School. class and inside that class file we have another class file called Student. class.
And if both class files are in the same directory and if we compile School.class then School.class file will compile well and give results but if both class files are in different directories and we are compiling School.class file then the Jvm will throw an error as it does not know the path of Student.class file .**in this case, we have to explicitly tell JVM where our Student.class file is present in the computer. Only this basic concept is known as setting up the ClassPath variable. Now, if we explicitly tell the path of Student.class file to JVM and then compile School.class, then it will work fine and will give the desired output.

### ClassPath in JDBC:
 ------------------------ 
 Jdbc is an API(a collection of classes, interfaces, and packages called an API) that consists of interfaces that are implemented by different database companies such as MySql, Oracle, MariaDB, etc. These companies implement the jdbc interface and write their own class called Driver or connector class to connect any java program with their database. 
And we have to download their connector files from their official websites.

I am taking the example of the MySQL database. In the MySQL database, we have to download a jar file called connector.jar which contains the Driver class that connects java programs with their database . And when we download that jar file, we have to also explicitly tell the JVM where it is present so that it can load that driver class and establish the connection between our java program and MySQL database. Only this step is called setting up the classPath Variable.

#### Steps for setting up the classpath variable :
---------------------------------------------------
it is quite similar to setting up the path variable. the only difference is that 
in Step 4:you will write the variable name as classpath and the variable path as the path where u have downloaded the connector.jar file.
![](https://www.researchgate.net/profile/Richard-Johnson-27/publication/324454006/figure/fig2/AS:614281703854097@1523467579836/Adding-the-CLASSPATH-variable-for-the-JDBC-driver-in-Windows-10.png).

Hooray! you are done setting up the classpath variable for the driver class.

```
Hope this article will help you. Subscribe to my newsletter for more.
```



