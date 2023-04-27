---
title: "Prepared Statement in JDBC"
seoTitle: "Prepared Statement in java"
seoDescription: "This article will let you know about prepared statements in java and how it is used to overcome a special set of a problem and increase performance."
datePublished: Sat Feb 18 2023 12:52:39 GMT+0000 (Coordinated Universal Time)
cuid: cle9ymo7z000f08jncn7ba4j7
slug: prepared-statement-in-jdbc
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1676723628529/b9b3d0d9-412e-4b43-9adc-f3be46e7e072.png
tags: java, mysql, sql, jdbc, advance-java

---

### prerequisites

1. How to create a connection object and establish a connection between a java application and a database.
    
2. Core Java basics(concept of inheritance,interface,exception handling)
    
3. Jdbc basics
    

## What is a Prepared Statement?

It is an interface present in jdbc that provides methods to execute SQL queries with the database. It extends from the Statement interface. Its implementation class is provided by the Database vendors who are using JDBC. It is used to execute parameterized queries (those queries in which we pass the values in query at runTime or dynamically). It is nothing but an advanced version of the Statement interface to solve a particular problem.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676716530169/5edb3956-a5df-4d44-9267-a32257e05a44.jpeg align="center")

## What is needed for a Prepared Statement in Jdbc?

As in the case of the Statement interface, one statement object can be used to compile and execute any no of different queries. But compilation and execution of a query is not a lightweight task as it requires time .and in the real world even if 1 query is taking 3 to 4 milliseconds to compile and execute then it is a very heavy task as there are millions of queries running over a program And for millions of queries million milli seconds required. So, here comes the Prepared Statement to solve the problem. Let's understand it by an example: If the query is the same as the booking of train tickets. Millions of users are using the same query but only station names and dates vary, then there is no need to compile and execute every user's query each time. The query must be compiled only once as it saves millions of milliseconds. Only at the time of Query execution, For each user, different values can be passed at run time. So in these cases, the Prepared Statement Interface comes in handy. Examples where the prepared Statement Interface comes in handy as ticket booking applications of movies, buses, trains, flights hotels, etc where the same queries run multiple times with different parameters.

## Benefits over Statment Interface?

1. Performance of an application is increased many folds.
    
2. Time-saving by reducing compile time of million queries to almost none.
    

`Note: Prepared Statement Object comes to execute only those queries which are the same in nature(like only search or only insert or only delete or only update ) but with different parameters. If you have to execute different queries of different natures then u have to create different Prepared Statement objects. U can't execute different queries of different natures with the same prepared Statement object. If you have to execute different queries of different natures with the same object then you must go with Statement Object. We are emphasizing here on object creations as object creation is also not a light-weight task (one must consider this in mind).`

## Concept of Dynamic Query in Prepared Statement?

The prepared Statement object is used to execute mainly dynamic queries (queries in which we pass the parameter at run time or at the time of execution ).
 ## Methods to execute queries with Prepared Statement object:

1. executeQuery: This method is used by the prepared Statement object while executing any search query. After method execution, it returns data in form of tables which must be kept in an object of the ResultSet Interface of JDBC.
    
2. executeUpdate: This method is used by the prepared Statement object while executing any insert, delete, or update queries. After method execution, it returns data in form of an integer(no of rows affected by the query).
    
3. execute: This method is rarely used by prepared Statement objects. It is used for both operations i.e Search operations or Non-search operations(insert, delete, update). It returns a boolean value. And according to that value, you can use if-else conditions to execute any one of both operations. ##Creating a PreparedStatement Object First, you have to create a connection object of Connection Interface in JDBC and with the Connection object, you have to execute the prepareStatement method and pass the query to be compiled in that method as a parameter in the form of a String.
    

`note: Query compilation will be done at the time of creating preparedStatement object simultaneously.`

```java
//we have created a connection object named con through which we will create //preparedStatement object and the reference for that object will be pstmt.
pstmt=con.prepareStatement(sqlQuery);
```

## Crud Operations through Prepared Statement(Learning through Examples).

I have created a table named generalstore in the MySQL database named juniorg. In that table, we will insert, delete, search, and update items. I will show you one by one how it is done with java and jdbc and how to use prepared Statement.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676720829080/aa58ff51-734b-44e1-b66f-172d3eb26484.png align="center")

I have written a java utility code in which we are creating two methods. One method of work is to establish a connection between our java program and our database by taking the URL, username, and password from a properties file (we keep that data in properties files which we have to update from time to time without re-compiling the source file again and again ). And 2nd method is to close the resources (note: every object created is a resource). So we have to close all the resources before the termination of the program so that the resources won't get wasted or underutilized.

Utility java code:

```java
package in.generalStore.properties;

import java.io.FileInputStream;
import java.io.IOException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Properties;

public class UtilityCodeForConnectionAndResourceCleanUp {
public static Connection getJdbcConnection() throws SQLException,IOException
{
	FileInputStream fis=new FileInputStream("E:\\Java_Programs_Eclipse\\GeneralStorePreparedStatement\\src\\in\\generalStore\\utility\\app.properties");
	Properties properties= new Properties();
	properties.load(fis);
	Connection connection=DriverManager.getConnection(properties.getProperty("url"), properties.getProperty("username"),properties.getProperty("password"));
	return connection;
	
}
public static void CleanUpCodeForResources(Connection connection,Statement statement,ResultSet resultSet)throws SQLException
{
	if (connection!=null) {
		connection.close();
	}
	if (statement!=null) {
		statement.close();
	}
	if (resultSet!=null) {
		resultSet.close();
	}
	
	
}
}
```

Properties file :

```plaintext
url=jdbc:mysql:///juniorg
username=root
password=Lumia@540
```

And i have used MySQL connector with my project as I am working with MySQL database.

## Insertion program

```
package in.generalStore.main;

import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.util.Scanner;

import in.generalStore.properties.UtilityCodeForConnectionAndResourceCleanUp;

public class InsertItemApp {

	public static void main(String[] args) {
		Connection connection=null;
		PreparedStatement pstmt=null;
		Scanner scanner=null;
	Integer noOfRowsInserted=null;
		try {
			connection=UtilityCodeForConnectionAndResourceCleanUp.getJdbcConnection();
		if (connection!=null) {
			String SqlInsertQuery="insert into generalstore(ItemName,ItemPrice,ItemQuantity) values(?,?,?)";
			pstmt=connection.prepareStatement(SqlInsertQuery);	
		}
			if (pstmt!=null) {
				scanner=new Scanner(System.in);
				if (scanner!=null) {
				
					System.out.println("enter the itemName::");
					String itemName=scanner.next();
					System.out.println("enter the itemPrice::");
					int itemPrice=scanner.nextInt();
					System.out.println("enter the itemQuantity::");
					int itemQuantity=scanner.nextInt();
				
				pstmt.setNString(1, itemName);
				pstmt.setInt(2, itemPrice);
				pstmt.setInt(3, itemQuantity);
			}}
			noOfRowsInserted=pstmt.executeUpdate();
			System.out.println("no fo rows inserted is :"+noOfRowsInserted);
			
		}catch (SQLException|IOException e) {
			e.printStackTrace();
		}
		catch (Exception e) {
			e.printStackTrace();
		}finally {
			try {
				UtilityCodeForConnectionAndResourceCleanUp.CleanUpCodeForResources(connection, pstmt, null);
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		scanner.close();
		}

	}

}
```

output:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676722026382/f0d8ed2e-d28a-48fb-891a-e72bc2c2d3f8.png align="center")

here in the above screenshot, u can see that i have inserted five items in the table .

## Select Query

```
package in.generalStore.main;

import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;


import in.generalStore.properties.UtilityCodeForConnectionAndResourceCleanUp;

public class SelectItemApp {

	public static void main(String[] args) {
		Connection connection=null;
		PreparedStatement pstmt=null;
		ResultSet rSet=null;
		try {
			connection=UtilityCodeForConnectionAndResourceCleanUp.getJdbcConnection();
		if (connection!=null) {
			String sqlSelectQuery="select * from generalstore";
			pstmt=connection.prepareStatement(sqlSelectQuery);

		}
		if (pstmt!=null) {
			rSet=pstmt.executeQuery();
			
		}
		if (rSet!=null) {
			System.out.println("ItemId\tItemName\tItemPrice\tItemQuantity");
			while(rSet.next()) {

			System.out.println(rSet.getInt(1)+"\t"+rSet.getString(2)+"\t\t"+rSet.getInt(3)+"\t\t"+rSet.getInt(4));
			}
			
		}
		} catch(SQLException|IOException si) {si.printStackTrace();}
		catch (Exception e) {
			e.printStackTrace();
		}finally {
			try {
				UtilityCodeForConnectionAndResourceCleanUp.CleanUpCodeForResources(connection, pstmt, rSet);
			} catch (SQLException e) {
				e.printStackTrace();
			}
			
		}

	}

}
```

output:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676722224984/23b61c17-f3b7-4e0a-baf6-570cc83b88c1.png align="center")

## Update Query

```

package in.generalStore.main;

import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.util.Scanner;

import in.generalStore.properties.UtilityCodeForConnectionAndResourceCleanUp;

public class UpdateItemApp {

	public static void main(String[] args) {
	Connection connection=null;
	PreparedStatement pstmt=null;
	Integer noOfRowsAffected=null;
	Scanner scanner=null;
	
		try {
			connection=UtilityCodeForConnectionAndResourceCleanUp.getJdbcConnection();
			if (connection!=null) {
				String sqlUpdateQuery="update generalstore set ItemName='CloseUp' where ItemId=?";
				pstmt=connection.prepareStatement(sqlUpdateQuery);
				
			}
			if (pstmt!=null) {
				scanner=new Scanner(System.in);
				if (scanner!=null) {
					System.out.println("enter the id no for which you want to change ItemName::");
					int itemId=scanner.nextInt();
					pstmt.setInt(1, itemId);
				}
				noOfRowsAffected=pstmt.executeUpdate();
				System.out.println("no of rows updated is :"+noOfRowsAffected);
			}
		} catch (SQLException|IOException si) {
			si.printStackTrace();
		}
		catch (Exception e) {
		e.printStackTrace();
		}finally {
			try {
				UtilityCodeForConnectionAndResourceCleanUp.CleanUpCodeForResources(connection, pstmt, null);
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}scanner.close();
		}

	}

}
```

output:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676722374056/7692ea0d-3d06-43b4-a4c7-a5a98e3a11cb.png align="center")

in the above screenshot, u can see that I have updated the 5th item name from ToothPaste to CloseUp.

## Delete Query

```

package in.generalStore.main;

import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.util.Scanner;

import in.generalStore.properties.UtilityCodeForConnectionAndResourceCleanUp;

public class DeleteItemApp {

	public static void main(String[] args) {
		Connection connection=null;
		PreparedStatement pstmt=null;
		Integer noOfRowsAffectedInteger=null;
		Scanner scanner=null;
		try {connection=UtilityCodeForConnectionAndResourceCleanUp.getJdbcConnection();
		if (connection!=null) {
			String sqlDeleteQuery="delete from generalstore where ItemId=?";
			pstmt=connection.prepareStatement(sqlDeleteQuery);
			
		}
		if (pstmt!=null) {
			scanner=new Scanner(System.in);
			if (scanner!=null) {
				System.out.println("enter the id of the record you want to delete from the table:");
				int id=scanner.nextInt();
			pstmt.setInt(1,id);	
			}
			noOfRowsAffectedInteger=pstmt.executeUpdate();
			System.out.println("no of rows deleted is :"+noOfRowsAffectedInteger);
		}
		}
		catch(SQLException|IOException si) 
		{si.printStackTrace();}
		catch (Exception e) {
			e.printStackTrace();
		}finally {
			try {
				UtilityCodeForConnectionAndResourceCleanUp.CleanUpCodeForResources(connection, pstmt, null);
			} catch (SQLException e) {
				e.printStackTrace();
			}scanner.close();
		}

	}

}
```

output:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676722502245/c9d1e979-ad3f-44bc-ae9e-49511254b77d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676722521400/85034538-854c-4d37-a6f7-f52f212d4e84.png align="center")

in the above screenshot, u can see that I have deleted the 5th row and there are only four records in the table named generalstore.

`Note: you must code yourself for a better understanding of this topic otherwise u can't understand it properly.`

`Subscribe to my newsletter to read more such articles and if u think I am doing good work for this community u can sponsor me also. The sponsor link is present in the dashboard of my Hashnode blog`