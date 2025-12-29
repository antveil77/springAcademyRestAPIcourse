# Repositories and Spring Data  

Spring Data works with Spring Boot to make database integration simple. Before we jump in, let’s briefly talk about Spring Data’s architecture.

## Controller-Repository Architecture  

Up until now, our codebase only returns a hard-coded response from the Controller. This setup violates the Separation of Concerns principle by mixing the concerns of a Controller, which is an abstraction of a web interface, with the concerns of reading and writing data to a data store, such as a database. In order to solve this, we’ll use a common software architecture pattern to enforce data management separation via the Repository pattern.

A common architectural framework that divides these layers, typically by function or value, such as business, data, and presentation layers, is called Layered Architecture. In this regard, we can think of our Repository and Controller as two layers in a Layered Architecture. The Controller is in a layer near the Client (as it receives and responds to web requests) while the Repository is in a layer near the data store (as it reads from and writes to the data store).

The Repository is the interface between the application and the database, and provides a common abstraction for any database, making it easier to switch to a different database when needed.

![Spring Initializr](/images/LabSpringInitializr_Image6.png)  

In good news, Spring Data provides a collection of robust data management tools, including implementations of the Repository pattern.

## Choosing a Database  

For our database selection, we’ll use an embedded, in-memory database. “Embedded” simply means that it’s a Java library, so it can be added to the project just like any other dependency. “In-memory” means that it stores data in memory only, as opposed to persisting data in permanent, durable storage. At the same time, our in-memory database is largely compatible with production-grade relational database management systems (RDBMS) like MySQL, SQL Server, and many others. Specifically, it uses JDBC (the standard Java library for database connectivity) and SQL (the standard database query language).


