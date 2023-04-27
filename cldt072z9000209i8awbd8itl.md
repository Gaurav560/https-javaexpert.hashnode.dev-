---
title: "Static Queries of SQL in Java(Jdbc)"
seoTitle: "sql static queries with java and jdbc"
seoDescription: "implementation of static queries in SQL through java and jdbc and MySQL database."
datePublished: Mon Feb 06 2023 16:04:25 GMT+0000 (Coordinated Universal Time)
cuid: cldt072z9000209i8awbd8itl
slug: static-queries-of-sql-in-javajdbc
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1675689568627/86f116fd-71f7-4381-939a-6f8e45647be7.png
tags: programming-blogs, java, mysql, sql, jdbc

---

INTRO: Static queries are those queries in which we insert the query early before the runtime of the program. these are also called hard-coded queries that cannot be altered once the program executes.

> In SQL with Java, there are only two types of queries

1. Select Queries
    
2. Non-Select Queries
    

# Select Queries:

Those queries which are used for searching data within records in tables are called select Queries. example: I have created a database named **juniorg** in MySQL Workbench and created a table within that database named **brothers**. I have inserted some records and I want to fetch them through the java program.

> **Java utility code**: I have written a java utility code in which I have written code for establishing a connection of my java program with the MySQL database and cleanup code for the closing of resources. (reusable code which will be used in my every jdbc program).

> **Properties file**: I have also created a properties file in which we can keep data in form of key-value pairs. so that we don't have to write the main code again and again with respect to different URLs, usernames, passwords, etc.

utility code:

```

package in.ineuron.util;

import java.io.FileInputStream;
import java.io.IOException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Properties;
import java.util.Scanner;

public class jdbcUtility {
	
	//private constructor ko bana rahe hain taaki koi is class ka object bana ke iske method ko call nahi kar sake .
	private jdbcUtility(){}

	public static Connection jdbcGetConnection() throws IOException, SQLException
	{
		
		//connecting the application properties file with java utility file
		FileInputStream fis=new FileInputStream("E:\\Java_Programs_Eclipse\\jdbcSelfPractice\\application1.properties");
		Properties properties=new Properties();
		properties.load(fis);
		
		//establishing the connection 
		System.out.println("establishing jdbc connection ");
		Connection connection =DriverManager.getConnection(properties.getProperty("url"),properties.getProperty("username"),properties.getProperty("password"));
		return connection;
	}
	
	
	//method to clean up the resources 
	public static  void CleanUp(Connection connection,Statement statement,ResultSet resultSet) throws SQLException
	{
		if (connection!=null) 
		{
			connection.close();
		}
		if(statement!=null) {
			statement.close();
		}
		if(resultSet!=null) {
	resultSet.close();
		}
		
		
	}
}
```

properties file:

```

url=jdbc:mysql:///juniorg
username=root
password=Lumia@540
```

### java code to select all records from table brothers:

---

```

package jdbcSelfPractice;

import java.io.IOException;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import in.ineuron.util.jdbcUtility;

public class SelectQueryWithApplicationProperties {

	public static void main(String[] args) {
		Connection connection=null;
		Statement statement=null;
		ResultSet resultSet=null;
	try {
		connection=jdbcUtility.jdbcGetConnection();
		if (connection!=null) {
			statement=connection.createStatement();
		}
		if (statement!=null) {
			resultSet=statement.executeQuery("select * from brothers;");
		}
		
		if (resultSet!=null) {
			System.out.println("pid\tname\tage\taddress\tphone");
			while(resultSet.next())
			{
				System.out.println("\n");
				int pid=resultSet.getInt(1);
				String name=resultSet.getString(2);
				int age=resultSet.getInt(3);
				String address=resultSet.getString(4);
				String phone=resultSet.getString(5);
				System.out.printf(pid+"\t"+name+"\t"+age+"\t"+address+"\t"+phone);
			}
		}
		
	} catch (IOException ie) {
	ie.printStackTrace();
	}
	catch (SQLException se) {
		se.printStackTrace();
	}
	catch (Exception e) {
		e.printStackTrace();
	}finally {
		try {
			jdbcUtility.CleanUp(connection, statement, resultSet);
		} catch (SQLException e2) {
			e2.printStackTrace();
		}
	}


	}

}
```

output:

```
establishing jdbc connection 
pid	name	age	address	phone


2	aryan	18	berlin	5063568905

3	amar	24	paris	437886464

4	piyusg	16	tokyo	803605896

5	sameer	19	brazil	425745854

6	puchu	14	kyoto	408890544

9	goku	24	gaya	45804568
```

# Non-Select Static Queries(Insert,Delete,Update)

those static queries in which any operation can be done with data except search the query are called non-select queries. e.g: deletion, insertion, or updation of data within records or tables. we will see how to insert a record in a table, how to delete a record in a table, and how to update a record in a table.

### Inserting a record in a table with the help of a static SQL query (java program):
---
```

package jdbcSelfPractice;

import java.io.IOException;
import java.sql.Connection;
import java.sql.SQLException;
import java.sql.Statement;

import in.ineuron.util.jdbcUtility;

public class NormalInsertApp {

	public static void main(String[] args) {
		Connection connection=null;
		Statement statement=null;
		Integer integer=null;
	try {
		connection=jdbcUtility.jdbcGetConnection();
		if (connection!=null) {
			statement=connection.createStatement();
		}
		if (statement!=null) {
			integer=statement.executeUpdate("insert into brothers values(7,'ankit',23,'kashipur','70554345855');");
		}
		if (integer!=null) {
			System.out.println("no of rows affected is :"+integer);
		}
		
	} catch (IOException ie) {
	ie.printStackTrace();
	}
	catch (SQLException se) {
		se.printStackTrace();
	}
	catch (Exception e) {
		e.printStackTrace();
	}finally {
		try {
			jdbcUtility.CleanUp(connection, statement, null);
		} catch (SQLException e2) {
			e2.printStackTrace();
		}
	}

	}

}
```

output:

```
establishing jdbc connection 
no of rows affected is :1
```

Adding screenshot of inserted record:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675697228728/53508f98-bc74-4429-b0c5-679f1535a75c.png align="center")

### Deleting a record in a table with the help of a static SQL query (java program):
---
```
package jdbcSelfPractice;

import java.io.IOException;
import java.sql.Connection;
import java.sql.SQLException;
import java.sql.Statement;

import in.ineuron.util.jdbcUtility;

public class NormalDeleteApp {

	public static void main(String[] args) {
		Connection connection=null;
		Statement statement=null;
		Integer integer=null;
	try {
		connection=jdbcUtility.jdbcGetConnection();
		if (connection!=null) {
			statement=connection.createStatement();
		}
		if (statement!=null) {
			integer=statement.executeUpdate("delete from brothers where pid=7;");
		}
		if (integer!=null) {
			System.out.println("no of rows affected is :"+integer);
		}
		
	} catch (IOException ie) {
	ie.printStackTrace();
	}
	catch (SQLException se) {
		se.printStackTrace();
	}
	catch (Exception e) {
		e.printStackTrace();
	}finally {
		try {
			jdbcUtility.CleanUp(connection, statement, null);
		} catch (SQLException e2) {
			e2.printStackTrace();
		}
	}


	}

}
```

output:

```
 establishing jdbc connection no of rows affected is :1
```

deletion of the last record which was inserted:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675698049364/ff3432f0-f33f-4065-b142-2703838f53d9.png align="center")

### Updating a record in a table with the help of a static SQL query (java program):
---
```
package jdbcSelfPractice;

import java.io.IOException;
import java.sql.Connection;
import java.sql.SQLException;
import java.sql.Statement;

import in.ineuron.util.jdbcUtility;

public class NormalUpdateApp {

	public static void main(String[] args) {
		Connection connection=null;
		Statement statement=null;
		Integer integer=null;
	try {
		connection=jdbcUtility.jdbcGetConnection();
		if (connection!=null) {
			statement=connection.createStatement();
		}
		if (statement!=null) {
			integer=statement.executeUpdate("update brothers set address='Patna' where name='sameer';");
	

		}
		if (integer!=null) {
			System.out.println("no of rows affected is :"+integer);
		}
		
	} catch (IOException ie) {
	ie.printStackTrace();
	}
	catch (SQLException se) {
		se.printStackTrace();
	}
	catch (Exception e) {
		e.printStackTrace();
	}finally {
		try {
			jdbcUtility.CleanUp(connection, statement, null);
		} catch (SQLException e2) {
			e2.printStackTrace();
		}
	}


	}

}
```

output:

```
 establishing jdbc connection no of rows affected is :1
```

screenshot output:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675698436500/6bbda1ec-de7f-4a64-b9bf-630433080a98.png align="center")


>Note: please write all code to understand all the concepts clearly. And subscribe to my newsletter to get updates about my articles.