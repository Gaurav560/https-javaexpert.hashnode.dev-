---
title: "Demystifying Java Records: 
Simply Better Data Handling"
seoTitle: "record in java"
seoDescription: "Unlock the efficiency of Java Records – a game-changer for streamlined and readable data classes.
Java Records: Streamlined, Readable, Efficient."
datePublished: Sat Dec 09 2023 01:06:45 GMT+0000 (Coordinated Universal Time)
cuid: clpxcvc8o000008l6auvz1wil
slug: demystifying-java-records-simply-better-data-handling
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702071142431/857103bd-e6cd-49be-b667-d168078e4a67.png
tags: spring, java, javascript, technology, python, web-development, 100daysofcode, springboot, spring-framework, technical-writing-1, recordsinjava

---

## Introduction

Java has often been labeled as a verbose language, requiring extensive code even for simple tasks. In a quest to tackle this verbosity, the 14th version of Java introduced a game-changer – the Record class. This special addition of Record in Java aims to simplify and streamline how we write code, particularly for classes that store model data.

Let's delve into the evolution of Java and uncover how the introduction of Records marks a significant step towards a more concise and efficient coding experience.

<mark>Java record is a simple model class to hold and transfer data. This feature was part of Project Amber, an OpenJDK project aimed at improving productivity for Java developers by bringing more expressive and readable syntax to the language.</mark>

## What specific issue does this Record aim to address?

Imagine you're setting up a system to manage student information. In old Java days, the approach would involve creating a class loaded with fields, a constructor, getters, setters, and perhaps even equals(), hashCode(), and toString() methods. That's quite a bit of repetitive code for the simple task of storing data.

Records simplify this process. They act as a quick shortcut for classes that essentially hold data.

### Practical Explanation

Before the introduction of records, creating a simple class like Student to store student data was a rather verbose process.

It involved manually defining fields, creating getters and setters, crafting constructors, and implementing methods for equality comparison equal(), hash code generation hashcode(), and creating a string representation toString().

This traditional approach demanded a significant amount of boilerplate code and could make even a simple class quite long.

However, with records, this process has been simplified into a concise, one-liner declaration, significantly reducing the verbosity associated with data-centric classes.

```java
import java.util.Objects;

public class Student {
    private int studentId;
    private String studentName;
    private String studentAddress;

    public Student(int studentId, String studentName, String studentAddress) {
        this.studentId = studentId;
        this.studentName = studentName;
        this.studentAddress = studentAddress;
    }

    public int getStudentId() {
        return studentId;
    }

    public void setStudentId(int studentId) {
        this.studentId = studentId;
    }

    public String getStudentName() {
        return studentName;
    }

    public void setStudentName(String studentName) {
        this.studentName = studentName;
    }

    public String getStudentAddress() {
        return studentAddress;
    }

    public void setStudentAddress(String studentAddress) {
        this.studentAddress = studentAddress;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return studentId == student.studentId &&
                studentName.equals(student.studentName) &&
                studentAddress.equals(student.studentAddress);
    }

    @Override
    public int hashCode() {
        return Objects.hash(studentId, studentName, studentAddress);
    }

    @Override
    public String toString() {
        return "Student{" +
                "studentId=" + studentId +
                ", studentName='" + studentName + '\'' +
                ", studentAddress='" + studentAddress + '\'' +
                '}';
    }
}
```

<mark>After the introduction of Record, With just a single line, you turn your above nearly 50 lines of code into a single line code.</mark>

we pass the fields of the class into the parameters of the record. Rest everything will be taken care of at the backend. You don't have to do anything else. You just use the record as your logic demands.

```java
public record StudentRecord(int studentId, String studentName, String studentAddress) {}
```

That's it. One line of code now accomplishes what used to take 50 lines in earlier versions of Java.

# When to Choose Records?

You might be wondering, "When should I use records?" Well, records are perfect when your class's primary role is to store data without a ton of additional logic.

If you're dealing with configurations, database data, or just passing information around, records are your new best friends.

<mark>But here's the key point to remember: once you've stored data in a record, you won't be able to modify the data present in fields of record. There is no setter method in the record to set the data. There is no chance of going back. So always think of scenarios while creating a record in your project.</mark>

## Some Important points to keep in mind about records

* **Immutable Nature:** Records in Java are immutable by default, meaning once you've set their values, you can't change them. This helps in creating more predictable and thread-safe code.
    
* **Automatic Methods:** Records automatically generate methods like `equals()`, `hashCode()`, and `toString()` based on the fields declared in the record. This reduces boilerplate code significantly.
    
* **No Explicit Getters and Setters:** Records eliminate the need for explicit getter and setter methods. The fields themselves act as getters, and records don't support setters since they're immutable.
    
    ```java
    public record Student(int studentId, String studentName, String studentAddress) {
        // Additional methods or fields specific to the Student record can be added here if needed
    }
    
    public class Main {
        public static void main(String[] args) {
            // Create a Student record instance
            Student student = new Student(14, "Gaurav Sharma", "India");
    
            // Attempt to modify a field (this will result in a compilation error)
            // student.studentId(11);  // Uncommenting this line will result in a compilation error
    
            // Accessing fields using the automatically generated getters
            int studentId = student.studentId();
            String studentName = student.studentName();
            String studentAddress = student.studentAddress();
    
            // Printing the retrieved values
            System.out.println("Student ID: " + studentId);
            System.out.println("Student Name: " + studentName);
            System.out.println("Student Address: " + studentAddress);
        }
    }
    ```
    
* **Field Order Matters:** The order of fields in a record's declaration defines the order of parameters in the automatically generated constructor and the order of components in the `toString()` method.
    
* **Final by Default:** Records are implicitly `final`, meaning they cannot be further subclassed. If you attempt to extend a record, you'll get a compilation error. This restriction ensures that the behavior of records, particularly their automatic methods, remains consistent.
    
* ```java
    // Attempting to extend the Student record
    // This will result in a compilation error
    // public class ExtendedStudent extends Student {
    //     // Compilation error: 'ExtendedStudent' cannot inherit from final 'Student'
    // }
    ```
    
* In Java, records can implement interfaces just like regular classes. When a record implements an interface, it means that the record class agrees to provide concrete implementations for all the methods declared in that interface.
    
    In the below code,u can see that we have a record named Student that has three fields and implements an interface Displayable.
    
    ```java
    interface Displayable {
        void display();
    }
    
    public record Student(int studentId, String studentName, String studentAddress) implements Displayable {
        @Override
        public void display() {
            System.out.println("Student Information:\n" +
                    "ID: " + studentId +
                    "\nName: " + studentName +
                    "\nAddress: " + studentAddress);
        }
    
    }
    ```
    
    Now, Create an object of record Student and call the overridden method display() present in the interface Displayable.
    
    ```java
    public class Main {
        public static void main(String[] args) {
            // Create a Student record instance
            Student student = new Student(11, "Gaurav Sharma", "India");
    
            // Invoke the display() method to print student information
            student.display();
        }
    }
    ```
    
    o/p:
    
    ```java
    Student Information:
    ID: 11
    Name: Gaurav Sharma
    Address: India
    ```
    
* **Backward Compatibility:** While records were introduced in Java 14, they are fully backward compatible. This means you can use them in newer Java versions and still run your code on older versions without any issues.
    

<mark>THE END.</mark>

Thank you for taking the time to read this article. If you'd like to explore more content like this, consider subscribing. Crafting these explanations involves extensive research and hard work over several days. Your support through subscribing is greatly appreciated.

Stay tuned for more insightful articles.

Feel free to let me know if you have any specific preferences or adjustments you'd like!

Let's connect:

Linkedin: [https://www.linkedin.com/in/gaurav4044/](https://www.linkedin.com/in/gaurav4044/)

Github: [https://www.linkedin.com/in/gaurav4044/](https://www.linkedin.com/in/gaurav4044/)