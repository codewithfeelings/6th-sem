Suggestion of Advanced Java With Web Application

 Group A:- (Marks1)
UNIT – I (M1): Introduction to Java EE
1. Define Java EE.

Java EE is a platform used to develop large-scale enterprise applications.

2. What is an enterprise application?

An enterprise application is a large software system used by organizations to manage business
processes.
3. Expand JDBC.

Java Database Connectivity.

4. Expand JSP.

Java Server Pages.

5. Expand MVC.

Model View Controller.
6. What is a web application?

A web application is a program that runs on a web server and is accessed through a web browser.

7. What is a web container?

A web container manages execution of servlets and JSP pages.

8. What is a deployment descriptor?

Deployment descriptor is an XML configuration file (web.xml) used for configuring web applications.

9. What is the purpose of an application server?

It provides an environment to run enterprise applications.

10. What is a WAR file?

WAR (Web Application Archive) is a packaged web application used for deployment.

11. What is Apache Tomcat?

Apache Tomcat is a web server and servlet container used to run Java web applications.

12. What is a servlet container?

It manages the lifecycle and execution of servlets.

13. What is JNDI?

JNDI stands for Java Naming and Directory Interface.

UNIT – II (M2): JDBC
14. What is JDBC?

JDBC is an API used to connect Java applications with databases.

15. Name any two JDBC drivers.

Type 1 Driver and Type 4 Driver.

16. What is ResultSet?

ResultSet is an object that stores data retrieved from a database query.

17. What is commit?

Commit saves all changes made during a transaction permanently.

18. What is rollback?

Rollback cancels the current transaction and restores the previous state.

19. What is a JDBC driver?

A JDBC driver is software that enables communication between Java and a database.

20. What is Connection object?

Connection represents a session between Java application and database.

21. What is PreparedStatement?

PreparedStatement is a precompiled SQL statement used for faster and secure execution.

22. What is CallableStatement?

CallableStatement is used to execute stored procedures.

23. What is batch processing in JDBC?

Batch processing executes multiple SQL statements together.

24. What is database metadata?

Metadata provides information about database structure.

25. What is DriverManager?

DriverManager manages JDBC drivers and establishes database connections.

26. What is executeQuery()?

executeQuery() is used to execute SELECT queries.

UNIT – III (M3): Java Server Pages (JSP)
27. What is JSP?

JSP is a technology used to create dynamic web pages using Java.

28. What is JSP lifecycle?

JSP lifecycle includes translation, compilation, initialization, execution, and destruction.

29. What is scriptlet?

Scriptlet is a Java code block written inside JSP.

30. What is JSP EL?

JSP Expression Language is used to access data stored in objects.

31. What is JSTL?

JSTL stands for JavaServer Pages Standard Tag Library.

32. What is JSP directive?

JSP directive provides instructions to the JSP container.

33. Name types of JSP directives.

Page, Include, and Taglib directives.

34. What is JSP expression tag?

It is used to display output directly on the webpage.

35. What is page directive?

Page directive defines page-level settings in JSP.

36. What is include directive?

It includes another file during JSP translation phase.

37. What is custom tag?

Custom tag is a user-defined tag used in JSP pages.

38. What is JSP translation phase?

It is the process of converting JSP into a servlet.

UNIT – IV (M4): Servlets
39. What is a Servlet?

Servlet is a Java program used to handle web requests and responses.

40. What is servlet lifecycle?

Servlet lifecycle includes init(), service(), and destroy() methods.

41. What is doGet()?

doGet() handles HTTP GET requests.

42. What is doPost()?

doPost() handles HTTP POST requests.

43. What is cookie?

A cookie is a small piece of data stored in the client browser.

44. What is servlet mapping?

Servlet mapping connects a URL with a servlet.

45. What is init() method?

init() initializes the servlet when it is loaded.

46. What is destroy() method?

destroy() removes the servlet from memory.

47. What is ServletException?

ServletException indicates a servlet-related error.

48. What is HttpSession?

HttpSession is used to maintain user session.

49. What is URL rewriting?

URL rewriting is a technique used for session tracking.

50. What is session tracking?

Session tracking maintains user interaction information.

UNIT – V (M5): JSP and Servlet Integration
51. What is MVC architecture?

MVC is a design pattern that separates application into Model, View, and Controller.

52. What is request forwarding?

Request forwarding sends a request from one resource to another on the server.

53. What is sendRedirect()?

sendRedirect() sends a new request to another URL.

54. What is controller?

Controller manages user requests and controls application flow.

55. What is RequestDispatcher?

RequestDispatcher forwards request to another resource.

56. What is Model in MVC?

Model represents business logic and data.

57. What is View in MVC?

View represents the user interface.

58. What is request scope?

Request scope stores data for a single request.

59. What is response object?

Response object sends response back to the client browser.

UNIT – VI (M6): Hibernate Framework
60. What is Hibernate?

Hibernate is an ORM framework used to simplify database operations in Java.

61. What is ORM?

ORM stands for Object Relational Mapping.

62. What is HQL?

HQL stands for Hibernate Query Language.

63. What is Hibernate Session?

Session is an interface used to interact with the database.

64. What is Hibernate mapping?

Hibernate mapping defines relation between Java class and database table.

65. What is Hibernate configuration file name?

hibernate.cfg.xml

66. What is persistent class?

A persistent class is mapped with a database table.

67. What is lazy loading?

Lazy loading loads data only when it is required.

68. What is Criteria Query?

Criteria Query is used to create database queries programmatically.

69. What is caching in Hibernate?

Caching stores frequently used data to improve performance.

70. What is SessionFactory in Hibernate?

SessionFactory is an object in Hibernate that creates Session objects and manages database
connections. It is created once and used throughout the application.

 Group B :- (Marks 5)

UNIT – I (M1): Introduction to Java EE
1. Explain Java EE Architecture.

Java EE (Java Enterprise Edition) architecture is designed to develop large scale, distributed and secure
enterprise applications. It follows a multi-tier architecture which separates different components of an
application.
The main layers of Java EE architecture are:

  Client Tier:

This layer contains client applications such as web browsers or desktop applications. The client sends
requests to the server.

  Web Tier:

The web tier handles user requests and responses. Technologies used in this layer include Servlets, JSP
and JSF. It processes the request received from the client.

  Business Tier:

This layer contains business logic of the application. Technologies like EJB and Java classes are used to
implement business rules.

  Enterprise Information System (EIS) Tier:

This layer contains databases and other enterprise systems. It stores and manages application data.
Java EE architecture provides scalability, security, and maintainability for enterprise applications.

2. Difference between Java SE and Java EE.
Java SE

Feature

Java EE

Full Form

Purpose

Java Standard Edition

Java Enterprise Edition

Used for standalone applications

Used for enterprise web applications

Components

Core Java libraries

Web and enterprise technologies

Technologies

AWT, Swing, Collections

JSP, Servlets, EJB, JDBC

Application Type

Desktop applications

Distributed web applications

Platform

Base platform for Java

Built on top of Java SE

3. Explain Multi-Tier Architecture in Java EE.

Multi-tier architecture divides an application into multiple layers to improve scalability and
maintainability.

The main tiers are:
Presentation Tier:
This layer interacts with the user. It contains technologies such as HTML, JSP, and Servlets which display
information to the user.
Business Logic Tier:
This layer processes business rules and application logic. It handles operations such as calculations,
validations and transactions.
Data Tier:
This layer manages the database and data storage. It uses JDBC, Hibernate or JPA to interact with
databases.
Advantages of multi-tier architecture:

Improves scalability

•
•  Easy maintenance
•  Better security
•  Separation of concerns

4. Difference between Web Container vs Application Container.

Feature

Web Container

Application Container

Purpose

Manages web components Manages enterprise components

Components Servlets and JSP

EJB, business components

Function

Handles HTTP requests

Handles business logic

Example

Apache Tomcat

Complexity  Simple

JBoss, GlassFish

More complex

UNIT – II (M2): JDBC
5. What is the Role of Class.forName() in JDBC?

Class.forName() is used to load the JDBC driver class dynamically at runtime. When the driver class is
loaded, it registers itself with the DriverManager.
Example:
Class.forName("com.mysql.cj.jdbc.Driver");
Role of Class.forName():

•  Loads JDBC driver into memory
•  Registers driver with DriverManager
•  Enables Java program to connect with database

In modern JDBC versions, driver loading may happen automatically.

6. Difference between Statement and PreparedStatement.

Feature

Statement

Query compilation  Compiled every time

Performance

Slower

PreparedStatement

Precompiled once

Faster

Security

Vulnerable to SQL injection

Prevents SQL injection

Parameters

Does not support parameters

Supports parameters

Usage

Simple queries

Dynamic queries

7. Explain ResultSet and ResultSetMetaData.

ResultSet:
ResultSet is an object used to store the result returned by a SQL query. It represents a table of data
retrieved from the database.
Features:

•  Stores rows returned from SELECT query
•  Allows navigation through records
•  Provides methods like next(), getString(), getInt()

Example:
ResultSet rs = stmt.executeQuery("SELECT * FROM student");
ResultSetMetaData:
ResultSetMetaData provides information about the structure of the ResultSet.
It can give details such as:
•  Number of columns
•  Column names
•  Column data types

Example:

   ResultSetMetaData rsmd = rs.getMetaData();

8. What is Transaction Management in JDBC.

Transaction management ensures that a group of SQL operations are executed as a single unit.
Important methods:
commit():
Saves all changes permanently.
rollback():
Cancels all changes made during the transaction.
Example:
connection.setAutoCommit(false);
Advantages:

•  Maintains data consistency
•  Ensures atomic operations
•  Prevents partial updates

9.What is JDBC Transaction Isolation Levels.

Transaction isolation level determines how transactions interact with each other.
Common levels are:
READ_UNCOMMITTED:
Allows reading uncommitted data.
READ_COMMITTED:
Allows reading only committed data.
REPEATABLE_READ:
Prevents other transactions from modifying the data.
SERIALIZABLE:
Highest level of isolation and prevents concurrency problems.
Higher isolation increases data consistency but reduces performance.

10. What is Connection Timeout and Login Timeout in JDBC?

Connection Timeout:
Connection timeout refers to the maximum amount of time a program waits to obtain a connection
from the database. If the connection is not established within the specified time limit, the system
throws an exception and stops waiting.
Purpose:

•  Prevents the application from waiting forever for a connection.
•  Helps handle slow or unavailable database servers.
•

Improves application reliability.

Example (conceptual):
dataSource.setLoginTimeout(30);
This means the program will wait 30 seconds to establish the connection.
Login Timeout:
Login timeout is the maximum time allowed for the JDBC driver to establish a database login
connection. If the login process takes longer than the specified time, the connection attempt fails.
Purpose:

•  Controls the time taken for authentication with the database.
•  Prevents long delays during database login.

UNIT – III (M3): JSP
11. Define JSP Implicit Objects.

JSP provides several built-in objects automatically available in JSP pages. These are called implicit
objects.
Common implicit objects:

Object

request

Description

Contains client request information

response

Sends response to client

session

Stores user session data

application

Shared data across application

out

config

Used to print output

Servlet configuration

pageContext  Provides access to page attributes

These objects simplify JSP development.

12. Define JSP Action Elements.

JSP action elements are special XML tags used to control the behavior of the JSP engine.
Common JSP actions:

Action

Purpose

<jsp:include>

Includes another resource

<jsp:forward>

Forwards request to another page

<jsp:param>

Passes parameters

<jsp:useBean>

Creates JavaBean object

<jsp:setProperty>  Sets bean property

These tags help reuse components and simplify page development.

13. Define JavaBeans in JSP.

JavaBeans are reusable Java classes used to store and manage data.
Characteristics:

•  Private variables
•  Public getter and setter methods
•  Default constructor

In JSP, JavaBeans help separate business logic from presentation logic.
Example:
<jsp:useBean id="student" class="com.StudentBean" />
Advantages:

•  Code reusability
•  Better code organization
•  Easy maintenance

14. Define JSP Expression Language (EL).

Expression Language (EL) is used to simplify access to application data in JSP.
Syntax:
${expression}
Example:
${student.name}
Advantages:

•  Reduces Java code in JSP
•  Easy access to attributes
Improves readability
•

15. What is the Use of <jsp:forward> and <jsp:param>.

<jsp:forward>
This tag forwards the request from one JSP page to another resource.
Example:
<jsp:forward page="result.jsp"/>
<jsp:param>
It is used to pass parameters during forwarding.
Example:
<jsp:param name="id" value="101"/>
Both are useful for transferring control between pages.

16. Define JSP Configuration using web.xml.

The web.xml file is the deployment descriptor of a Java web application.
It is used to configure:

•  Servlets
•  JSP pages
•  Session settings
•  Security constraints

Example configuration:
<welcome-file-list>
<welcome-file>index.jsp</welcome-file>
</welcome-file-list>
web.xml helps manage application configuration centrally.

17. Define Internationalization (i18n) in JSP.

Internationalization allows web applications to support multiple languages and regions.
JSP supports i18n using:
•  Resource bundles
•  Locale settings

Example:
ResourceBundle bundle = ResourceBundle.getBundle("messages", locale);
Benefits:

•  Supports multiple languages
•

Improves user experience globally

UNIT – IV (M4): Servlets
18. Difference between GenericServlet and HttpServlet.

Feature

Package

GenericServlet

javax.servlet

HttpServlet

javax.servlet.http

Protocol Support Protocol independent

HTTP protocol specific

Methods

service() method

doGet(), doPost(), doPut(), doDelete()

Usage

Used for general protocol handling Used for web applications

Inheritance

Base class for all servlets
19. Explain HttpServletRequest and HttpServletResponse.

Extends GenericServlet

HttpServletRequest:
HttpServletRequest is an interface that contains methods to get information from the client request.
Important functions:

•  Get request parameters
•  Get client information
•  Retrieve cookies and session data

Example methods:

•  getParameter()
•  getHeader()
•  getSession()

HttpServletResponse:
HttpServletResponse is used to send response from server to client.
Functions:

•  Send HTML response
•  Set response headers
•  Manage cookies

Example methods:

•  sendRedirect()
•  setContentType()
•  addCookie()

20. Explain ServletConfig and ServletContext.

ServletConfig:
ServletConfig is used to pass initialization parameters to a servlet.
Features:

•  Specific to one servlet

•  Used during servlet initialization
•  Parameters defined in web.xml

Example method:
getInitParameter()
ServletContext:
ServletContext is an object shared by all servlets in an application.
Features:

•  Represents the whole web application
•  Allows sharing data between servlets
•  Created once when application starts

Example method:
getAttribute()
Thus ServletConfig is servlet-specific, while ServletContext is application-wide.

21. Explain Servlet Filters.

Servlet filters are Java classes used to intercept requests and responses before they reach the servlet.
They perform tasks such as:
•  Logging requests
•  Authentication and authorization
•  Data compression
Input validation
•
Filters work in three stages:

1.  Request filtering before servlet execution
2.  Processing by servlet
3.  Response filtering before sending to client

Filters improve security and performance of web applications.

22. Explain Servlet Deployment in Tomcat Server.

Servlet deployment means placing and configuring servlets so that they can run on a server.
Steps to deploy servlet in Tomcat:

1.  Install Apache Tomcat server.
2.  Create a web application folder inside the webapps directory.
3.  Place compiled servlet class inside WEB-INF/classes.
4.  Configure servlet mapping in web.xml file.
5.  Start the Tomcat server.
6.  Access the servlet through a browser using URL.

Example URL:
http://localhost:8080/appname/servletname
Tomcat loads the servlet and executes it when the request is received.

UNIT – V (M5): JSP and Servlet Integration
23. Explain Request–Response Flow in MVC using JSP and Servlet.

MVC (Model View Controller) architecture separates application logic into three parts.
Client Request:
The user sends a request from the browser.
Controller (Servlet):
The servlet acts as the controller. It receives the request and processes it.

Model:
The controller interacts with the model (Java classes, database, business logic).
View (JSP):
After processing, the servlet forwards the result to JSP page which displays the output to the user.
Thus MVC separates presentation, logic and data for better maintainability.

24. What is the Role of Servlet in MVC.

In MVC architecture, the servlet acts as the controller.
Responsibilities of servlet:

•  Receive client requests
•  Process input data
•  Call business logic in model
•  Decide which JSP page to display
•  Forward request to view

Example:
RequestDispatcher rd = request.getRequestDispatcher("result.jsp");
rd.forward(request, response);
Thus servlet controls the application workflow.

25. What is the Role of JSP in MVC?

In MVC architecture, JSP acts as the view component.
Responsibilities of JSP:

•  Display data to the user
•  Generate dynamic web pages
•  Access model data using EL or JSTL
•  Format the output

Advantages:

•  Separates presentation from business logic
•  Simplifies UI development
Improves maintainability
•

JSP should only contain presentation logic.

26. Difference between forward() and sendRedirect().

Feature

Location

forward()

Server-side

sendRedirect()

Client-side

Request object Same request used

New request created

URL change

URL does not change

URL changes

Performance  Faster

Slower

Method

RequestDispatcher.forward() response.sendRedirect()

UNIT – VI (M6): Hibernate Framework
27. What is the Advantages of Hibernate over JDBC.

Hibernate is an ORM framework that simplifies database operations.
Advantages:

   Reduces boilerplate code – No need to write large JDBC code.

Automatic table mapping – Maps Java classes with database tables.
Database independence – Works with multiple databases.

Caching support – Improves performance.
Object-oriented query language (HQL) – Easier to write queries.
Therefore Hibernate makes database operations easier and more efficient.

28. Explain Hibernate Configuration Files.

Hibernate configuration file contains database and framework settings.
Main configuration file:
hibernate.cfg.xml
This file contains:

•  Database connection details
•  Driver class name
•  Username and password
•  Hibernate dialect
•  Mapping file configuration

Example:
<property name="connection.url">
jdbc:mysql://localhost:3306/test
</property>
This configuration helps Hibernate connect with the database.

29. Difference between XML Configuration and Annotation Configuration.

Feature

XML Configuration

Annotation Configuration

Configuration Location XML files

Mapping

hbm.xml files

Java classes

Annotations

Code readability

Separate configuration Embedded in code

Maintenance

Harder to maintain

Easier

Modern usage

Less common

More commonly used

      Annotations simplify configuration by directly mapping classes and tables.

30. Explain Hibernate Session and SessionFactory.

SessionFactory:
SessionFactory is responsible for creating Session objects.
It is created once during application startup and shared across the application.
Features:

•  Heavyweight object
•  Thread-safe
•  Created once per database

Session:
Session represents a connection between application and database.
Functions:

•  Save objects
•  Update recordss
•  Delete data
•  Execute queries

Example:
Session session = sessionFactory.openSession();
Session is lightweight and created whenever database operations are required.

 Group C:- (Marks10)

UNIT – I (M1): Introduction to Java EE
Q1. Discuss Advantages and Limitations of Java EE Technology.
✅ Advantages of Java EE Technology
1. 🔷 Platform Independence
One of Java EE’s core strengths is its platform independence, which ensures that applications written
once can be deployed across any system that supports the Java Virtual Machine (JVM).
2. 🔷 Vendor Independence
Java EE is a set of standard specifications, thus it is truly vendor-independent, as several implementations
exist for a specification. This means developers are not locked into a single vendor’s product or tools.
3. 🔷 Scalability
Java EE is specifically engineered to support high-demand environments, which makes it exceptionally
well-suited for developing enterprise applications that need to manage a large number of users and
handle significant transaction volumes efficiently.
4. 🔷 Built-in Security Framework
With its comprehensive security framework, Java EE helps protect applications from threats and
vulnerabilities by providing built-in mechanisms for secure communication, authentication, authorization,
and data encryption.
5. 🔷 Enterprise-Class Capabilities
Java EE provides a comprehensive set of features and APIs specifically designed for building large-scale,
enterprise-level applications.
6. 🔷 Rich API and Integration Support
Java EE excels in its ability to integrate with a multitude of external systems, which is critical for enterprise
applications that often need to interact with various databases, messaging systems, and external web
services.
7. 🔷 Multi-Tier Architecture
Java EE is a multi-tier application — this helps the application be more robust and more secure. The client
tier is where user interaction happens.
8. 🔷 Abstracted Software Architecture
Java EE as a framework represents both an abstraction notion of a software architecture as well as a
description of development artefacts, making the effort for transcribing between design and
implementation much less than that of competing application architecture frameworks.
❌ Limitations of Java EE Technology
1. 🔶 Complexity
Java EE has a complex application development environment and tools can be difficult to use. This steep
learning curve can slow down adoption, especially for beginners or small teams.
2. 🔶 High Cost
Java EE may cost more to build, deploy, and manage applications. Large-scale enterprise deployments
require expensive application servers and skilled personnel.

3. 🔶 Refactoring Challenges
The Java EE specification is a robust one, and as such, if your application grows in complexity, you might
end up refactoring most of the application code to meet ever-changing requirements.
4. 🔶 Not Suitable for Small Projects
Java EE is difficult to use for quick-turnaround, low-cost, and mass-market projects. It is over-engineered
for simple, lightweight applications.
5. 🔶 JSF Design Concerns
JSF, in many opinions, is flawed because it tries to abstract away HTML, CSS, and HTTP — exactly the
reverse of what modern web frameworks do. JSF, like ASP.net, attempts to create statefulness on top of
the stateless protocol HTTP and ends up causing a whole host of problems involving shared server-side
state.
6. 🔶 Limited Graphical UI Support
Java Swing environment’s ability to build graphical user interfaces has limitations, making it less
competitive compared to modern front-end technologies.

Q2. What is the Role of JDBC, JSP, and Servlets in Java EE Applications.
🟠 a) Role of JDBC (Java Database Connectivity)
Definition:
JDBC is a Java API that provides a standard interface for connecting to relational databases and executing
SQL queries.
Role in Java EE:
JDBC is a core part of the Java platform and is included in the standard JDK distribution. The purpose of
JDBC is to connect the database and manipulate the data in the database from a Servlet page or from a
JSP page.
Data Access Layer:
JDBC is part of the data access layer in a web application. It is responsible for connecting to a database,
executing SQL queries, and managing interactions with the database.
CRUD Operations:
JDBC is used for database access in Java applications. It allows developers to interact with databases,
perform CRUD (Create, Read, Update, Delete) operations, and retrieve results.
Implementation Steps:
JDBC involves writing Java code to connect to a database, create PreparedStatement or Statement
objects, execute SQL queries, and process results. It often requires managing connections, transactions,
and exception handling.
Integration with Servlets and JSP:
JSPs and HTTP servlets can access all services and APIs available in Java EE. These services include EJBs,
database connections by way of Java Database Connectivity (JDBC), Java Messaging Service (JMS), XML,
and more.
🟢 b) Role of JSP (JavaServer Pages)
Definition:
JavaServer Pages (JSPs) are a Sun Microsystems specification for combining Java with HTML to provide
dynamic content for Web pages.

Role in Java EE:
JSP is a technology for building dynamic web pages. It allows developers to embed Java code directly into
HTML pages, making it easier to create dynamic content. JSP is primarily used for the presentation layer
of a web application, and it is often used to generate HTML or other markup language content
dynamically.
Relationship with Servlets:
JSP complements servlets by allowing developers to embed Java code directly into HTML pages for
generating dynamic web content. This pairing forms the backbone of Java EE’s web application model,
facilitating the rapid development of interactive, server-rendered web interfaces.
Advantage over Servlets:
When you create dynamic content, JSPs are more convenient to write than HTTP servlets because they
allow you to embed Java code directly into your HTML pages, in contrast with HTTP servlets, in which you
embed HTML inside Java code.
JSP Processing:
Using the JSP compiler, the server converts the JSP into a servlet class that implements the
javax.servlet.jsp.JspPage interface.
Portability:
Because JSPs are part of the Java EE standard, you can deploy JSPs on a variety of platforms. In addition,
third-party vendors and application developers can provide JavaBean components and define custom JSP
tags that can be referenced from a JSP page to provide dynamic content.
🔵 c) Role of Servlets
Java Servlet technology and JavaServer Pages (JSP pages) are server-side technologies that have
dominated the server-side Java technology market; they’ve become the standard way to develop
commercial web applications. Java developers love these technologies for myriad reasons, including: the
technologies are fairly easy to learn, and they bring the Write Once, Run Anywhere paradigm to web
applications.
Definition:
Servlets are Java classes that handle HTTP requests and responses. They provide a server-side processing
model and are part of the Java EE (Enterprise Edition) or Jakarta EE specification.
Role in Java EE:
Servlets are powerful Java components that manage requests and responses in a web application. They
operate on the server side, handling incoming requests, processing them, and generating responses,
often dynamically creating HTML or other content types.
Servlets are responsible for handling the business logic, processing user input, interacting with databases,
and generating dynamic content for web applications.
In MVC Architecture:
Servlets can be part of both the presentation and business logic layers. They handle requests, process
data, and often act as controllers in a Model-View-Controller (MVC) architecture.
Request Handling:
When a client sends a request to the server, the server sends the request to the servlet. The servlet then
constructs a response that the server sends back to the client. Unlike CGI scripts, however, servlets run
within the same process as the HTTP server.

UNIT – II (M2): JDBC
Q3. Explain JDBC drivers and architecture with diagram. Types of JDBC driver.
(A) What is a JDBC Driver?
A JDBC driver is a software component (usually a .jar) that implements JDBC interfaces and knows how
to talk to a specific database (MySQL, Oracle, PostgreSQL, etc.). It converts your Java JDBC calls into the
database’s network/protocol calls.
(B) JDBC Architecture (Core Idea)
At a high level, JDBC separates your program from database-specific details:

•  Your program uses standard JDBC API (java.sql, javax.sql)
•  A DriverManager or DataSource finds/creates a connection
•  The driver handles actual DB communication

Architecture diagram (common view)

DriverManager role (important for exams):
When you call DriverManager.getConnection(url, user, pass), the DriverManager tries to select an
appropriate driver from registered JDBC drivers and uses it to connect.
DataSource (modern/enterprise preferred):
DataSource is the preferred way to get connections (commonly via JNDI in servers) and supports features
like connection pooling and distributed transactions depending on implementation.
(C) Types of JDBC Drivers (Type 1, 2, 3, 4) + diagrams
The JDBC specification commonly classifies drivers into four categories:
Type 1: JDBC–ODBC Bridge
How it works: JDBC → ODBC → Database
Needs: ODBC driver + often native libraries (less portable). Example mentioned in standard discussions:
JDBC-ODBC bridge.
Java App -> JDBC API -> Type 1 Driver (Bridge) -> ODBC Driver -> Database
Note (common practical point): Oracle’s old JDBC-ODBC Bridge (sun.jdbc.odbc.JdbcOdbcDriver) was
removed from Java 8 (so it’s obsolete in modern Java).

Type 2: Native-API / Partly Java Driver
How it works: JDBC calls go to native DB client libraries (vendor-specific).
Tradeoff: faster than bridge sometimes, but platform-dependent (needs native libs).
Java App -> JDBC API -> Type 2 Driver (part Java + native) -> Native DB API -> Database
Concrete example (Oracle naming): Oracle describes an OCI driver as a Type 2 client driver (requires
OCI/platform-specific libraries).
Type 3: Network Protocol / Middleware Driver
How it works: Pure Java client talks to a middleware server using a DB-independent protocol;
middleware talks to DB.
Java App -> JDBC API -> Type 3 Driver -> Middleware Server -> Database
Use case: When you want a middle layer for routing, security, logging, or connecting to multiple DB types
through one middle tier.
Type 4: Thin / Pure Java Direct-to-Database Driver (Most common today)
How it works: Pure Java driver implements the database’s native wire protocol and connects directly.
Java App -> JDBC API -> Type 4 Driver (pure Java) -> Database
Concrete example (Oracle): Oracle recommends using the JDBC Thin driver (a Type 4 client driver) in most
client-side applications for portability/performance.

Q4. Write Steps to connect Java application with database using JDBC.
Below is the standard step flow used in most JDBC programs. The Oracle JDBC tutorial also highlights that
applications can connect via DriverManager (simpler) or DataSource (preferred in many cases).
Steps (DriverManager approach)
1.  Add JDBC driver JAR to classpath

o  Example: MySQL Connector/J, PostgreSQL driver, Oracle JDBC driver, etc.

2.  Import JDBC packages

o

import java.sql.*;

3.  (Optional in modern Java) Load/Register the driver

o

In JDBC 4.0+, drivers can be auto-loaded when present on the classpath (DriverManager
uses the service provider mechanism).

o  Older style (still seen in labs): Class.forName("com.mysql.cj.jdbc.Driver");

4.  Create connection

o  Call DriverManager.getConnection(url, user, password); DriverManager selects a suitable

registered driver.

5.  Create Statement / PreparedStatement
o  Statement for simple SQL
o  PreparedStatement for parameterized SQL (recommended)
o  CallableStatement for stored procedures

6.  Execute SQL

o  executeQuery() for SELECT
o  executeUpdate() for INSERT/UPDATE/DELETE (returns number of rows affected)

7.  Process ResultSet (for SELECT)

o  Use rs.next() and getters like getString(), getInt(), etc.

8.  Close resources

o  Close ResultSet, Statement, Connection (or use try-with-resources).

Sample connection code (compact, good for exam)
import java.sql.*;

public class DbConnectDemo {
    public static void main(String[] args) {
        String url = "jdbc:postgresql://localhost:5432/testdb";
        String user = "test";
        String pass = "test123";

        String sql = "SELECT id, name FROM student";

        try (Connection con = DriverManager.getConnection(url, user, pass);
             PreparedStatement ps = con.prepareStatement(sql);
             ResultSet rs = ps.executeQuery()) {

            while (rs.next()) {
                System.out.println(rs.getInt("id") + " " + rs.getString("name"));
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}

Output

JDBC call
executeUpdate()  row count (int)
executeQuery()
executeUpdate()  row count (int)
executeUpdate()  row count (int)

Q5. Explain CRUD operations using JDBC.
CRUD = Create, Read, Update, Delete — implemented using SQL + JDBC objects (Connection,
PreparedStatement, ResultSet).
(A) CRUD mapping table (very exam-friendly)
SQL command
CRUD
INSERT
Create
Read
SELECT
Update  UPDATE
Delete  DELETE
Oracle’s JDBC basics explicitly states executeQuery() returns a ResultSet, and executeUpdate() is used for
INSERT/DELETE/UPDATE and returns affected row count.
(B) Example CRUD code using PreparedStatement
Assume a table: student(id INT PRIMARY KEY, name VARCHAR(50), marks INT)
1) CREATE (INSERT)
String sql = "INSERT INTO student (id, name, marks) VALUES (?, ?, ?)";
try (Connection con = DriverManager.getConnection(url, user, pass);
     PreparedStatement ps = con.prepareStatement(sql)) {

ResultSet

    ps.setInt(1, 101);
    ps.setString(2, "Asha");

    ps.setInt(3, 88);

    int rows = ps.executeUpdate();   // INSERT => executeUpdate
    System.out.println("Inserted rows: " + rows);
}
executeUpdate() is the standard method for INSERT/UPDATE/DELETE.
2) READ (SELECT)
String sql = "SELECT id, name, marks FROM student WHERE id = ?";
try (Connection con = DriverManager.getConnection(url, user, pass);
     PreparedStatement ps = con.prepareStatement(sql)) {

    ps.setInt(1, 101);

    try (ResultSet rs = ps.executeQuery()) {  // SELECT => executeQuery
        if (rs.next()) {
            System.out.println(rs.getInt("id"));
            System.out.println(rs.getString("name"));
            System.out.println(rs.getInt("marks"));
        }
    }
}
executeQuery() returns a ResultSet, and you iterate using rs.next().
3) UPDATE
String sql = "UPDATE student SET marks = ? WHERE id = ?";
try (Connection con = DriverManager.getConnection(url, user, pass);
     PreparedStatement ps = con.prepareStatement(sql)) {

    ps.setInt(1, 95);
    ps.setInt(2, 101);

    int rows = ps.executeUpdate();
    System.out.println("Updated rows: " + rows);
}
Again, UPDATE uses executeUpdate() and gives affected row count.
4) DELETE
String sql = "DELETE FROM student WHERE id = ?";
try (Connection con = DriverManager.getConnection(url, user, pass);
     PreparedStatement ps = con.prepareStatement(sql)) {

    ps.setInt(1, 101);

    int rows = ps.executeUpdate();
    System.out.println("Deleted rows: " + rows);
}
DELETE uses executeUpdate().

Q6. Explain Commit, rollback, and savepoint in JDBC with examples.
1) Transaction + Auto-commit (important base point)
In JDBC, transactions matter only when auto-commit is OFF.

•  By default, when a Connection is created it is in auto-commit mode, meaning each SQL statement
is treated as its own transaction and is committed automatically after the statement completes.

•  To group multiple SQL statements into one logical unit of work, you must disable auto-commit:

con.setAutoCommit(false);

2) commit() (make changes permanent)
Meaning
Connection.commit() makes permanent all changes done since the last commit() or rollback() and
releases database locks held by that connection. It should be used only when auto-commit is disabled.
When used
Use commit() when all SQL statements in your transaction succeed and you want to permanently save
them.
3) rollback() (undo changes)
Meaning
Connection.rollback() undoes all changes in the current transaction (since the last commit/rollback) and
releases locks. It should be used only when auto-commit is disabled.
When used
Use rollback() when: - any SQL statement fails (exception happens), or - your business rule fails (example:
insufficient balance, invalid input, etc.)
Oracle’s JDBC tutorial also describes rollback as aborting a transaction and restoring values to what they
were before the attempted update.
4) Savepoint (partial rollback inside a transaction)
Meaning
A savepoint is a marker inside a transaction. You can roll back only part of the transaction back to that
marker instead of rolling back everything.
In JDBC: - Create: Savepoint sp = con.setSavepoint(); or con.setSavepoint("S1") - Roll back partially:
con.rollback(sp); (undoes changes made after the savepoint) - Optional cleanup:
con.releaseSavepoint(sp);
Key rules/behavior: - Auto-commit must be OFF to use savepoints (otherwise JDBC throws an exception).
- Savepoints become invalid after commit or full rollback, and rolling back to a savepoint can invalidate
savepoints created after it.
Example : Commit & Rollback & savepoint (money transfer scenario)
import java.sql.*;

public class TransactionDemo {
    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");

            Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/test", "root", "1234");

            con.setAutoCommit(false);
            Statement st = con.createStatement();
            st.executeUpdate("insert into student values(1,'Ram')");
            Savepoint sp = con.setSavepoint("FirstPoint");
            st.executeUpdate("update student set name='Shyam' where id=1");
            con.rollback(sp);
            con.commit();
            System.out.println("Transaction completed successfully");
            con.close();

        } catch (Exception e) {
            System.out.println(e);
        }
    }
}

UNIT – III: Java Server Pages (JSP)
Q7. Explain JSP Lifecycle with Diagram.
📌 Definition
A JSP life cycle is defined as the process from its creation till the destruction. This is similar to a servlet life
cycle with an additional step which is required to compile a JSP into a servlet.
📝 Phases of JSP Lifecycle
JSP passes through the following phases: 1. Translation of JSP page 2. Compilation of JSP page 3. Class
loading 4. Instantiation 5. Initialization 6. Request Processing 7. Destruction
➤ Phase 1: Translation
The JSP file is parsed and converted into a Java servlet source file (test.java). This step checks for syntax
correctness.
In the translation phase, container validates the syntactic correctness of JSP page and tag files.
➤ Phase 2: Compilation
The generated test.java file is compiled into a class file (test.class). This step converts the servlet code into
bytecode.
➤ Phase 3: Class Loading
The java servlet class that was compiled from the JSP source is loaded into the container. In the execution
phase, the container manages one or more instances of this class in response to requests and other
events.
➤ Phase 4: Instantiation
As we compile the servlet, the object of the generated servlet is created. This process takes place after
the class file is loaded in the memory. As soon as the instantiation takes place, the objects: ServletConfig
and ServletContext get accessible to the JSP class.
➤ Phase 5: Initialization (jspInit())
After instantiation, container invokes jspInit() method, better known as initialization of JSP. It basically
initializes the instance we created. It is done to initialize resources needed to process the request —
resources like databases, allow JSP pages to read data, create lookup tables, and manage network
connections.

➤ Phase 6: Request Processing (_jspService())
Whenever a browser requests a JSP and the page has been loaded and initialized, the JSP engine invokes
the _jspService() method in the JSP. The _jspService() method takes an HttpServletRequest and an
HttpServletResponse as its parameters.
➤ Phase 7: Destruction (jspDestroy())
The destruction phase of the JSP life cycle represents when a JSP is being removed from use by a
container. The jspDestroy() method is the JSP equivalent of the destroy method for servlets. Override
jspDestroy when you need to perform any cleanup, such as releasing database connections or closing
open files.
📊 JSP Lifecycle Diagram

Q8. Explain JSP Syntax and Directives in details.
📌 JSP Syntax Overview
JSP syntax includes: directives, which convey information regarding the JSP page as a whole; scripting
elements, which are Java coding elements such as declarations, expressions, scriptlets, and comments;
objects and scopes.
A) Scripting Elements
1️⃣ Scriptlet Tag <% ... %>
Scripting elements in JSP must be written within the <% %> tags.
Example:
<%
  int count = 10;
  out.println("Count is: " + count);
%>
2️⃣ Declaration Tag <%! ... %>
As the name suggests, the declaration tag is used to declare methods and variables you will use in your
Java code within a JSP file.

Example:
<%!
  int x = 10;
  String greet() { return "Hello!"; }
%>
3️⃣ Expression Tag <%= ... %>
A JSP expression element contains a scripting language expression that is evaluated, converted to a String,
and inserted where the expression appears.
Example:
<p>Today's Date: <%= new java.util.Date() %></p>
4️⃣ Comments <%-- ... --%>
Comments are marked as text or statements that are ignored by the JSP container.
Example:
<%-- This is a JSP comment, not visible in browser source --%>
B) JSP Directives
In JSP, directives are described with a pair of <%@ .... %> tags.
General Syntax:
<%@ directive_name attribute="value" %>
There are three different JSP directives available.
1️⃣ Page Directive
JSP page directive is used to define the properties applying to the JSP page, such as the size of the
allocated buffer, imported packages and classes/interfaces, defining what type of page it is, etc.
Syntax:
<%@ page attribute="value" %>
Example:
<%@ page import="java.util.Date" contentType="text/html" errorPage="error.jsp" %>
2️⃣ Include Directive
The include directive is used to include a file during the translation phase. This directive tells the
container to merge the content of other external files with the current JSP during the translation phase.
Syntax:
<%@ include file="relative_url" %>
Example:
<%@ include file="header.html" %>
<%@ include file="footer.jsp" %>
3️⃣ Taglib Directive
The taglib directive declares that your JSP page uses a set of custom tags, identifies the location of the
library, and provides means for identifying the custom tags in your JSP page.
Syntax:
<%@ taglib uri="library_url" prefix="prefix_name" %>
Example:
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>

C) JSP Actions
JSP actions use constructs in XML syntax to control the behavior of the servlet engine. You can
dynamically insert a file, reuse JavaBeans components, forward the user to another page, or generate
HTML for the Java plugin.
Syntax:
<jsp:action_name attribute="value" />
Common JSP Actions:
Action
<jsp:include>
<jsp:forward>
<jsp:useBean>
<jsp:setProperty>  Set JavaBean property
<jsp:getProperty>  Get JavaBean property
<jsp:param>

Description
Include a file at request time
Forward request to another page
Use or create a JavaBean

Pass parameters

Q9. Explain JSTL Core Tags with Examples.
📌 What is JSTL?
The JavaServer Pages Standard Tag Library (JSTL) is a collection of useful JSP tags which encapsulates the
core functionality common to many JSP applications.
📦 JSTL Core Tags in Detail
1️⃣ <c:out> – Output Tag
The <c:out> tag is used for displaying the content on client after escaping XML and HTML markup tags.
Main attributes are default and escapeXML.
Example:
<c:out value="${username}" default="Guest"/>
2️⃣ <c:set> – Set Variable
The <c:set> tag is useful for setting up a variable value in a specified scope. It basically evaluates an
expression and sets the result in the given variable.
Example:
<c:set var="city" value="Mumbai" scope="session"/>
<c:out value="${city}"/>
3️⃣ <c:remove> – Remove Variable
The <c:remove> tag is used for removing the specified variable from a particular scope. This action can be
used for ensuring that a JSP can also clean up any scope resources.
Example:
<c:remove var="city" scope="session"/>
4️⃣ <c:if> – Conditional Tag
The <c:if> tag is used to include the conditional statement in the Java Server Pages. Body content is
evaluated only when the condition evaluates to true.
Example:
<c:set var="age" value="20"/>
<c:if test="${age >= 18}">

   <p>Eligible to Vote</p>
</c:if>
5️⃣ <c:choose>, <c:when>, <c:otherwise> – Multiple Conditions
The <c:choose> tag is a conditional tag that establishes a context for mutually exclusive conditional
operations. It works like a Java switch statement in which we choose between a number of alternatives.
Example:
<c:set var="score" value="75"/>
<c:choose>
   <c:when test="${score >= 90}">Grade: A</c:when>
   <c:when test="${score >= 70}">Grade: B</c:when>
   <c:otherwise>Grade: C</c:otherwise>
</c:choose>
6️⃣ <c:forEach> – Iteration Tag
The <c:forEach> is an iteration tag used for repeating the nested body content for a fixed number of times
or over a collection.
Example 1 – Fixed Iterations:
<c:forEach var="i" begin="1" end="5">
   <p>Item: ${i}</p>
</c:forEach>
Example 2 – Loop over List:
<c:forEach var="fruit" items="${fruitList}">
   <p>${fruit}</p>
</c:forEach>
7️⃣ <c:forTokens> – Token-based Iteration
The <c:forTokens> tag is used for iteration but it only works with a delimiter.
Example:
<c:forTokens items="Apple,Mango,Orange" delims="," var="fruit">
   <p>${fruit}</p>
</c:forTokens>
8️⃣ <c:catch> – Exception Handling
JSTL core tag library contains tags for performing basic operations such as printing values, variables
declaration, exception handling, performing iterations, and declaring conditional statements among
others.
Example:
<c:catch var="err">
   <%  int x = 10/0; %>
</c:catch>
<c:if test="${err != null}">
   Error: ${err.message}
</c:if>
9️⃣ <c:redirect> – Redirect Tag
The <c:redirect> tag is used for redirecting the current page to another URL; provide the relative address
in the URL attribute of this tag and the page will be redirected to the URL.
Example:

<c:redirect url="home.jsp"/>
🔟 <c:url> – URL Formatting
The <c:url> tag is used for URL formatting or URL encoding. It converts a relative URL into an application
context’s URL.
Example:
<c:url value="/login" var="loginUrl"/>
<a href="${loginUrl}">Login</a>

Q10. Explain Custom Tag Library in JSP.
📌 What are Custom Tags?
Custom tags are user-defined action tags that can be used within Java Server Pages. A tag handler is
associated with each tag to implement the operations.
🔧 Step 1: Create the Tag Handler Class
Example – Tag Handler Class:
package com.example;
import javax.servlet.jsp.*;
import javax.servlet.jsp.tagext.*;
import java.io.*;

public class HelloTag extends SimpleTagSupport {
    public void doTag() throws JspException, IOException {
        JspWriter out = getJspContext().getOut();
        out.println("Hello from Custom Tag!");
    }
}
🗂️ Step 2: Create the TLD File
The TLD is a file saved with a .tld extension that contains a set of related tags mapped to their respective
tag handlers along with their description such as the name of the tag, attributes of the tag, etc.
Example – custom.tld:
<?xml version="1.0" encoding="UTF-8"?>
<taglib>
  <tlib-version>1.0</tlib-version>
  <jsp-version>2.0</jsp-version>
  <short-name>My Custom Tags</short-name>
  <tag>
    <name>Hello</name>
    <tag-class>com.example.HelloTag</tag-class>
    <body-content>empty</body-content>
  </tag>
</taglib>
📄 Step 3: Use Custom Tag in JSP Page
To use a custom tag library from a JSP page, reference its tag library descriptor with a <%@ taglib %>
directive.

Custom tag is called like this: <prefix:tagName/>. For example, if our prefix is myprefix and tag name is
MyMsg, we call it as <myprefix:MyMsg/> in the JSP page.
Example – index.jsp:
<%@ taglib prefix="ex" uri="WEB-INF/custom.tld" %>
<html>
<body>
    <ex:Hello/>
</body>
</html>
Output: Hello from Custom Tag!
🏷️ Custom Tag with Attributes
To accept an attribute value, a custom tag class needs to implement the setter methods, identical to the
JavaBean setter methods.
Tag Handler with Attribute:
public class HelloTag extends SimpleTagSupport {
    private String message;

    public void setMessage(String msg) {
        this.message = msg;
    }

    public void doTag() throws JspException, IOException {
        JspWriter out = getJspContext().getOut();
        out.println("Message: " + message);
    }
}
TLD with Attribute:
<tag>
  <name>Hello</name>
  <tag-class>com.example.HelloTag</tag-class>
  <body-content>empty</body-content>
  <attribute>
    <name>message</name>
    <required>true</required>
  </attribute>
</tag>
JSP Usage:
<ex:Hello message="Welcome to JSP Custom Tags!"/>

UNIT – IV: Servlets
Q11. Explain servlet lifecycle & servlet methods with diagram.
Servlet lifecycle (what it means)
A servlet container (Tomcat/Jetty/GlassFish etc.) “owns” servlet objects and manages them through a
well-defined lifecycle exposed by the Servlet interface methods init(), service(), and destroy().

(A)Lifecycle steps (with key points):
1) Loading and instantiation

•  When the app starts (if configured as load-on-startup) or on the first request, the container loads

the servlet class and creates one servlet instance per servlet declaration (typical case).

2) Initialization — init(ServletConfig) / init()

•  Container calls init(...) exactly once for that instance to let it allocate resources (DB connections,

thread pools, caches, reading init parameters, etc.).

3) Request handling — service(req,res) → doGet/doPost/...

•  For every client request, the container calls service(request, response).
•

In HttpServlet, service() dispatches to HTTP-method handlers like doGet(), doPost(), doPut(), etc.
(this is why we usually override doGet/doPost).

4) Destruction — destroy()

•  When the container shuts down or unloads the servlet (redeploy, memory reclaim, etc.), it calls
destroy() once so the servlet can release resources (close files/DB connections, stop background
threads, flush caches).

Diagram: servlet lifecycle

(B)Servlet Life Cycle Methods:
There are three life cycle methods of a Servlet:
1. init() Method

Invoked once when the Servlet is instantiated.

•
•  Used to initialize resources (e.g., database connections).

Example:
@Override
public void init() throws ServletException {
    // Initialization code
}
2. service() Method

•  Handles client requests and responses.
•  Determines HTTP request type (GET, POST, PUT, DELETE) and delegates to doGet(), doPost(), etc.

Example:
@Override
public void service(ServletRequest req, ServletResponse res)

        throws ServletException, IOException {
    // Request handling code
}
3. destroy() Method

•  Called once at the end of the Servlet’s life cycle.
•  Cleans up resources (e.g., closes DB connections, releases memory).

Example:
@Override
public void destroy() {
    // Cleanup code
}
Diagram: servlet methods

Q12. Explain session management in servlets.
Why session management is needed
HTTP is stateless: every request is independent. Web apps need a way to remember a user across
multiple requests (login state, shopping cart, preferences). The Servlet specification defines HttpSession
so containers can track sessions using mechanisms such as cookies or URL rewriting without forcing the
developer to handle low-level details.
Main session tracking techniques (servlet-side)
A) Cookies (most common)

•  Container sends a session id cookie (commonly JSESSIONID) to the browser.
•  Browser returns it with later requests, letting the container map requests to the correct

HttpSession.

B) URL Rewriting (when cookies are disabled)

•  Session id is appended to URLs, often like ;jsessionid=....
•  The Servlet spec even warns that URL rewriting exposes session identifiers in places like

logs/bookmarks/referer headers/caches (so it’s less secure than cookies).

C) Hidden form fields (classic technique)

•  Put a session token in <input type="hidden"> fields and submit it back.
•  Works only for form-based navigation, not for normal links unless combined with rewriting. (Often

taught as a basic “session tracking” method alongside cookies/URL rewriting.)

D) SSL session tracking (container-specific option)
Some platforms can use SSL information as a tracking mechanism in addition to cookies and URL
rewriting.
Using HttpSession in a servlet (core API flow)
1) Create/get session
HttpSession session = request.getSession();      // creates if absent
// or:
HttpSession session2 = request.getSession(false); // null if absent
The specification describes HttpSession as the standard interface for tracking a user’s session and allowing
objects bound into the session to be shared among servlets in the same ServletContext.
2) Store and read values
session.setAttribute("user", userObject);
User u = (User) session.getAttribute("user");
Objects stored in the session can trigger listener behavior if they implement HttpSessionBindingListener
(useful for resource cleanup patterns).
3) Timeout and invalidation

•  Sessions end when they timeout or are invalidated.
•  You can explicitly log out a user by calling:

session.invalidate();
The spec discusses session timeout controls such as max inactive interval concepts (and related APIs),
which containers enforce.
Security best practices:

1) Avoid putting sensitive data in URL (URL rewriting leaks IDs into logs/bookmarks/referrers). Prefer

cookies.

2) Prevent session fixation after login by changing the session id:

            request.changeSessionId();

      The spec explicitly notes session IDs can be changed via HttpServletRequest.changeSessionId().
3) Store minimal objects in session; big objects increase memory usage and replication cost (clustered
servers). (This is common engineering practice; containers treat session as server memory, not a
database.)

Q13. Explain servlet filters and servlet chaining.
What is a servlet filter?
A filter is a component that sits in front of a target resource (servlet/JSP/static file) and can: - preprocess
the request, - optionally block the request, - modify/wrap the request/response, - call the next entity in
the chain, - postprocess the response.
The Jakarta EE tutorial states the filtering API is defined by Filter, FilterChain, and FilterConfig.
Filter lifecycle
Like servlets, filters have a lifecycle: 1) init(FilterConfig) — once 2) doFilter(request, response, chain) —
per request 3) destroy() — once
This lifecycle is shown in filter docs and consistently implemented by servlet containers.

Servlet chaining (FilterChain) — how it works
A FilterChain represents “the next thing to run”. - Calling chain.doFilter(req,res) invokes the next filter, or
if none remain, the target resource.
The Servlet specification explains how the container builds the chain and invokes the first filter, passing a
FilterChain object; it also specifies that URL-pattern matched filters are chained in the order declared in
the deployment descriptor.
Typical filter use-cases (write these in exams)

•  Authentication/authorization checks
•  Logging & audit
•  Compression (e.g., GZIP)
•  CORS headers / security headers
•
•  Request/response wrapping (e.g., caching request body, modifying parameters)

Input validation, XSS protection output escaping

Wrapping is a central concept: the spec discusses wrapping request/response objects so downstream
filters/servlets see the wrapper or a wrapper-of-wrapper.
Example: simple logging filter (shows chaining)
public class LoggingFilter implements Filter {
  public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain)
      throws IOException, ServletException {

    long start = System.currentTimeMillis();
    // pre-processing
    chain.doFilter(req, res);  // next filter or servlet
    // post-processing
    System.out.println("Took ms = " + (System.currentTimeMillis() - start));
  }
}
This pattern (pre → chain → post) is exactly what filter docs describe: after the target finishes, control
returns back up the chain for postprocessing
Filter mapping + dispatcher types (important detail)
Filters can be mapped: - by URL pattern (e.g., /*) - or by servlet name
Dispatcher types include REQUEST, FORWARD, INCLUDE, ERROR, ASYNC (used to control when a filter
applies)

Q14. Explain file upload and download using servlets.
A) File upload using servlets
1) HTML form requirement
Example:
<form method="post" action="upload" enctype="multipart/form-data">
  <input type="file" name="file">
  <button type="submit">Upload</button>
</form>

2) Enable multipart parsing: @MultipartConfig (Servlet 3+)
Servlets annotated with @MultipartConfig may retrieve uploaded components via getPart() / getParts().
import jakarta.servlet.annotation.MultipartConfig;
import jakarta.servlet.http.*;

@MultipartConfig(
  fileSizeThreshold = 1024 * 1024,
  maxFileSize = 10L * 1024 * 1024,
  maxRequestSize = 20L * 1024 * 1024
)
public class UploadServlet extends HttpServlet { ... }
3) Read parts with request.getParts() and use Part
The Java EE tutorial explains: - request.getParts() returns a collection of Part objects, - Part allows
introspection of each uploaded part.
The Part API provides methods such as: - getSubmittedFileName() - getInputStream() - write(String
fileName) - delete() (cleanup temp storage)
Example servlet code:
protected void doPost(HttpServletRequest request, HttpServletResponse response)
    throws IOException, ServletException {

  for (Part part : request.getParts()) {
    if ("file".equals(part.getName()) && part.getSubmittedFileName() != null) {
      String original = part.getSubmittedFileName();
      // IMPORTANT: sanitize original name before using it
      part.write(original); // writes to configured multipart location
      part.delete();        // optional cleanup depending on container behavior
    }
  }
  response.getWriter().println("Uploaded");
}
getSubmittedFileName() and write() are explicitly part of the Part interface.
B) File download using servlets
1) Set headers correctly (Content-Type + Content-Disposition)
To prompt “Save as / Download” behavior in browsers, you usually set: - Content-Type (e.g.,
application/pdf or application/octet-stream) - Content-Disposition: attachment; filename="..."
MDN explains that Content-Disposition indicates whether content should be displayed inline or
downloaded as an attachment, and gives the standard attachment; filename="..." form.
Example:
response.setContentType("application/pdf");
response.setHeader("Content-Disposition", "attachment; filename=\"report.pdf\"");
setHeader(...) is one of the standard ways to set response headers on HttpServletResponse.
2) Stream bytes to the response output stream
Use the response output stream and copy bytes in a buffer. The ServletResponse API includes
getOutputStream() and content length setters (which map to HTTP headers for HTTP servlets).

Example:
protected void doGet(HttpServletRequest request, HttpServletResponse response)
    throws IOException {

  Path file = Path.of("/safe/storage/report.pdf");

  response.setContentType("application/pdf");
  response.setHeader("Content-Disposition", "attachment; filename=\"report.pdf\"");
  response.setContentLengthLong(Files.size(file));

  try (ServletOutputStream out = response.getOutputStream();
       InputStream in = Files.newInputStream(file)) {
    in.transferTo(out);
  }
}

UNIT – V: JSP and Servlet Integration
Q15. Explain MVC architecture with diagram.
Meaning of MVC (Model–View–Controller)
MVC is an architectural pattern that splits a web application into three cooperating parts:

•  Model: application data + business rules (e.g., JavaBeans/POJOs, service classes, DAO/JPA layer).
•  View: presentation/UI (HTML output; in classic Java web apps this is commonly JSP with EL/JSTL).
•  Controller: request handling + navigation (in classic JSP/Servlet “Model-2”, this is commonly a

Servlet that interprets HTTP requests and chooses the next view).

Oracle’s Java EE tutorial describes the controller as the part that dispatches user requests, interprets
inputs (HTTP GET/POST), invokes model operations, and selects the next view for presentation.
MVC diagram (web application request flow)

In JSP/Servlet-based MVC (often called Model-2), the Servlet acts as controller and dispatches to JSP
pages for rendering. This separation is contrasted with “Model-1”, where JSP/servlet code tends to mix
presentation and logic.

Responsibilities of each layer (exam-friendly bullets)
1) Model - Stores and manages application state and business data - Implements business rules (e.g.,
validation rules, pricing rules) - Talks to persistence layer (DB) via DAO/JPA/JDBC
In the Oracle tutorial example, JavaBeans (like a shopping cart) are part of the model and get
prepared/updated by the controller.
2) View - Displays data (formats model data as HTML) - Should contain minimal logic (prefer EL/JSTL over
Java scriptlets) JSP is widely used as the view layer in server-side MVC; it’s also important that JSP is
translated into a servlet by the container.
3) Controller - Receives HTTP request - Selects action (what to do) - Calls model methods and prepares
data for the view - Chooses the next view (navigation) and forwards/redirects accordingly
The controller role and “dispatch to view JSP pages” is explicitly described in Oracle’s tutorial (Dispatcher
servlet example).
Advantages of MVC (write any 4–5 for marks)

•  Separation of concerns: UI changes don’t force business-logic changes.
•  Maintainability: clearer code structure, easier debugging.
•  Reusability: the same model can support multiple views (web page, REST, etc.).
•  Testability: model/services can be tested without rendering JSP.
•  Team collaboration: UI and backend developers can work independently.

Q16. Explain how JSP and Servlets work together in a web application.
Core idea (what actually happens)

1.  A Servlet is a Java class that handles requests and generates responses under the servlet

container.

2.  A JSP page is also a servlet at runtime: the JSP container translates JSP → a servlet class, then

executes it. JSP has a translation phase (once per page, typically) and a request phase (once per
request).

3.  Therefore, JSP and servlets “work together” mainly as Controller (Servlet) + View (JSP) in

MVC/Model-2 style applications.

Typical integration flow (step-by-step)
Step 1: Client sends request - Example: user submits login form → POST /login
Step 2: Servlet (Controller) handles request - Reads parameters: request.getParameter("username") -
Calls model/services: authService.login(...) - Puts results into scopes: - request.setAttribute("user", user)
for data needed only for the next view - session.setAttribute("user", user) if login must persist across
pages
Step 3: Controller chooses navigation - Forward to JSP to render HTML using the same request - Or
Redirect to a new URL (new browser request) after POST (Post/Redirect/Get pattern)
Step 4: JSP renders response - Uses EL/JSTL to display model data placed in request/session attributes -
Sends HTML back to the browser
This “controller servlet forwards to JSP view” workflow is described in practical tutorials (e.g., NetBeans e-
commerce tutorial) and is exactly the MVC/Model-2 pattern.
Forward vs Redirect (high-scoring integration point)
1) RequestDispatcher.forward(...) (server-side)
•  Happens inside the server/container
•  Same request/response objects are forwarded to another resource

•  Constraint from servlet spec: forward() can be called only before the response is committed (i.e.,

before output is sent to the client).

Typical use: - Forward to JSP after preparing model data:
request.setAttribute("products", products);
request.getRequestDispatcher("/WEB-INF/views/products.jsp")
       .forward(request, response);
2) response.sendRedirect(...) (client-side redirect)

•  Container sends a redirect response to the browser; the browser then requests the new URL.
•  Servlet spec: sendRedirect sets appropriate headers/body to redirect the client, and relative paths

must be converted to a fully qualified URL by the container.

Typical use: - After successful POST (e.g., form submission), redirect to avoid duplicate form resubmission:
response.sendRedirect(request.getContextPath() + "/products");
How data is passed from Servlet to JSP (important)
The most common mechanism is request attributes:
// Controller
request.setAttribute("msg", "Welcome");
request.getRequestDispatcher("/welcome.jsp").forward(request, response);
Then in JSP:
Message: ${msg}
Why this works: JSP inherits servlet concepts (request/response/session/context) and is executed via the
servlet protocol because the JSP page implementation object is a servlet.
Where JSP fits technically (what the container does)

•  The JSP container converts JSP into a servlet class (JSP compiler step).
•

JSP pages are textual components with:

o  translation phase (JSP → servlet class)
o  request phase (serving each request)

•  Standard JSP actions like <jsp:include> / <jsp:forward> ultimately map to servlet mechanisms

(forward/include through the servlet API).

UNIT – VI (M6): Hibernate Framework
Q17. Explain Hibernate architecture with diagram.
What Hibernate is doing (big picture)
Hibernate ORM “sits between” your Java application’s data-access layer and the relational database. Your
code calls Hibernate APIs to load/store/query domain objects, and Hibernate translates those operations
into SQL and JDBC calls.
Core Hibernate architecture components (must-write points)
1) SessionFactory

•  SessionFactory is a thread-safe, immutable representation of the mapping between your domain

•
•

model and the database.
It is very expensive to create, so applications typically have one SessionFactory per database.
It maintains shared services like 2nd-level cache, connection handling, and transaction
integration.

buildSessionFactory() method gathers the meta-data which is in the cfg Object.
From cfg object it takes the JDBC information and create a JDBC Connection.
SessionFactory factory=cfg.buildSessionFactory();

2) Session

•  Session is single-threaded and short-lived, modeling a “Unit of Work”.
•
•

It wraps a JDBC Connection and is a factory for Transaction.
It holds a persistence context (first-level cache), helping repeatable reads and identity-scope
within the unit of work.
Session session = factory.openSession();

3) Transaction

•  Transaction is also single-threaded and short-lived, used to demarcate a physical transaction

boundary (JDBC or JTA).
Transaction tx=session.beginTransaction();
tx.commit();

4) Persistent entities / mappings
Entities are mapped Java objects (POJOs) with metadata (annotations or XML) telling Hibernate which
table/columns to use. (You’ll detail this in Q18.)
5) JDBC + Database
Hibernate generates SQL and executes it via JDBC (connections are typically obtained from a pool
configured under the SessionFactory).
6) Query

•  Query is an interface in the org.hibernate package used to execute HQL queries.

•

•

It is created using the Session.createQuery() method to interact with the database.
It supports advanced features like pagination (setMaxResults(), setFirstResult()) and named
parameters for better query handling.

7) Criteria

•  Criteria is a simplified API for retrieving entities by composing Criterion objects.
•  The Session is a factory for Criteria. Criterion instances are usually obtained via the factory

methods on Restrictions.

Diagram: Hibernate architecture:

Q18. Explain mapping of Java class to database table.
What “mapping” means
Mapping is the metadata that tells Hibernate/JPA: - which Java class is persisted (entity), - which table
stores it, - which field/property maps to which column, - which field is the primary key, - and how
relationships map (foreign keys/join tables).
Jakarta Persistence explains it simply: fields map to columns, and every entity must have a primary key
mapped using @Id.
Basic entity mapping using annotations (most common)
Step 1: Mark the class as an entity: @Entity
Every persistent POJO is declared using @Entity.
Step 2: Specify the primary key: @Id
@Id declares the identifier property (primary key) of the entity.
Step 3: Map entity to a table: default or @Table

•  By default, if you don’t specify @Table, the entity maps to a table with the (unqualified) class

name (configuration by exception).

•  Use @Table(name="...") to override table name, schema, catalog, and constraints.

Step 4: Map fields/properties to columns: default or @Column

•  Basic attributes map to columns; if you need a different column name or constraints, use

@Column(name="..."). Hibernate’s quick-start notes “a basic attribute… maps a column of a
database table”.

Step 5: (Common) Generate IDs: @GeneratedValue
If the primary key is a surrogate key, you can let Hibernate/database generate it using @GeneratedValue.
Example: mapping a Java class to a table
import jakarta.persistence.*;

@Entity
@Table(name = "student")
public class Student {

  @Id
  @GeneratedValue
  private Long id;

  @Column(name = "full_name", nullable = false, length = 100)
  private String name;

  @Column(name = "email", unique = true)
  private String email;

  // getters/setters
}

This style follows the standard ideas shown in Hibernate’s entity mapping docs: @Entity + @Id, optional
@Table(name=...).

Q19. Explain CRUD operations using Hibernate.
The “unit of work” pattern (how CRUD is normally done)
CRUD is typically done inside: 1) Open a Session 2) Begin a Transaction 3) Perform operations
(Create/Read/Update/Delete) 4) Commit (or rollback on error) 5) Close session
This aligns with Hibernate’s model of Session and Transaction being short-lived and bound to a unit of
work.
CREATE (Insert)
Using persist()
Hibernate explicitly notes: persist() has no immediate effect on the database; it schedules an insert that’s
executed later when the session is flushed (often at commit).
try (Session session = sessionFactory.openSession()) {
  Transaction tx = session.beginTransaction();

  Student s = new Student();
  s.setName("Asha");
  s.setEmail("asha@example.com");

  session.persist(s);     // schedules INSERT
  tx.commit();            // triggers flush by default
}
Hibernate describes flushing as the process that synchronizes in-memory changes by executing SQL
INSERT/UPDATE/DELETE, and notes a flush is triggered by default when the transaction commits.
READ (Select)
Using find(Class, id)
Hibernate’s introduction guide lists find(Class,Object) as a method to “obtain a persistent object given its
type and its id”.
try (Session session = sessionFactory.openSession()) {
  Student s = session.find(Student.class, 1L);
  // use s (may be null if not found)
}
(Also, reading/locking operations like find() generally hit the DB immediately unless already available in
the persistence context/1st-level cache.)
UPDATE (Modify existing row)
“Dirty checking” (no explicit update call)
Hibernate notes there’s no update() operation for a stateful session because modifications to managed
entities are automatically detected and synchronized on flush.
try (Session session = sessionFactory.openSession()) {
  Transaction tx = session.beginTransaction();

  Student s = session.find(Student.class, 1L);

  s.setEmail("newmail@example.com"); // change tracked

  tx.commit(); // flush executes UPDATE
}
DELETE (Remove)
Using remove()
Like persist(), Hibernate notes remove() does not immediately delete; it schedules a delete for flush time.
try (Session session = sessionFactory.openSession()) {
  Transaction tx = session.beginTransaction();

  Student s = session.find(Student.class, 1L);
  if (s != null) session.remove(s);  // schedules DELETE

  tx.commit();
}

Q20. Explain HQL with examples.
What is HQL?
HQL (Hibernate Query Language) is a powerful query language that looks like SQL, but it is object-
oriented: it understands entities, inheritance/polymorphism, and associations.
In modern Hibernate documentation, HQL is described as a “dialect” of JPQL, where JPQL is a subset of
modern HQL.
Key differences from SQL (exam points)

•  SQL queries tables/columns; HQL queries entities/properties.
•  Results are usually entity objects (or projections/DTOs).

Basic HQL syntax (with examples)
1) Simplest query: from Entity
Hibernate’s HQL reference gives the classic example:
from eg.Cat
which returns all instances of the class.
Example in an app:
List<Student> list =
  session.createQuery("from Student", Student.class)
         .getResultList();
2) select + where
List<Student> top =
  session.createQuery(
      "select s from Student s where s.email like :pat",
      Student.class
  )
  .setParameter("pat", "%@example.com")
  .getResultList();
Hibernate’s user guide shows usage of named parameters via .setParameter("name", "J%") patterns in
HQL/JPQL examples.

3) Projections (select specific columns/properties)
HQL supports selecting specific properties:
List<Object[]> rows =
  session.createQuery(
      "select s.name, s.email from Student s",
      Object[].class
  ).getResultList();
Also, Hibernate’s modern HQL guide shows you may write a query in a more “alias-first” style like: from
Book book select book.title, book.isbn.
4) Joins and join fetch (performance feature)
Hibernate’s HQL/JPQL documentation explains JOIN FETCH can load an associated collection in the same
SQL query, helping avoid N+1 queries.
Example (typical domain: Author → books):
List<Author> authors =
  session.createQuery(
      "select distinct a from Author a join fetch a.books",
      Author.class
  ).getResultList();
5) Aggregate functions (example)
Hibernate’s modern guide shows functions like size(): select name, size(books) from Author.
Example:
List<Object[]> stats =
  session.createQuery(
      "select a.name, size(a.books) from Author a",
      Object[].class
  ).getResultList();

Below are MORE IMPORTANT, UNIQUE & HIGH-PROBABILITY semester exam
questions
No repetition from any previous lists.
Focused on analytical, application-based & long-answer questions.
UNIT – I : Java EE
1. Describe the evolution of Java web technologies.

Java web technologies have evolved from basic dynamic content generation to a comprehensive
enterprise platform. The process started with CGI and advanced through Servlets and JSP. This led to
the development of Java EE for building scalable web applications.
•  CGI (Common Gateway Interface): The earliest web technology, but it suffered from performance

issues because it created a new, heavy OS process for every single user request.

•  Java Servlets: Introduced to replace CGI. Servlets significantly improved performance by using

lightweight threads for each request rather than heavy OS processes, running within a Java Web
Server.

•  JSP (JavaServer Pages): While Servlets were great for logic, writing HTML inside Java code was
tedious. JSP was introduced to allow writing Java code inside HTML, acting as the View layer.

•  EJB and Java EE (J2EE): As applications grew, enterprise features like transaction management,

security, and distributed computing were needed, leading to the full Java EE stack.

•  Modern Frameworks: Java EE evolved and paved the way for modern, lightweight frameworks like

Spring and Hibernate, and eventually the transition from Java EE to Jakarta EE.

2. Explain how Java EE supports distributed applications.

Java EE is designed to build distributed, multi-tiered applications that run across multiple systems. It
provides built-in support for scalability and reliability. This makes it ideal for enterprise environments
where components are spread geographically.
•  Multi-Tier Architecture: Java EE inherently supports breaking an application into Client, Web,
Business, and Enterprise Information System (EIS) tiers, which can run on separate machines.
•  EJB (Enterprise JavaBeans): EJBs allow developers to write business logic that resides on remote

servers, enabling clients to invoke methods over a network securely.

•  RMI (Remote Method Invocation): Java EE relies heavily on RMI (and RMI-IIOP) to allow Java

objects running on one JVM to invoke methods on objects in another JVM.

•  Web Services: Java EE provides robust APIs (JAX-WS for SOAP, JAX-RS for REST) to create
interoperable web services that allow different distributed systems to communicate.

•  JMS (Java Message Service): Allows distributed components to communicate asynchronously via

message queues and topics, decoupling the sender and receiver.

3. Write a note on reusable components in Java EE.

Reusable components are a core strength of Java EE that promote code efficiency and maintainability.
These pre-built modules can be used across different applications without modification. They reduce
development time significantly in enterprise projects.
•  Write Once, Run Anywhere: Java EE components are standard Java classes, meaning they inherit

Java's platform independence and can be deployed on any compatible server.

•  JavaBeans: Simple, reusable, encapsulated Java classes with getters and setters that can be easily

used across JSPs and Servlets to carry data (Model).

•  Enterprise JavaBeans (EJB): Highly reusable business components that encapsulate complex logic

and can be injected into multiple web applications or web services.

•  Custom Tags (JSTL): JSP allows the creation of reusable custom tag libraries, allowing developers to

reuse UI logic across multiple web pages without rewriting code.

•  Resource Adapters: Java EE provides standardized components (via JCA) to connect to legacy

systems, which can be reused across different enterprise applications.

4. Explain the importance of web containers in Java EE.

Web containers form the runtime environment for Java EE web components like Servlets and JSP pages.
They are responsible for managing the lifecycle and execution of these components. Their presence is
fundamental to Java-based web application deployment.
•  Lifecycle Management: The container (e.g., Tomcat) manages the entire lifecycle of a Servlet or JSP,

from instantiation and initialization (init) to execution (service) and destruction (destroy).

•  Communication Support: It abstracts the complexity of network communication. It listens on a port,

accepts HTTP requests, and translates them into HttpServletRequest objects.

•  Multithreading Support: The container automatically creates and manages a new Java thread for

every incoming client request, saving developers from writing complex concurrency code.

•  JSP Translation: It is responsible for dynamically translating JSP files into Java Servlet classes,

compiling them, and loading them into memory.

•  Security & Configuration: It enforces security constraints defined in the web.xml file and provides

essential services like database connection pooling and session management.

5. Discuss how Java EE simplifies web application development.

Java EE simplifies web application development by providing standardized APIs, containers, and
services. Developers avoid writing boilerplate code for common tasks. This allows focus on business
logic rather than infrastructure.
•  Standardized APIs: It provides a rich set of built-in APIs for database access (JDBC), messaging (JMS),

•

and persistence (JPA), eliminating the need for third-party libraries.
Infrastructure Abstraction: Developers only need to focus on business logic; the Java EE container
handles infrastructure tasks like multi-threading, memory management, and socket connections.
•  MVC Implementation: It naturally supports the Model-View-Controller design pattern, making large

codebases easier to organize, test, and maintain.

•  Declarative Configuration: Features like security, error handling, and URL mapping can be
configured in an XML file (web.xml) or via annotations, without writing hard-coded logic.

•  Portability: Applications written to the Java EE specification can be deployed on any compliant

application server (like GlassFish, WebLogic, or WildFly) without code changes.

6. Explain request–response model in Java EE web applications.

The request-response model is the foundation of communication in Java EE web applications based on
HTTP protocol. A client sends a request and the server returns a response. This stateless model is
implemented primarily through Servlets.
•  Client Initiation: The cycle begins when a client (usually a web browser) sends an HTTP Request over

the network to the server.

•  Container Interception: The Java EE Web Container receives the raw HTTP text and parses it into an

HttpServletRequest Java object.

•  Servlet Processing: The container invokes the appropriate Servlet (based on URL mapping), passing

the Request object and an empty HttpServletResponse object.

•  Logic Execution: The Servlet reads parameters from the request, executes business logic,
communicates with a database if necessary, and writes data to the Response object.

•  Response Delivery: The container takes the populated HttpServletResponse object, converts it back

into an HTTP text response, and sends it back to the client's browser.

7. Write a note on advantages of server-side programming using Java EE.

Server-side programming using Java EE offers several benefits over client-side approaches. Code
executes on the server, keeping business logic secure. It enables dynamic content generation based on
user requests and database data.
•  Platform Independence: Server-side Java code runs on the JVM, meaning the same application can

be hosted on Windows, Linux, or macOS servers without modification.

•  High Performance: Unlike older CGI scripts that started a new process per request, Java EE creates

lightweight threads, handling thousands of concurrent users efficiently.

•  Robust Security: Java EE provides built-in, container-managed security models including

authentication, authorization, and data encryption techniques.

•  Scalability: Java EE applications can easily be scaled horizontally by adding more servers to a cluster,

sharing workloads seamlessly.

•  Extensive Ecosystem: Developers have access to standard libraries for almost every enterprise need,

from email (JavaMail) to XML parsing and JSON processing.

UNIT – II : JDBC
8. Write a note on driver loading and registration process.

Driver loading and registration is the first step in any JDBC application. It makes the database driver
available to the DriverManager. This process enables the creation of database connections in Java
applications.
•  Purpose: Loading a driver makes the Java application aware of the specific database vendor's

implementation of the JDBC API.

•  Traditional Method: Historically, Class.forName("com.mysql.cj.jdbc.Driver") was used to dynamically

load the driver class into memory at runtime.

•  Registration: When the driver class is loaded, it contains a static block that automatically calls

DriverManager.registerDriver() to register itself with the JDBC API.

•  Modern Approach (Java 6+): Thanks to the Service Provider Mechanism (ServiceLoader), explicitly
calling Class.forName() is no longer strictly required; the DriverManager automatically finds drivers
in the classpath.

•  Connection Establishment: Once registered, the DriverManager.getConnection(url, user, pass)

method iterates through registered drivers to find one that understands the provided connection
URL.

9. Discuss performance issues in JDBC applications.

JDBC applications often face performance challenges due to improper resource management and
inefficient API usage. These issues can degrade application speed and scalability. Understanding them
helps developers build optimized database layers.
•  Connection Overhead: Opening and closing a physical database connection for every query is

extremely slow and resource-intensive. (Solution: Use Connection Pooling).

•  Un-optimized Statements: Using Statement instead of PreparedStatement forces the database to

parse and compile the SQL string every single time it runs.

•  Network Latency: Fetching data row-by-row or sending multiple individual insert statements causes

excessive network round-trips. (Solution: Use Batch Processing).

•  Resource Leaks: Failing to properly close ResultSet, Statement, or Connection objects in a finally

block or try-with-resources leads to memory leaks and connection exhaustion.

•  Fetching Unnecessary Data: Using SELECT * or retrieving massive result sets without pagination

wastes RAM and network bandwidth.

10. Explain how JDBC supports database independence.

JDBC supports database independence by providing a standard API that hides vendor-specific details.
Applications interact with interfaces rather than direct database implementations. This allows
switching databases with minimal code changes.
•

Interface-Based Design: The java.sql package consists mostly of interfaces (like Connection,
Statement, ResultSet), not concrete classes.

•  Driver Abstraction: Vendors (Oracle, MySQL, PostgreSQL) provide the concrete implementation

classes in their specific JDBC driver files (.jar).

•  Plug-and-Play Architecture: To switch databases, a developer only needs to swap the driver .jar file

and change the connection URL string; the Java code remains identical.

•  Standardized SQL: While databases have dialects, JDBC encourages the use of standard SQL,

meaning basic CRUD operations work identically across different platforms.

•  DatabaseMetaData: JDBC provides metadata classes that allow an application to dynamically query

the database at runtime to discover its specific capabilities and adjust accordingly.

11. Write a note on handling large objects (BLOB, CLOB) in JDBC.

JDBC provides special support for handling large objects like BLOB and CLOB. BLOB stores binary data
while CLOB stores character data. Proper handling is necessary to avoid memory issues with large files.
•  Definition: BLOB (Binary Large Object) is used for storing binary data like images or audio. CLOB

(Character Large Object) is used for large text files like XML or documents.

•  PreparedStatement Usage: To insert a BLOB/CLOB, you must use a PreparedStatement because

standard SQL strings cannot accommodate raw binary streams.

•  Setting Data: You use setBlob(index, InputStream) or setBinaryStream() for BLOBs, and

setClob(index, Reader) or setCharacterStream() for CLOBs.

•  Retrieving Data: When reading from a ResultSet, use getBlob() or getBinaryStream() to fetch the

data chunk-by-chunk rather than loading massive files directly into memory.

•  Memory Management: Handling LOBs via streams is crucial to prevent OutOfMemoryError in Java,

as the data streams directly between the DB and the file system.

12. Explain JDBC error handling mechanism with examples.

JDBC uses SQLException for error handling. It is a checked exception that provides detailed
database error information. Proper handling ensures robust and debuggable applications.
•  SQLException Class: Almost all JDBC methods throw SQLException, which is a checked exception

that must be caught using try-catch blocks.

•  Error Details: The SQLException object provides valuable methods like getMessage() (string

description), getErrorCode() (vendor-specific number), and getSQLState() (X/Open standard string).

•  Exception Chaining: Since one DB operation might trigger multiple errors, SQLException supports

chaining. You can loop through them using ex.getNextException().

•  Example Usage:

catch(SQLException e) {
    System.out.println("Error Code: " + e.getErrorCode());
    System.out.println("Message: " + e.getMessage());
}

•  SQLWarnings: For non-fatal errors (like data truncation), JDBC generates SQLWarning objects
attached to the Connection or Statement, which do not stop execution but should be logged.

13. Discuss the role of SQLData and RowSet in JDBC.

SQLData and RowSet are advanced JDBC features that extend basic functionality. SQLData helps map
complex database types while RowSet offers flexible result handling. Both improve developer
productivity.

•  SQLData Interface: SQLData is used for custom mapping of SQL User-Defined Types (UDTs) to Java

classes, allowing you to treat a complex database object as a single Java object.

•  RowSet Overview: A RowSet is an interface that extends ResultSet but acts as a JavaBeans

component, making it easier to use in visual builders and network transfers.

•  Disconnected Architecture: Unlike a ResultSet which requires an open connection, a CachedRowSet

can hold data in memory, close the DB connection, and still allow data manipulation.
•  Updatability: RowSet objects are inherently scrollable and updatable by default, allowing

developers to easily modify data and sync it back to the DB later.

•  Reduced Overhead: By working disconnected, RowSets free up valuable database connections

quickly, improving the overall scalability of the application.

14. Explain how batch processing reduces network overhead.

Batch processing in JDBC allows execution of multiple SQL statements in a single database call. It
significantly reduces network overhead compared to individual executions. This technique improves
performance in bulk operations.

•  Definition: Batch processing allows you to group multiple SQL statements together and send them

to the database in a single network trip.

•  The Problem: Normally, executing 1,000 INSERT statements requires 1,000 separate requests and

•

1,000 responses across the network, causing massive latency.
Implementation: Developers use the addBatch() method on a Statement or PreparedStatement to
queue up operations locally in memory.

•  Execution: Calling executeBatch() packages the entire queue and sends it as one bulk operation to

the database.

•  Result: The database processes the chunk and returns an array of update counts. This drastically

cuts down TCP/IP network traffic and speeds up bulk data operations.

UNIT – III : JSP
15. Explain JSP compilation process with flow.

JSP compilation process converts JSP pages into servlets automatically. It occurs when the page is first
accessed or modified. This two-phase process makes dynamic content generation easier for
developers.
•  Request & Identification: A client requests a .jsp file. The web container determines if this is the first

request or if the JSP file has been modified since the last request.

•  Translation Phase: The container parses the JSP file and translates the HTML and JSP tags into a

standard Java Servlet class (.java file).

•  Compilation Phase: The container invokes the Java compiler (javac) to compile the generated .java

file into a .class bytecode file.

•  Loading and Instantiation: The container loads the newly created Servlet class into memory and

instantiates it.

•  Execution Phase: The container calls the _jspInit() method once, and then calls the _jspService()

method to process the request and generate the HTML response.

16. Write a note on JSP implicit objects related to output handling.

JSP provides implicit objects that are automatically available in JSP pages. Two important objects
related to output handling are ‘out’ and ‘response’.

•  Definition: Implicit objects are pre-created Java objects provided by the JSP container that

developers can use immediately without declaring them.

•  The out Object: This is an instance of JspWriter. It is the primary object used to send text, HTML, or

variables directly to the client's browser (e.g., out.print("Hello");).

•  The response Object: An instance of HttpServletResponse. It is used to manipulate the HTTP

response headers, set cookies, or redirect the user to another page.

•  Buffering Output: The out object usually utilizes a buffer. This means output is gathered in memory
before being sent over the network, which improves performance and allows clearing the output if
an error occurs.
Interaction: While out handles the physical body of the HTML page, response handles the meta-
information (like status codes and content types) surrounding that body.

•

17. Explain page directive attributes in detail.

The page directive provides instructions to the JSP container about how to process the page. It appears
at the top of JSP files using <%@ page %> syntax. These attributes control important page-level
behavior.
•  Purpose: The <%@ page ... %> directive provides global instructions to the JSP container on how to

•

translate the current page into a Servlet.
import attribute: Works exactly like Java imports, allowing the JSP to use external Java classes (e.g.,
<%@ page import="java.util.List" %>). This is the only attribute that can appear multiple times.

•  session attribute: Takes "true" or "false". If true (default), the page implicitly creates an HttpSession.

If false, the session implicit object is unavailable, saving server memory.

•  errorPage & isErrorPage: errorPage="error.jsp" defines where to route unhandled exceptions. On
the receiving end, isErrorPage="true" enables the exception implicit object to print the error.

•  contentType attribute: Defines the MIME type and character encoding of the response (e.g., <%@

page contentType="text/html; charset=UTF-8" %>).

18. Discuss advantages of JSP over CGI.

JSP offers several advantages compared to CGI technology for generating dynamic web content. CGI
creates a new process for each request while JSP uses a servlet-based approach.
Performance (Threading): CGI creates a new, heavy OS process for every request. JSP uses a single JVM
and spawns lightweight threads, making it significantly faster and less resource-heavy.
•  Persistence: A CGI script is loaded into memory, executed, and destroyed. A JSP (as a Servlet)
remains in memory after initialization, resulting in zero startup time for subsequent requests.

•  Java Ecosystem: JSP has full access to the powerful Java API, including JDBC for databases, JNDI, and

JavaBeans, which standard CGI (often written in Perl/C) lacks natively.

•  State Management: JSP provides built-in, easy-to-use session tracking (session implicit object),

whereas CGI requires developers to manually code state management via cookies or hidden fields
from scratch.

•  Separation of Concerns: JSP allows the use of Custom Tags and JavaBeans, making it much easier to

separate front-end HTML from back-end logic compared to clunky CGI scripts.

19. Explain how JSP simplifies servlet development.

JSP simplifies servlet development by separating presentation logic from business logic. Writing HTML
inside Java print statements in servlets is tedious.

•  HTML-Centric: In a Servlet, you must write out.println("<html>..."); for every line of UI. JSP acts like

•

an HTML file where you only insert Java where needed, making UI design vastly easier.
Implicit Objects: JSP automatically provides 9 objects (like request, response, session, out) without
the developer having to write the code to instantiate or fetch them.

•  No Compilation Needed: Developers simply save the .jsp file and refresh the browser. The container

handles the tedious process of translation and compilation automatically.

•  JSTL and EL: JSP offers the Expression Language (${}) and the Standard Tag Library, allowing

developers to loop and conditionally display data without writing raw Java code.

•  Role Separation: It allows web designers to work on the HTML/CSS in the JSP file, while Java

developers can work on the backend Servlets/JavaBeans independently.

20. Write a note on JSP session tracking techniques.

Session tracking maintains user state across multiple requests in JSP applications. Since HTTP is
stateless, various techniques are used.
•  Why it's needed: HTTP is stateless. The server forgets the user after every request. Session tracking

ties multiple requests to a single user.

•  Cookies: Small text files stored on the client's browser. The server reads the cookie on subsequent

requests. (If users disable cookies, this fails).

•  URL Rewriting: Appending a unique session ID to the end of every URL (e.g.,

page.jsp?jsessionid=12345). Used as a fallback if cookies are disabled.

•  Hidden Form Fields: Embedding invisible input fields in HTML forms (<input type="hidden"

name="sessionID" value="...">). Only works if navigation happens strictly via form submissions.
•  HttpSession API: The standard Java EE way. It automatically handles the heavy lifting, usually using

cookies by default and falling back to URL rewriting, providing a simple setAttribute() / getAttribute()
interface.

21. Explain role of JSP in MVC-based applications.

In MVC architecture, JSP plays the role of the View component. MVC separates Model, View and
Controller responsibilities. JSP focuses exclusively on presentation logic in Java EE applications.
•  The View Layer: In the Model-View-Controller architecture, JSP strictly acts as the "View". Its sole

responsibility is to generate the user interface (HTML/CSS).

•  Passive Receiver: A JSP should not fetch data from a database directly. Instead, it waits for the

Controller (Servlet) to process the request and forward the data to it.

•  Data Presentation: The JSP receives data encapsulated in Model objects (JavaBeans) from the

Servlet, usually placed in the request scope.

•  Expression Language (EL): JSPs use EL (${user.name}) and JSTL (<c:forEach>) to extract and loop

through the model data gracefully, avoiding raw Java code (scriptlets).

•  Clean Codebase: By restricting JSP to the View role, the application becomes highly maintainable. UI

changes don't break business logic, and logic bugs don't affect the UI.

22. Discuss security considerations in JSP pages.

Security in JSP pages is critical to prevent common web vulnerabilities. Poorly written JSP code can
expose applications to attacks like XSS and SQL injection. Several best practices must be followed.
•  Cross-Site Scripting (XSS): JSPs are vulnerable if they print user input directly. Always escape output

using JSTL's <c:out value="${var}" /> to sanitize malicious scripts.

•  Direct Access Prevention: JSPs containing sensitive fragments or logic should be placed inside the
WEB-INF folder, making them inaccessible directly via URL but accessible via Servlet forwarding.

•  SQL Injection Prevention: Never use raw Java scriptlets (<% %>) in a JSP to construct database

queries. Always use Servlets with PreparedStatements for database access.

•  Authentication Validation: Ensure that every secure JSP checks if a valid session exists (e.g., using a
Filter) before rendering, preventing unauthorized users from accessing the page via direct URL.

•  Disabling Scriptlets: It is a security best practice to disable Java scriptlets entirely via web.xml
(<scripting-invalid>true</scripting-invalid>) to force developers to use secure tags and EL.

23. Explain errorPage and isErrorPage attributes.

The errorPage and isErrorPage attributes of the page directive handle exceptions gracefully in JSP. They
help create a consistent error handling mechanism across the application instead of showing raw stack
traces to users.
•  Declarative Error Handling: These attributes provide a clean way to handle exceptions without

cluttering standard JSP pages with try-catch blocks.

•  The errorPage attribute: Placed in the source page (e.g., <%@ page errorPage="error.jsp" %>). If any
unhandled runtime exception occurs on this page, the container automatically forwards the request
to error.jsp.

•  The isErrorPage attribute: Placed in the destination error handler page (e.g., <%@ page

isErrorPage="true" %>). This tells the container that this page is specifically designed to handle
errors.

•  The exception Object: Setting isErrorPage="true" activates the 9th JSP implicit object, exception,

which contains the actual error thrown by the source page.

•  User Experience: Instead of the user seeing a scary, technical Java stack trace (500 Server Error),

they see a friendly, custom-designed HTML error page.

UNIT – IV : Servlets
24. Explain servlet request handling mechanism.

The servlet request handling mechanism defines how a web container processes incoming client
requests. It forms the foundation of dynamic web applications in Java EE. The mechanism revolves
around the HttpServletRequest object and servlet lifecycle methods.
•  Client Request: A browser sends an HTTP request (GET, POST, etc.) to a specific URL mapped to a

Servlet.

•  Container Processing: The Web Container creates HttpServletRequest and HttpServletResponse

objects representing the incoming data and outgoing response mechanism.

•  The service() Method: The container calls the Servlet's service() method, passing the request and

response objects.

•  Method Dispatching: The service() method inspects the HTTP method type (GET, POST, PUT, etc.)
and dynamically dispatches the request to the appropriate handler method (e.g., doGet() or
doPost()).

•  Parameter Extraction: Inside the doGet/doPost method, the developer uses methods like

request.getParameter("username") to read form data and execute business logic.

25. Write a note on servlet response generation.

Servlet response generation involves creating and sending dynamic content back to the client. The
HttpServletResponse object provides methods to build this response. It completes the
request-response cycle in Java EE.
•  Response Object: The HttpServletResponse object is used by the Servlet to format and send data

back to the client.

•  Setting Content Type: Before writing any data, the Servlet must define what type of data it is

sending using response.setContentType("text/html") or application/json.

•  Acquiring the Writer: The Servlet obtains an output stream using PrintWriter out =

response.getWriter(); to send text data, or getOutputStream() for binary data (like images).

•  Writing the Output: The developer uses out.println() to sequentially write HTML tags, JSON strings,

or XML structures directly to the response buffer.

•  Status Codes & Headers: The response object is also used to set HTTP status codes (e.g., 404, 500)

and custom headers (e.g., cache controls) via methods like response.setStatus().

26. Explain servlet context initialization parameters with use cases.

Servlet context initialization parameters are application-wide configuration values defined in
web.xml. They are loaded when the web application starts. These parameters provide global settings
accessible to all servlets and JSPs.
•  Definition: Context Initialization Parameters are configuration values stored in web.xml using the

<context-param> tag.

•  Global Scope: Unlike ServletConfig parameters which apply only to one specific Servlet,

ServletContext parameters are globally available to every Servlet and JSP in the entire web
application.

•  Retrieval: Developers read these values inside a Servlet using
getServletContext().getInitParameter("parameterName");.

•  Use Case - Database Configurations: Storing the database driver name, URL, or connection pool

settings, since all Servlets need to know how to connect to the DB.

•  Use Case - Administrator Info: Storing global application constants like the Admin's support email

address, payment gateway URLs, or the application's current version number.

27. Discuss importance of thread management in servlets.

Servlets follow a single-instance, multi-threaded model in Java EE. Thread management is critical
because multiple requests are handled by separate threads on the same servlet instance. Poor
management can lead to data inconsistency.
•  Single Instance Model: By default, the container creates only one instance of a Servlet class in

memory.

•  Multi-threading: For every concurrent client request, the container spawns a new thread that

executes the service() method on that single shared instance.

•  Thread Safety Issue: Because threads share the same instance, any instance variables (class-level
variables) are shared across all users. Modifying them can lead to severe data corruption/race
conditions.

•  Best Practice: To ensure thread safety, developers must strictly use local variables (inside

doGet/doPost) because each thread gets its own isolated stack memory for local variables.

•  Synchronization Overhead: Avoid using synchronized blocks in the doGet/doPost methods unless

absolutely necessary, as this forces requests to queue up sequentially, destroying server
performance.

28. Explain how servlets maintain state in stateless HTTP.

HTTP is a stateless protocol where each request is independent. Servlets provide mechanisms to
maintain state across multiple requests. This is achieved through session tracking techniques in Java EE
applications.
•  The Stateless Problem: HTTP treats every request as a brand new interaction, making it impossible

natively to remember a user across multiple page clicks (like a shopping cart).

•  Cookies: Servlets can create a Cookie object, add it to the response, and read it on the next request

using request.getCookies().

•  URL Rewriting: Servlets can append session data to URLs using response.encodeURL(), ensuring

state is passed via GET parameters.

•  Hidden Form Fields: Emitting HTML forms containing <input type="hidden"> to pass state data

during form submissions.

•  HttpSession API: The most powerful method. request.getSession() assigns a unique ID to the user
(via a cookie), allocating server-side memory (setAttribute) to securely store complex Java objects
for that user.

29. Write a note on cookie security issues.

Cookies are widely used in servlets for session tracking and storing user preferences. However, they
introduce several security vulnerabilities if not handled properly. Understanding these issues is
important for secure Java EE development.
•  Plain Text Storage: Cookies are stored on the client's local machine in plain text, meaning sensitive

data (like passwords or credit cards) should never be stored in them.

•  Cross-Site Scripting (XSS): If a malicious script is injected into a page, it can access document.cookie

and steal session IDs. Setting the HttpOnly flag prevents JavaScript from accessing the cookie.
•  Network Sniffing: If sent over plain HTTP, cookies can be intercepted over the network. Setting the

Secure flag ensures the cookie is only transmitted over encrypted HTTPS connections.

•  Cross-Site Request Forgery (CSRF): Browsers automatically send cookies with requests. Attackers
trick users into clicking links that perform unwanted actions using their active session cookie.
SameSite attribute helps mitigate this.

•  Size and Count Limits: Malicious users can attempt to overflow the server by sending massive

cookies. Applications must validate and restrict incoming cookie sizes.

30. Explain advantages of filters over servlets.

Filters were introduced in Servlet 2.3 to perform pre-processing and post-processing tasks. They
provide modular solutions for cross-cutting concerns. Filters have distinct advantages compared to
traditional servlets.
•

Interception: Servlets generate the actual response. Filters sit in front of Servlets, intercepting the
request before it reaches the Servlet, or modifying the response before it reaches the client.
•  Reusability (Pluggability): A single Filter (e.g., an Authentication Filter) can be mapped to multiple

Servlets or entire URL patterns, eliminating duplicate code across Servlets.

•  Separation of Concerns: Filters remove non-core logic (like logging or compression) from the

Servlet, allowing the Servlet to focus purely on business logic.

•  Chain Execution: Multiple filters can be chained together (FilterChain). The request passes through

Filter A, then Filter B, then the Servlet, providing modular processing.

•  Non-Destructive: You can add, remove, or rearrange filters in web.xml or via annotations without

touching the source code of the Servlets they protect.

31. Discuss real-time applications of servlet filters.

Servlet filters have numerous practical applications in enterprise web applications. They address
common requirements like security and performance without modifying core servlet logic. Their real-
time usage demonstrates their power in Java EE environments.
•  Authentication & Authorization: Checking if a user's session is valid or if they have the correct

admin role before allowing the request to reach secure JSPs or Servlets.

•  Auditing and Logging: Recording the client's IP address, the time of request, and the requested

URL to a log file for analytics or security audits.

•  Data Compression: A filter can intercept the outgoing response, compress the HTML/JSON data

•

•

using GZIP, and drastically reduce network bandwidth usage.
Input Validation & Sanitization: Inspecting incoming request parameters and stripping out
malicious HTML/SQL tags to prevent XSS and SQL Injection attacks globally.
Localization & Encoding: A filter can universally set the character encoding
(request.setCharacterEncoding("UTF-8")) for all incoming requests, fixing gibberish text issues.

32. Explain how servlets interact with databases.

Servlets interact with databases to provide dynamic content in Java EE applications. This interaction is
typically achieved through JDBC or connection pooling. Proper integration ensures data-driven
functionality while maintaining performance.
•

Initialization (init): Database drivers are usually loaded, and Connection Pools (via JNDI
DataSources) are established within the Servlet's init() method so they are ready when requests
arrive.

•  Processing (doGet/doPost): Inside the request handler, the Servlet borrows a Connection from the

pool.

•  Execution: It creates a PreparedStatement, binds parameters retrieved from the
HttpServletRequest, and executes the query (executeQuery or executeUpdate).

•  Data Translation: The Servlet extracts data from the JDBC ResultSet and translates it into Java

Objects (Model/JavaBeans) to be forwarded to a JSP.

•  Resource Cleanup: Finally, within a finally block or try-with-resources, the Servlet closes the

ResultSet and PreparedStatement, and returns the Connection back to the pool.

UNIT – V : JSP & Servlet (MVC)
33. Explain end-to-end execution flow of MVC web application.

MVC (Model-View-Controller) is a design pattern widely used in Java EE to separate concerns in web
applications. The end-to-end flow starts from client request and ends at dynamic response generation.
Servlet acts as controller, JSP as view and JavaBeans as model.
•  1. Request (Client -> Controller): The user submits a form or clicks a link. The request goes to the

Servlet (Controller).

•  2. Processing (Controller -> Model): The Servlet reads the parameters, decides what action to
take, and invokes the appropriate Java class (Model) to apply business logic or fetch database
records.

•  3. State Update (Model -> Controller): The Model executes the logic and returns data (e.g., an

ArrayList of User objects) back to the Servlet.

•  4. Forwarding (Controller -> View): The Servlet attaches this data to the request scope

(request.setAttribute()) and uses RequestDispatcher to forward the request to a specific JSP
(View).

•  5. Rendering (View -> Client): The JSP extracts the data using EL/JSTL, generates the dynamic

HTML, and sends it back to the client's browser.

34. Write a note on controller design patterns in servlets.

Controller design patterns organize how servlets handle incoming requests in MVC architecture. They
help manage request processing and navigation logic centrally. The most common pattern used with
servlets is the Front Controller pattern.
•  Page Controller Pattern: You have one specific Servlet for every specific action (e.g., LoginServlet,
RegisterServlet, CartServlet). Good for small apps, but leads to too many Servlets in large apps.
•  Front Controller Pattern: A single, central Servlet (e.g., DispatcherServlet in Spring MVC) intercepts

all incoming requests for the entire application.

•  Routing Logic: The Front Controller examines the URL (e.g., /user/login vs /user/delete) and

delegates the task to smaller helper classes (Action classes).

•  Centralized Processing: Allows applying global policies—like checking security, logging, or setting

encodings—in one place before delegating the request.

•  Maintainability: Massively reduces the configuration bulk in web.xml and creates a highly

organized, scalable architecture.

35. Explain advantages of MVC in large-scale applications.

MVC architecture offers significant benefits when developing large-scale Java EE applications. It divides
the application into three independent layers. This separation becomes crucial as project size and team
strength increase.
•  Separation of Concerns: UI designers work on JSP (View), Java developers work on Servlets

(Controller), and database engineers work on DAOs (Model) without stepping on each other's toes.

•  Code Reusability: Business logic in the Model is completely decoupled from the web layer. The

same Model can be reused for a web interface, a mobile API, or a desktop app.

•  Parallel Development: Because the layers are separate, multiple teams can work on the View,

Controller, and Model simultaneously, drastically speeding up development time.

•  Ease of Maintenance: If a database table changes, only the Model is updated. The Controller and

View remain untouched, minimizing regression bugs.

•  Testability: MVC components can be tested independently. You can write unit tests for the Model

logic without needing to launch a web server or load a UI.

36. Discuss drawbacks of mixing business logic in JSP.

Mixing business logic with presentation code in JSP pages violates the MVC principle. Earlier JSP
development often embedded Java code using scriptlets. This practice creates several serious
drawbacks in application quality.

•  Spaghetti Code: Mixing HTML tags, CSS, and raw Java scriptlets (<% %>) makes the file unreadable

and incredibly difficult to maintain.

•  Breaks Role Separation: Web designers who know HTML/CSS but not Java will accidentally break

the code when trying to update the UI.

•  No Reusability: If business logic (like tax calculation) is written inside cart.jsp, it cannot be reused

by an API or another page. You have to copy-paste the code.

•  Hard to Debug: When an exception occurs in a translated JSP, the stack trace points to the auto-

generated Servlet class, making it very difficult to track down the original error line.

•  Testing Nightmare: You cannot write a simple JUnit test for logic embedded in a JSP; you must

deploy the app and use heavy browser automation tools to test it.

37. Explain best practices for JSP–Servlet integration.

Proper integration between JSP and Servlets is essential for clean MVC implementation in Java EE.
Following best practices ensures separation of concerns and improves application quality. These
practices focus on clear roles for each component.
•  Controller First: Requests should always hit a Servlet first, never a JSP directly. The Servlet handles

logic, then forwards to the JSP. JSPs should be placed in WEB-INF to enforce this.

•  No Scriptlets: Strictly avoid <% %> in JSPs. Use Expression Language (${}) and JSTL (<c:forEach>) to

read and display data.

•  Use Beans for Data Transfer: Package data retrieved from the database into JavaBeans (POJOs),

and attach those beans to the request scope before forwarding.

•  Keep View Dumb: The JSP should only contain logic related to presentation (e.g., loops to display

rows, if/else to highlight a row). It should make zero database or network calls.

•  Proper Navigation: Use RequestDispatcher.forward() when passing control within the server to a

JSP, and use response.sendRedirect() when sending the user to an entirely different flow (like after
a successful POST submission).

38. Write a note on request scope vs session scope in MVC.

In MVC architecture, data sharing between servlet controllers and JSP views is done through different
scopes. Request scope and session scope are most commonly used. Choosing the correct scope is vital
for performance and data consistency.
•  Request Scope: Data stored using request.setAttribute(). It lives only for the duration of a single

HTTP request-response cycle.

•  Request Scope Use Case: Passing specific data from a Servlet to a JSP for immediate display (e.g.,

search results, single-page error messages). Highly memory efficient.

•  Session Scope: Data stored using session.setAttribute(). It lives across multiple requests from the

same specific user until they log out or the session times out.

•  Session Scope Use Case: Storing data that needs to persist across the entire user journey (e.g.,

logged-in user profile, shopping cart contents).

•  Best Practice: Always prefer Request scope unless the data strictly needs to survive across multiple

page clicks, to prevent the server memory from bloating with unnecessary session data.

39. Explain how navigation control is handled in MVC.

Navigation control determines the next view after processing a request in MVC architecture. In servlet-
based MVC, this responsibility lies with the controller.

•  Centralized Navigation: The Controller (Servlet) dictates the flow of the application. The View does

not decide where to go next.

•  Forwarding (RequestDispatcher.forward): Used when the Servlet finishes processing and needs to

•

show a JSP. It happens purely on the server side; the URL in the browser doesn't change.
Including (RequestDispatcher.include): Used when a Servlet wants to dynamically pull in the
output of another Servlet or JSP (like including a header or footer).

•  Redirecting (response.sendRedirect): The server sends a 302 status to the browser, forcing the
browser to make a brand-new GET request to a new URL. This drops all request-scoped data.
•  Post-Redirect-Get (PRG) Pattern: A standard MVC practice where, after a successful POST request
(like submitting a form), the Controller uses a Redirect (instead of a Forward) to prevent duplicate
form submissions if the user refreshes the page.

UNIT – VI : Hibernate
40. Write a note on Hibernate bootstrapping process.

Hibernate bootstrapping is the initialization process that prepares the framework for database
operations. It involves loading configuration files and building core objects like SessionFactory.
•  Definition: Bootstrapping is the initialization process where Hibernate starts up, reads its

configuration, and builds the environment needed to connect to the DB.

•  Configuration Object: The process begins by creating a Configuration object, which parses the

hibernate.cfg.xml file to load database credentials, dialects, and mapping files.

•  ServiceRegistry: In modern Hibernate, configurations are passed to a ServiceRegistryBuilder, which

manages core services like database connections and transaction management.

•  SessionFactory Creation: The Configuration and ServiceRegistry are used to build a SessionFactory.
This is a heavy, thread-safe object that holds all the mapped SQL statements and is created only
once per application.

•  Session Opening: Finally, whenever the application needs to interact with the database, it asks the

SessionFactory to openSession(), providing a lightweight interface to execute queries.

41. Explain advantages of ORM in enterprise applications.

Object-Relational Mapping (ORM) bridges the gap between object-oriented programming and
relational databases. Hibernate is a popular ORM tool in Java EE.
•  Object-Centric: ORM (Object-Relational Mapping) allows developers to think and code strictly in

Object-Oriented terms (Classes, Objects) instead of Relational terms (Tables, Rows).

•  Database Independence: Hibernate handles the specific "Dialect" of the database. You write HQL
(Hibernate Query Language), and Hibernate translates it to Oracle, MySQL, or PostgreSQL syntax
automatically.

•  Caching: ORM frameworks provide built-in L1 and L2 caching mechanisms, significantly reducing

the number of repetitive database hits and improving performance.

•  Concurrency Management: Features like Optimistic Locking (using @Version) are built-in, making

it easy to handle scenarios where multiple users try to update the same record.

•  Rapid Development: It automatically generates database schemas from Java classes and removes
the need to write hundreds of repetitive CRUD (Create, Read, Update, Delete) SQL statements.

42. Discuss how Hibernate reduces boilerplate code.

Hibernate significantly reduces boilerplate code compared to traditional JDBC programming. It
automates repetitive database tasks through its ORM capabilities.
•  No JDBC Code: Developers no longer need to write Class.forName(),

DriverManager.getConnection(), or manage raw ResultSet loops manually.

•  Automatic Mapping: Instead of manually extracting data rs.getString("name") and creating Java

objects, Hibernate maps DB rows directly to Java POJOs via simple @Entity and @Column
annotations.

•  Built-in CRUD: Simple operations don't require writing any SQL. Saving an object is as simple as

session.save(userObj), and fetching is session.get(User.class, id).

•  Exception Handling: JDBC's checked SQLException forces massive try-catch blocks. Hibernate

wraps these into unchecked HibernateException, decluttering the code.

•  Relationship Management: Handling foreign keys and Joins requires complex SQL. Hibernate

handles this automatically via annotations like @OneToMany, fetching related data effortlessly.

43. Explain Hibernate transaction boundaries.

Transaction boundaries in Hibernate define the start and end points of a unit of work. They ensure data
consistency and integrity during database operations.
•  ACID Properties: Transactions ensure that a series of database operations either completely

succeed or completely fail (rollback), maintaining data integrity.

•  Begin Boundary: A transaction is started via Transaction tx = session.beginTransaction();. This

marks the start of the logical unit of work.

•  Commit Boundary: If all operations succeed, tx.commit() is called. This flushes the changes to the

database and makes them permanent.

•  Rollback Boundary: If an exception occurs, tx.rollback() is executed in the catch block, undoing all

operations since the transaction began.

•  Mandatory for Updates: In Hibernate, while simple Read operations can occur outside a

transaction, all Create, Update, and Delete operations must be wrapped within explicit transaction
boundaries.

44. Write a note on Hibernate session cache mechanism.

Hibernate session cache, also known as first-level cache, improves performance by reducing database
hits. It is associated with the Session object and enabled by default.
•  First-Level Cache (L1): This is the default cache associated with the Session object. It is mandatory

•

and cannot be disabled.
L1 Scope: It lives only as long as the Session is open. If you request the same object (by ID) twice
within the same session, Hibernate hits the DB the first time, and returns the cached object the
second time.

•  Second-Level Cache (L2): This is an optional cache associated with the SessionFactory object. It

•

must be explicitly configured using third-party providers (like Ehcache).
L2 Scope: It is shared across all sessions in the application. If Session A fetches a user, Session B can
retrieve that user from the L2 cache without hitting the database.

•  Query Cache: Works alongside the L2 cache to store the actual results of HQL queries, mapping

query parameters to the IDs of the entities returned.

45. Explain object-relational impedance mismatch.

Object-relational impedance mismatch refers to the fundamental differences between object-oriented
programming models and relational database models. Hibernate solves this mismatch through its ORM
capabilities.
•  Definition: It is the conceptual and technical conflict that arises when trying to map Object-

Oriented paradigms (Java) to Relational paradigms (SQL Databases).

•  Granularity Problem: In Java, you might have a User object containing an Address object. In a

•

•

database, this might just be flattened into a single Users table.
Inheritance Problem: Java heavily uses inheritance (Employee extends Person). Relational
databases have no concept of inheritance; tables cannot "extend" other tables.
Identity Problem: In Java, two objects are identical if a == b (memory address). In a DB, two rows
are identical if they share the same Primary Key.

•  Association Problem: Java represents relationships via unidirectional or bidirectional object

references. DBs represent relationships using Foreign Keys, which are inherently bidirectional via
Joins. (Hibernate solves all of these mismatches).

46. Discuss real-time advantages of using Hibernate in web applications.

Hibernate offers several practical advantages when used in Java EE web applications. It integrates
smoothly with Servlets, JSP, and MVC architecture. These benefits make it a preferred choice for
dynamic data-driven websites.
•  Development Speed: By abstracting SQL and JDBC, developers can build enterprise features in half

the time, allowing them to focus purely on business logic.

•  Easy Migration: If a company decides to migrate their web app from a costly Oracle DB to a free
PostgreSQL DB, they only change one line in hibernate.cfg.xml (the Dialect); no Java code needs
rewriting.

•  Performance Optimization: Features like Lazy Loading ensure that connected data (e.g., a user's
5,000 order history records) is only loaded into memory exactly when requested, saving massive
bandwidth.

•  Maintainability: Database tables are represented as Java Classes. When a new column is added to
a DB, you just add a single variable to the class rather than rewriting 20 different SQL queries
across the application.

•  Schema Generation: During prototyping or early development, Hibernate's hbm2ddl.auto feature
can automatically create or update the physical database tables based on your Java annotations,
skipping manual DB setup.

