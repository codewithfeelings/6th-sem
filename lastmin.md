# Java EE – Complete Study Guide (M1 to M6)

---

# 📘 MODULE 1 – Introduction to Java EE

---

## 1. What is Java EE? Explain its Architecture.

**Java EE (Java Enterprise Edition)** is a platform built on top of Java SE that provides a set of specifications, APIs, and runtime environments for developing large-scale, multi-tiered, scalable, reliable, and secure enterprise applications.

> It was later renamed **Jakarta EE** after being transferred to the Eclipse Foundation.

### 🏗️ Java EE Architecture (Multi-Tier):

```
┌──────────────────────────────────────────────────────────┐
│                    CLIENT TIER                           │
│        (Web Browser, Mobile App, Desktop GUI)            │
└─────────────────────┬────────────────────────────────────┘
                      │ HTTP Request/Response
┌─────────────────────▼────────────────────────────────────┐
│                  WEB TIER                                │
│         (Servlets, JSP, JSF, Filters)                    │
│      Handles HTTP requests, generates responses          │
└─────────────────────┬────────────────────────────────────┘
                      │ Business Logic Calls
┌─────────────────────▼────────────────────────────────────┐
│               BUSINESS TIER                              │
│         (EJB, CDI Beans, Spring Beans)                   │
│      Contains core business logic and rules              │
└─────────────────────┬────────────────────────────────────┘
                      │ Database Access
┌─────────────────────▼────────────────────────────────────┐
│               DATA / EIS TIER                            │
│     (JDBC, JPA, Hibernate, Databases, Legacy Systems)    │
│      Manages data persistence and retrieval              │
└──────────────────────────────────────────────────────────┘
```

### Key Java EE APIs:
| API | Purpose |
|-----|---------|
| Servlet / JSP | Web tier components |
| EJB | Business logic components |
| JPA / Hibernate | Database ORM |
| JDBC | Raw database connectivity |
| JNDI | Naming and directory interface |
| JMS | Messaging service |
| JAX-RS | RESTful web services |
| JSTL | Tag libraries for JSP |

---

## 2. Differentiate Between Java SE and Java EE

| Feature | Java SE | Java EE |
|--------|---------|---------|
| **Full Form** | Java Standard Edition | Java Enterprise Edition |
| **Purpose** | Desktop/standalone apps | Enterprise/web applications |
| **APIs** | Core Java APIs (Collections, IO, etc.) | Servlet, JSP, EJB, JPA, JMS, etc. |
| **Architecture** | Single-tier or two-tier | Multi-tier (3 or n-tier) |
| **Server** | JVM only (no server needed) | Requires Application/Web Server (Tomcat, JBoss) |
| **Scalability** | Limited | Highly scalable |
| **Transaction Mgmt** | Manual | Built-in (JTA) |
| **Security** | Basic | Advanced (JAAS, LDAP integration) |
| **Target** | Developers, students | Enterprise organizations |
| **Examples** | Swing apps, CLI tools | Banking systems, E-commerce |

---

## 3. What is the Role of JDBC in Web Applications?

**JDBC (Java Database Connectivity)** is a Java API that enables Java applications to interact with relational databases.

### Role in Web Applications:
- Acts as the **bridge between the application and the database**
- Allows web applications to perform **CRUD** (Create, Read, Update, Delete) operations
- Enables **dynamic content generation** by fetching real-time data from DB
- Supports **transaction management** to ensure data integrity
- Used in the **Data Tier** of multi-tier architecture

```
JSP/Servlet → JDBC API → JDBC Driver → Database
```

---

## 4. What is the Role of JSP in Web Applications?

**JSP (Java Server Pages)** is a server-side technology used to create **dynamic HTML web pages** using Java code embedded in HTML.

### Role in Web Applications:
- Serves as the **View layer** in MVC architecture
- Generates **dynamic web content** based on user requests
- Reduces the complexity of Servlets by separating **presentation from logic**
- Supports **JSP tags, EL, JSTL** for cleaner code
- Automatically compiled into Servlets by the web server

---

## 5. What is the Role of Servlets in Web Applications?

**Servlets** are Java classes that handle HTTP requests and responses on the **server side**.

### Role in Web Applications:
- Act as the **Controller** in MVC architecture
- Handle **GET, POST, PUT, DELETE** HTTP requests
- Process **form data, user input, and business logic**
- Manage **sessions, cookies, authentication**
- Forward requests to JSP or other resources
- Provide **thread-safe** request handling

---

## 6. Compare Roles of JDBC, JSP, and Servlet in a Web Application

| Feature | JDBC | JSP | Servlet |
|--------|------|-----|---------|
| **Role** | Data access | View (Presentation) | Controller (Logic) |
| **MVC Layer** | Model (Data) | View | Controller |
| **Purpose** | DB communication | Dynamic HTML generation | Request handling |
| **Language** | Pure Java + SQL | HTML + Java tags | Pure Java |
| **Output** | Data (ResultSet) | HTML page | HTTP Response |
| **Handles** | SQL queries | UI rendering | Business logic |
| **Location** | Data Tier | Web Tier | Web Tier |

### Flow in a Web App:
```
Browser → Servlet (Controller) → JDBC (Data Access) → Database
              ↓
           JSP (View) → Browser (HTML Response)
```

---

---

# 📘 MODULE 2 – JDBC (Java Database Connectivity)

---

## 1. What is JDBC? Explain its Need.

**JDBC** is a Java API (part of Java SE) that provides a standard interface to connect and execute queries on relational databases.

- Defined in the package: `java.sql` and `javax.sql`
- Provides classes and interfaces to interact with any relational database

### Need for JDBC:
- Before JDBC, each database required its **own proprietary API**
- JDBC provides a **unified, database-independent** interface
- Enables **portability** – same code works with different databases
- Allows **dynamic SQL execution**, result processing, and transaction control
- Required for any **data-driven web application**

---

## 2. Different Types of JDBC Drivers

```
┌─────────────────────────────────────────────────────────┐
│                JDBC DRIVER TYPES                        │
├──────────┬──────────────────────────────────────────────┤
│ Type 1   │ JDBC-ODBC Bridge Driver                      │
│ Type 2   │ Native API Driver                            │
│ Type 3   │ Network Protocol Driver (Middleware)         │
│ Type 4   │ Thin Driver (Pure Java Driver)               │
└──────────┴──────────────────────────────────────────────┘
```

### Type 1 – JDBC-ODBC Bridge Driver
- Converts JDBC calls into ODBC calls
- Requires ODBC to be installed on client machine
- **Slow, platform-dependent**
- Removed from Java 8+
- Example: `sun.jdbc.odbc.JdbcOdbcDriver`

### Type 2 – Native API Driver (Partly Java)
- Converts JDBC calls into **database-native C/C++ API calls**
- Requires native libraries on client machine
- **Faster than Type 1** but still platform-dependent
- Example: Oracle OCI Driver

### Type 3 – Network Protocol Driver (Pure Java)
- Converts JDBC calls into a **middleware-independent network protocol**
- Middleware translates calls to the DB
- **No client-side installation** required
- Used in **3-tier architecture**
- Example: IDS Server Driver

### Type 4 – Thin Driver (Pure Java Driver) ✅ Most Used
- Converts JDBC calls **directly into database protocol**
- No native libraries needed – **100% pure Java**
- **Fastest and most portable**
- Platform-independent
- Example: MySQL Connector/J, PostgreSQL JDBC Driver

| Feature | Type 1 | Type 2 | Type 3 | Type 4 |
|--------|--------|--------|--------|--------|
| Language | Java+ODBC | Java+Native | Pure Java | Pure Java |
| Speed | Slow | Medium | Medium | Fast |
| Portability | Low | Low | High | High |
| Client Install | Required | Required | Not needed | Not needed |

---

## 3. JDBC Architecture

```
┌─────────────────────────────────────────────────────────┐
│                  JAVA APPLICATION                       │
└──────────────────────┬──────────────────────────────────┘
                       │ Uses
┌──────────────────────▼──────────────────────────────────┐
│                   JDBC API                              │
│   (DriverManager, Connection, Statement, ResultSet)     │
└──────────────────────┬──────────────────────────────────┘
                       │ Loads
┌──────────────────────▼──────────────────────────────────┐
│                 JDBC DRIVER MANAGER                     │
│       Manages list of database drivers                  │
└────────┬─────────────┬──────────────┬───────────────────┘
         │             │              │
    ┌────▼───┐    ┌────▼───┐    ┌────▼───┐
    │Driver 1│    │Driver 2│    │Driver 3│   (JDBC Drivers)
    └────┬───┘    └────┬───┘    └────┬───┘
         │             │              │
    ┌────▼───┐    ┌────▼───┐    ┌────▼───┐
    │MySQL DB│    │Oracle  │    │PostGres│  (Databases)
    └────────┘    └────────┘    └────────┘
```

### Core JDBC Components:
| Component | Description |
|-----------|-------------|
| `DriverManager` | Manages and registers JDBC drivers |
| `Connection` | Represents DB connection |
| `Statement` | Executes static SQL queries |
| `PreparedStatement` | Executes pre-compiled SQL |
| `CallableStatement` | Calls stored procedures |
| `ResultSet` | Holds query result data |

---

## 4. Steps to Connect a Java Program to a Database

```java
import java.sql.*;

public class JDBCExample {
    public static void main(String[] args) {
        // Step 1: Load the Driver
        Class.forName("com.mysql.cj.jdbc.Driver");

        // Step 2: Establish Connection
        Connection con = DriverManager.getConnection(
            "jdbc:mysql://localhost:3306/mydb", "root", "password");

        // Step 3: Create Statement
        Statement stmt = con.createStatement();

        // Step 4: Execute Query
        ResultSet rs = stmt.executeQuery("SELECT * FROM students");

        // Step 5: Process ResultSet
        while (rs.next()) {
            System.out.println(rs.getInt(1) + " " + rs.getString(2));
        }

        // Step 6: Close Connection
        rs.close();
        stmt.close();
        con.close();
    }
}
```

### Steps Summary:
1. **Load Driver** – `Class.forName("driver_name")`
2. **Create Connection** – `DriverManager.getConnection(url, user, pass)`
3. **Create Statement** – `con.createStatement()`
4. **Execute Query** – `stmt.executeQuery()` or `stmt.executeUpdate()`
5. **Process ResultSet** – Iterate through `rs.next()`
6. **Close Resources** – Close `ResultSet`, `Statement`, `Connection`

---

## 5. Executing SELECT, INSERT, UPDATE, DELETE in JDBC

### SELECT Query:
```java
Statement stmt = con.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM students");
while (rs.next()) {
    System.out.println(rs.getInt("id") + " " + rs.getString("name"));
}
```

### INSERT Query:
```java
Statement stmt = con.createStatement();
int rows = stmt.executeUpdate(
    "INSERT INTO students VALUES(1, 'Alice', 85)");
System.out.println(rows + " row(s) inserted.");
```

### UPDATE Query:
```java
Statement stmt = con.createStatement();
int rows = stmt.executeUpdate(
    "UPDATE students SET marks=90 WHERE id=1");
System.out.println(rows + " row(s) updated.");
```

### DELETE Query:
```java
Statement stmt = con.createStatement();
int rows = stmt.executeUpdate(
    "DELETE FROM students WHERE id=1");
System.out.println(rows + " row(s) deleted.");
```

> `executeQuery()` → for SELECT (returns `ResultSet`)
> `executeUpdate()` → for INSERT, UPDATE, DELETE (returns int – rows affected)

---

## 6. Differentiate Between Statement and PreparedStatement

| Feature | Statement | PreparedStatement |
|--------|-----------|-------------------|
| **SQL Compilation** | Compiled each time | Compiled once, reused |
| **Performance** | Slower for repeated queries | Faster due to pre-compilation |
| **Parameters** | Hardcoded in SQL | Uses `?` placeholders |
| **SQL Injection** | Vulnerable | **Safe – prevents injection** |
| **Readability** | Less readable for complex SQL | More readable and clean |
| **Use Case** | Static queries, run once | Parameterized, repeated queries |

```java
// Statement
Statement stmt = con.createStatement();
stmt.executeQuery("SELECT * FROM students WHERE id = 1");

// PreparedStatement
PreparedStatement ps = con.prepareStatement(
    "SELECT * FROM students WHERE id = ?");
ps.setInt(1, 1);
ps.executeQuery();
```

---

## 7. What is ResultSet? Explain its Types.

**ResultSet** is an object that holds the data retrieved by a SELECT query. It maintains a **cursor** pointing to rows of the result.

### Basic Usage:
```java
ResultSet rs = stmt.executeQuery("SELECT * FROM students");
while (rs.next()) {
    int id = rs.getInt("id");
    String name = rs.getString("name");
}
```

### Types of ResultSet:

#### By Scrollability:
| Type | Constant | Description |
|------|----------|-------------|
| Forward Only | `TYPE_FORWARD_ONLY` | Cursor moves **only forward** (default) |
| Scroll Insensitive | `TYPE_SCROLL_INSENSITIVE` | Can scroll; **doesn't reflect DB changes** |
| Scroll Sensitive | `TYPE_SCROLL_SENSITIVE` | Can scroll; **reflects DB changes** |

#### By Updatability:
| Type | Constant | Description |
|------|----------|-------------|
| Read Only | `CONCUR_READ_ONLY` | Cannot update data (default) |
| Updatable | `CONCUR_UPDATABLE` | Can update rows in ResultSet |

```java
Statement stmt = con.createStatement(
    ResultSet.TYPE_SCROLL_INSENSITIVE,
    ResultSet.CONCUR_READ_ONLY);
ResultSet rs = stmt.executeQuery("SELECT * FROM students");
rs.last();     // Go to last row
rs.first();    // Go to first row
rs.absolute(3); // Go to 3rd row
```

---

## 8. What is Metadata? DatabaseMetaData and ResultSetMetaData

**Metadata** = Data about data. In JDBC, it provides **structural information** about the database or query results.

### 🔹 DatabaseMetaData
Provides information about the **database itself**.

```java
DatabaseMetaData dbMeta = con.getMetaData();
System.out.println("DB Name: " + dbMeta.getDatabaseProductName());
System.out.println("DB Version: " + dbMeta.getDatabaseProductVersion());
System.out.println("Driver: " + dbMeta.getDriverName());
System.out.println("URL: " + dbMeta.getURL());
System.out.println("User: " + dbMeta.getUserName());
```

### 🔹 ResultSetMetaData
Provides information about **columns of a ResultSet**.

```java
ResultSet rs = stmt.executeQuery("SELECT * FROM students");
ResultSetMetaData rsMeta = rs.getMetaData();
int cols = rsMeta.getColumnCount();
for (int i = 1; i <= cols; i++) {
    System.out.println("Column Name: " + rsMeta.getColumnName(i));
    System.out.println("Data Type: " + rsMeta.getColumnTypeName(i));
    System.out.println("Size: " + rsMeta.getColumnDisplaySize(i));
}
```

| Feature | DatabaseMetaData | ResultSetMetaData |
|---------|-----------------|-------------------|
| Info about | Database/Server | Query Result Columns |
| Obtained from | `con.getMetaData()` | `rs.getMetaData()` |
| Example info | DB name, version | Column names, types, count |

---

## 9. Transaction Management in JDBC

A **transaction** is a set of SQL operations that should be treated as a single unit (**ACID** properties).

### Default Behavior:
By default, JDBC uses **auto-commit mode** (each statement is committed immediately).

### Manual Transaction Control:
```java
try {
    con.setAutoCommit(false);  // Disable auto-commit

    stmt.executeUpdate("UPDATE account SET balance=balance-500 WHERE id=1");
    stmt.executeUpdate("UPDATE account SET balance=balance+500 WHERE id=2");

    con.commit();  // Commit if all statements succeed
    System.out.println("Transaction committed successfully.");

} catch (SQLException e) {
    con.rollback();  // Rollback if any statement fails
    System.out.println("Transaction rolled back.");
}
```

---

## 10. Commit, Rollback, and Savepoint

### Commit:
- Makes all changes in the current transaction **permanent**
- `con.commit();`

### Rollback:
- **Undoes** all changes since last commit or savepoint
- `con.rollback();`

### Savepoint:
- A **checkpoint** within a transaction to which you can rollback partially

```java
con.setAutoCommit(false);

stmt.executeUpdate("INSERT INTO orders VALUES(1, 'Laptop', 50000)");
Savepoint sp = con.setSavepoint("sp1");  // Create Savepoint

stmt.executeUpdate("INSERT INTO orders VALUES(2, 'Phone', 30000)");

con.rollback(sp);  // Rollback to Savepoint sp1 (only 2nd insert undone)
con.commit();      // Commit first insert only
```

| Operation | Method | Purpose |
|-----------|--------|---------|
| Commit | `con.commit()` | Save all changes permanently |
| Rollback | `con.rollback()` | Undo all uncommitted changes |
| Savepoint | `con.setSavepoint("name")` | Create a partial rollback point |
| Release Savepoint | `con.releaseSavepoint(sp)` | Remove a savepoint |

---

## 11. Batch Processing in JDBC

**Batch processing** allows multiple SQL statements to be grouped and sent to the database **in one go**, improving performance.

### Without Batch (Slow):
- Each query makes a separate DB round-trip

### With Batch (Fast):
- All queries sent at once, reducing network overhead

```java
con.setAutoCommit(false);

PreparedStatement ps = con.prepareStatement(
    "INSERT INTO students(id, name, marks) VALUES(?, ?, ?)");

// Add multiple records to batch
ps.setInt(1, 1); ps.setString(2, "Alice"); ps.setInt(3, 90);
ps.addBatch();

ps.setInt(1, 2); ps.setString(2, "Bob"); ps.setInt(3, 85);
ps.addBatch();

ps.setInt(1, 3); ps.setString(2, "Carol"); ps.setInt(3, 92);
ps.addBatch();

// Execute batch
int[] results = ps.executeBatch();
con.commit();
System.out.println("Batch executed: " + results.length + " records inserted.");
```

### Benefits:
- Reduces number of database round-trips
- Improves performance for bulk inserts/updates
- Supports transaction management over entire batch

---

## 12. SQL Injection and How PreparedStatement Prevents It

### 🔴 What is SQL Injection?
SQL Injection is a security vulnerability where malicious SQL code is **inserted into user input** to manipulate the database.

### Example of SQL Injection:
```java
// Vulnerable code using Statement
String user = "admin' OR '1'='1";
String pass = "anything";
String sql = "SELECT * FROM users WHERE user='" + user + "' AND pass='" + pass + "'";
// Resulting SQL:
// SELECT * FROM users WHERE user='admin' OR '1'='1' AND pass='anything'
// This logs in without correct password!
```

### 🟢 How PreparedStatement Prevents It:

```java
// Safe code using PreparedStatement
String user = "admin' OR '1'='1";
String pass = "anything";

PreparedStatement ps = con.prepareStatement(
    "SELECT * FROM users WHERE user=? AND pass=?");
ps.setString(1, user);  // Value treated as data, NOT SQL code
ps.setString(2, pass);
ResultSet rs = ps.executeQuery();
// SQL injection attempt fails!
```

### Why PreparedStatement is Safe:
- SQL structure is **pre-compiled** separately
- User inputs are treated as **data/parameters**, not executable SQL
- Special characters like `'`, `--`, `;` are **automatically escaped**
- The injected code is never executed as SQL

---

---

# 📘 MODULE 3 – Java Server Pages (JSP)

---

## 1. What is JSP? Explain its Advantages.

**JSP (Java Server Pages)** is a server-side web technology that allows embedding Java code inside HTML pages using special tags. JSP pages are compiled into Servlets internally by the web container.

**File extension:** `.jsp`

### Advantages of JSP:
| Advantage | Description |
|-----------|-------------|
| **Easy to write** | HTML with embedded Java – familiar to web designers |
| **Separation of concerns** | Separates UI (HTML) from business logic (Java) |
| **Automatic compilation** | JSP container auto-compiles to Servlet |
| **Implicit Objects** | Built-in objects like `request`, `response`, `session` |
| **Tag support** | Supports JSTL, Custom Tags, EL for cleaner code |
| **Platform independent** | Runs on any server supporting Java EE |
| **Session management** | Built-in session tracking |
| **Reusability** | Using JavaBeans and custom tags |

---

## 2. JSP Lifecycle

```
┌─────────────────────────────────────────────────────────────┐
│                     JSP LIFECYCLE                           │
│                                                             │
│  1. Translation   → JSP → Servlet (.java file)             │
│  2. Compilation   → Servlet → Bytecode (.class file)        │
│  3. Loading       → Class loaded into JVM                   │
│  4. Instantiation → Servlet object created                  │
│  5. Initialization → jspInit() called (once)               │
│  6. Request Processing → _jspService() called (per request) │
│  7. Destruction   → jspDestroy() called (once)             │
└─────────────────────────────────────────────────────────────┘
```

### Methods:
| Method | Called | Purpose |
|--------|--------|---------|
| `jspInit()` | Once at startup | Initialization (like `init()` in Servlet) |
| `_jspService()` | Every request | Handles each HTTP request |
| `jspDestroy()` | Once at shutdown | Cleanup (like `destroy()` in Servlet) |

---

## 3. JSP Scriptlet, Expression, and Declaration

### 🔹 Scriptlet `<% %>`
Embeds Java code inside the `_jspService()` method.
```jsp
<%
    int a = 10, b = 20;
    int sum = a + b;
    out.println("Sum = " + sum);
%>
```

### 🔹 Expression `<%= %>`
Evaluates a Java expression and outputs it as a String (no semicolon).
```jsp
<p>Current Time: <%= new java.util.Date() %></p>
<p>Sum: <%= 10 + 20 %></p>
```

### 🔹 Declaration `<%! %>`
Declares variables or methods at the **class level** (outside `_jspService()`).
```jsp
<%!
    int count = 0;
    public int square(int n) {
        return n * n;
    }
%>
<p>Square of 5: <%= square(5) %></p>
```

| Tag | Syntax | Placed In | Semicolon |
|-----|--------|-----------|-----------|
| Scriptlet | `<% %>` | `_jspService()` | Yes |
| Expression | `<%= %>` | `_jspService()` | No |
| Declaration | `<%! %>` | Class level | Yes |

---

## 4. JSP Implicit Objects (9 Total – Explain any 5)

Implicit objects are **pre-defined objects** available in every JSP page without declaration.

| Object | Type | Description |
|--------|------|-------------|
| `request` | `HttpServletRequest` | Client's HTTP request |
| `response` | `HttpServletResponse` | Server's HTTP response |
| `out` | `JspWriter` | Output stream to write to browser |
| `session` | `HttpSession` | User's session |
| `application` | `ServletContext` | Web application context |
| `config` | `ServletConfig` | Servlet configuration |
| `pageContext` | `PageContext` | Access to all other implicit objects |
| `page` | `Object` | Reference to current JSP page (`this`) |
| `exception` | `Throwable` | Exception object (in error pages only) |

### Explanation of 5 Key Objects:

#### 1. `request`
```jsp
<%
    String name = request.getParameter("username");
    out.println("Hello, " + name);
%>
```

#### 2. `response`
```jsp
<% response.sendRedirect("login.jsp"); %>
```

#### 3. `out`
```jsp
<% out.println("<h1>Welcome!</h1>"); %>
```

#### 4. `session`
```jsp
<%
    session.setAttribute("user", "Alice");
    String user = (String) session.getAttribute("user");
    out.println("Logged in as: " + user);
%>
```

#### 5. `application`
```jsp
<%
    application.setAttribute("appName", "MyApp");
    String app = (String) application.getAttribute("appName");
    out.println("App: " + app);
%>
```

---

## 5. JSP Directives

Directives provide **global information** about a JSP page to the web container. They don't produce output.

**Syntax:** `<%@ directive attribute="value" %>`

### Types of Directives:

#### 1. Page Directive `<%@ page %>`
```jsp
<%@ page language="java"
         contentType="text/html; charset=UTF-8"
         import="java.util.*"
         session="true"
         errorPage="error.jsp"
         isErrorPage="false"
         buffer="8kb" %>
```

| Attribute | Purpose |
|-----------|---------|
| `language` | Script language (usually "java") |
| `contentType` | MIME type of response |
| `import` | Java packages to import |
| `session` | Enable/disable session |
| `errorPage` | Redirect to error page on exception |
| `isErrorPage` | Mark page as error handler |

#### 2. Include Directive `<%@ include %>`
Statically includes file content at **compile time**.
```jsp
<%@ include file="header.html" %>
<h1>Main Content</h1>
<%@ include file="footer.html" %>
```

#### 3. Taglib Directive `<%@ taglib %>`
Imports a custom or standard tag library (like JSTL).
```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
```

---

## 6. JSP Action Elements (Explain any 3)

Action elements are **XML-style tags** processed at **runtime** (unlike directives processed at compile time).

**Syntax:** `<jsp:action_name attribute="value" />`

### 1. `<jsp:include>`
Dynamically includes another page at runtime.
```jsp
<jsp:include page="header.jsp">
    <jsp:param name="title" value="Home Page"/>
</jsp:include>
```

### 2. `<jsp:forward>`
Forwards the request to another resource (page/servlet). Browser URL doesn't change.
```jsp
<jsp:forward page="dashboard.jsp">
    <jsp:param name="user" value="Alice"/>
</jsp:forward>
```

### 3. `<jsp:useBean>`
Creates or accesses a JavaBean object.
```jsp
<jsp:useBean id="student" class="com.model.Student" scope="session"/>
<jsp:setProperty name="student" property="name" value="Alice"/>
<jsp:getProperty name="student" property="name"/>
```

### Comparison: `<%@ include %>` vs `<jsp:include>`

| Feature | `<%@ include %>` | `<jsp:include>` |
|---------|-----------------|-----------------|
| Processing | Compile time | Runtime |
| Type | Static | Dynamic |
| Changes reflected | Only after recompile | Immediately |

---

## 7. JavaBeans in JSP

**JavaBeans** are reusable Java classes that follow specific conventions used to represent **data model objects** in JSP.

### JavaBean Rules:
1. Must be a **public class**
2. Must have a **public no-arg constructor**
3. Properties accessed via **public getter/setter methods**
4. Should implement `Serializable`

### JavaBean Class Example:
```java
// Student.java
package com.model;
public class Student implements java.io.Serializable {
    private int id;
    private String name;
    private int marks;

    public Student() {}  // No-arg constructor

    // Getters and Setters
    public int getId() { return id; }
    public void setId(int id) { this.id = id; }
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public int getMarks() { return marks; }
    public void setMarks(int marks) { this.marks = marks; }
}
```

### Using JavaBean in JSP:
```jsp
<!-- Declare/create the bean -->
<jsp:useBean id="s" class="com.model.Student" scope="request"/>

<!-- Set properties -->
<jsp:setProperty name="s" property="id" value="1"/>
<jsp:setProperty name="s" property="name" value="Alice"/>
<jsp:setProperty name="s" property="marks" value="95"/>

<!-- Get properties -->
<p>Name: <jsp:getProperty name="s" property="name"/></p>
<p>Marks: <jsp:getProperty name="s" property="marks"/></p>
```

### Bean Scope Options:
| Scope | Description |
|-------|-------------|
| `page` | Available only in current page |
| `request` | Available in current request |
| `session` | Available for user's session |
| `application` | Available throughout app |

---

## 8. JSP Expression Language (EL)

**EL (Expression Language)** provides a simpler syntax to access data stored in JSP scopes, beans, and collections **without writing Java code**.

**Syntax:** `${expression}`

### Features of EL:
| Feature | Description |
|---------|-------------|
| **Simple syntax** | No Java code needed in HTML |
| **Auto type conversion** | Converts types automatically |
| **Null safe** | Returns empty string instead of null |
| **Scope access** | Searches page → request → session → application |
| **Arithmetic operators** | `+`, `-`, `*`, `/`, `%` |
| **Relational operators** | `==`, `!=`, `<`, `>`, `<=`, `>=` |
| **Logical operators** | `&&`, `\|\|`, `!` |
| **Ternary operator** | `${condition ? a : b}` |

### EL Examples:
```jsp
<!-- Access request parameter -->
${param.username}

<!-- Access session attribute -->
${sessionScope.user}

<!-- Access bean property -->
<jsp:useBean id="s" class="com.model.Student" scope="request"/>
Name: ${s.name}
Marks: ${s.marks}

<!-- Arithmetic -->
${10 + 20}   <!-- Output: 30 -->

<!-- Conditional -->
${s.marks >= 50 ? "Pass" : "Fail"}

<!-- Collection access -->
${myList[0]}       <!-- List index -->
${myMap["key"]}    <!-- Map key -->
```

### EL Implicit Objects:
| EL Object | Description |
|-----------|-------------|
| `param` | Request parameters |
| `paramValues` | Multiple parameter values |
| `sessionScope` | Session attributes |
| `requestScope` | Request attributes |
| `applicationScope` | Application attributes |
| `header` | HTTP request headers |
| `cookie` | Cookies |
| `pageContext` | PageContext object |

---

## 9. JSTL Core Tags

**JSTL (JavaServer Pages Standard Tag Library)** provides standard tags to avoid Java code in JSP.

**Include:** `<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>`

### `<c:out>` – Output Data
```jsp
<c:out value="${user.name}" default="Guest"/>
```

### `<c:set>` – Set Variable
```jsp
<c:set var="price" value="500" scope="session"/>
<c:set var="discount" value="${price * 0.1}"/>
```

### `<c:if>` – Conditional
```jsp
<c:if test="${marks >= 50}">
    <p>Result: Pass</p>
</c:if>
```

### `<c:choose>`, `<c:when>`, `<c:otherwise>` – If-Else
```jsp
<c:choose>
    <c:when test="${marks >= 90}">Grade: A</c:when>
    <c:when test="${marks >= 75}">Grade: B</c:when>
    <c:when test="${marks >= 60}">Grade: C</c:when>
    <c:otherwise>Grade: F</c:otherwise>
</c:choose>
```

### `<c:forEach>` – Loop
```jsp
<!-- Loop with list -->
<c:forEach var="student" items="${studentList}">
    <p>${student.name} - ${student.marks}</p>
</c:forEach>

<!-- Loop with counter -->
<c:forEach var="i" begin="1" end="5" step="1">
    <p>Item ${i}</p>
</c:forEach>
```

### Summary of Core Tags:
| Tag | Purpose |
|-----|---------|
| `<c:out>` | Display data (with escaping) |
| `<c:set>` | Set/create a variable |
| `<c:remove>` | Remove a variable |
| `<c:if>` | Simple condition |
| `<c:choose>` | Multiple conditions (switch) |
| `<c:when>` | Condition within `<c:choose>` |
| `<c:otherwise>` | Default in `<c:choose>` |
| `<c:forEach>` | Loop over collection or range |
| `<c:forTokens>` | Loop over token string |
| `<c:import>` | Include external content |
| `<c:redirect>` | Redirect to URL |
| `<c:url>` | Build URL with encoding |

---

## 10. JSTL Function Tags

**Function tags** provide utility methods, mainly for **String manipulation**.

**Include:** `<%@ taglib uri="http://java.sun.com/jsp/jstl/functions" prefix="fn" %>`

### Commonly Used Function Tags:

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/functions" prefix="fn" %>

<!-- String length -->
${fn:length("Hello")}   <!-- Output: 5 -->

<!-- Uppercase / Lowercase -->
${fn:toUpperCase("hello")}   <!-- HELLO -->
${fn:toLowerCase("HELLO")}   <!-- hello -->

<!-- Substring -->
${fn:substring("JavaEE", 0, 4)}  <!-- Java -->

<!-- Replace -->
${fn:replace("Hello World", "World", "Java")}  <!-- Hello Java -->

<!-- Contains -->
${fn:contains("Hello World", "World")}  <!-- true -->

<!-- Starts/Ends With -->
${fn:startsWith("Hello", "He")}  <!-- true -->
${fn:endsWith("Hello", "lo")}    <!-- true -->

<!-- Split and Join -->
<c:set var="arr" value="${fn:split('a,b,c', ',')}"/>
${fn:join(arr, '-')}  <!-- a-b-c -->

<!-- Trim -->
${fn:trim("  Hello  ")}  <!-- Hello -->

<!-- Index Of -->
${fn:indexOf("Hello", "ll")}  <!-- 2 -->
```

### Summary Table:
| Function | Description |
|----------|-------------|
| `fn:length(str)` | Length of string/collection |
| `fn:toUpperCase(str)` | Convert to uppercase |
| `fn:toLowerCase(str)` | Convert to lowercase |
| `fn:substring(str, start, end)` | Extract substring |
| `fn:replace(str, old, new)` | Replace substring |
| `fn:contains(str, sub)` | Check if contains |
| `fn:startsWith(str, prefix)` | Starts with check |
| `fn:endsWith(str, suffix)` | Ends with check |
| `fn:split(str, delim)` | Split to array |
| `fn:join(arr, sep)` | Join array to string |
| `fn:trim(str)` | Remove whitespace |

---

## 11. Custom Tag Library in JSP

A **Custom Tag Library** allows developers to create their own HTML-like tags to encapsulate reusable logic.

### Steps to Create a Custom Tag:

#### Step 1: Create Tag Handler Class
```java
// HelloTag.java
package com.tags;
import javax.servlet.jsp.tagext.SimpleTagSupport;
import javax.servlet.jsp.JspWriter;
import java.io.IOException;

public class HelloTag extends SimpleTagSupport {
    private String name;  // Tag attribute

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public void doTag() throws IOException {
        JspWriter out = getJspContext().getOut();
        out.println("<h2>Hello, " + name + "! Welcome to Custom Tags.</h2>");
    }
}
```

#### Step 2: Create TLD File (Tag Library Descriptor)
```xml
<!-- WEB-INF/mytags.tld -->
<?xml version="1.0" encoding="UTF-8"?>
<taglib xmlns="http://java.sun.com/xml/ns/javaee" version="2.1">
    <tlib-version>1.0</tlib-version>
    <short-name>mytags</short-name>
    <uri>http://mycompany.com/tags</uri>

    <tag>
        <name>hello</name>
        <tag-class>com.tags.HelloTag</tag-class>
        <body-content>empty</body-content>
        <attribute>
            <name>name</name>
            <required>true</required>
            <rtexprvalue>true</rtexprvalue>
        </attribute>
    </tag>
</taglib>
```

#### Step 3: Use Custom Tag in JSP
```jsp
<%@ taglib uri="http://mycompany.com/tags" prefix="my" %>

<html>
<body>
    <my:hello name="Alice"/>
    <my:hello name="Bob"/>
</body>
</html>
```

### Output:
```
Hello, Alice! Welcome to Custom Tags.
Hello, Bob! Welcome to Custom Tags.
```

---

---

# 📘 MODULE 4 – Servlets

---

## 1. What is a Servlet? Explain its Advantages.

A **Servlet** is a Java class that runs on a web server and handles HTTP requests and responses. It extends `HttpServlet` and runs inside a **Servlet Container** (e.g., Apache Tomcat).

### Servlet Advantages:
| Advantage | Description |
|-----------|-------------|
| **Platform Independent** | Pure Java – runs on any OS |
| **Better Performance** | Thread-based (not process-based like CGI) |
| **Robust** | Java exception handling, strong typing |
| **Secure** | Uses Java Security Manager |
| **Scalable** | Handles many requests via multithreading |
| **Persistent** | Object lives in memory between requests |
| **Integration** | Works with JDBC, EJB, JSP, and all Java APIs |

---

## 2. Servlet Lifecycle

```
┌──────────────────────────────────────────────────────────────┐
│                    SERVLET LIFECYCLE                         │
│                                                              │
│  1. Loading     → Servlet class loaded by ClassLoader        │
│  2. Instantiation → Servlet object created (once)           │
│  3. init()      → Initialization (once at startup)          │
│  4. service()   → Called for EVERY request                  │
│        ├── doGet()  → Handles GET requests                  │
│        ├── doPost() → Handles POST requests                 │
│        ├── doPut(), doDelete(), etc.                        │
│  5. destroy()   → Cleanup (once at shutdown)                │
└──────────────────────────────────────────────────────────────┘
```

```java
public class MyServlet extends HttpServlet {

    @Override
    public void init() throws ServletException {
        System.out.println("Servlet Initialized");
    }

    @Override
    protected void service(HttpServletRequest req,
                           HttpServletResponse res)
            throws ServletException, IOException {
        // Determines GET/POST and calls appropriate method
        super.service(req, res);
    }

    @Override
    protected void doGet(HttpServletRequest req,
                         HttpServletResponse res)
            throws IOException {
        res.getWriter().println("GET request handled");
    }

    @Override
    protected void doPost(HttpServletRequest req,
                          HttpServletResponse res)
            throws IOException {
        res.getWriter().println("POST request handled");
    }

    @Override
    public void destroy() {
        System.out.println("Servlet Destroyed");
    }
}
```

### Lifecycle Summary:
| Phase | Method | Times Called |
|-------|--------|-------------|
| Initialization | `init()` | Once |
| Request Handling | `service()` / `doGet()` / `doPost()` | Every Request |
| Destruction | `destroy()` | Once |

---

## 3. GET and POST Request Handling in Servlets

### GET Request:
- Data sent as **URL query string**: `?name=Alice&age=25`
- **Visible in URL** – not secure for passwords
- Limited data size (~2048 chars)
- Can be **bookmarked**
- Used for: fetching pages, search queries

```java
protected void doGet(HttpServletRequest request,
                     HttpServletResponse response)
        throws IOException {
    String name = request.getParameter("name");
    response.setContentType("text/html");
    PrintWriter out = response.getWriter();
    out.println("<h1>Hello, " + name + "</h1>");
}
```

### POST Request:
- Data sent in **HTTP request body** – not visible in URL
- No size limit
- **More secure** for sensitive data (passwords, forms)
- Cannot be bookmarked
- Used for: login forms, file uploads, data submission

```java
protected void doPost(HttpServletRequest request,
                      HttpServletResponse response)
        throws IOException {
    String username = request.getParameter("username");
    String password = request.getParameter("password");
    response.setContentType("text/html");
    PrintWriter out = response.getWriter();
    if (username.equals("admin") && password.equals("1234")) {
        out.println("<h1>Login Successful</h1>");
    } else {
        out.println("<h1>Invalid Credentials</h1>");
    }
}
```

### GET vs POST Comparison:
| Feature | GET | POST |
|---------|-----|------|
| Data Location | URL (query string) | Request body |
| Visibility | Visible | Hidden |
| Data Size | Limited (~2KB) | Unlimited |
| Security | Less secure | More secure |
| Bookmarkable | Yes | No |
| Caching | Yes | No |
| Use Case | Retrieve data | Submit data |

---

## 4. Servlet Deployment Descriptor (web.xml)

**web.xml** is an XML configuration file located in `WEB-INF/` that configures servlets, mappings, filters, listeners, and other web app settings.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee" version="3.1">

    <!-- Servlet Definition -->
    <servlet>
        <servlet-name>HelloServlet</servlet-name>
        <servlet-class>com.example.HelloServlet</servlet-class>
        <load-on-startup>1</load-on-startup>
        <init-param>
            <param-name>adminEmail</param-name>
            <param-value>admin@example.com</param-value>
        </init-param>
    </servlet>

    <!-- URL Mapping -->
    <servlet-mapping>
        <servlet-name>HelloServlet</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>

    <!-- Context Parameters -->
    <context-param>
        <param-name>dbUrl</param-name>
        <param-value>jdbc:mysql://localhost/mydb</param-value>
    </context-param>

    <!-- Session Timeout (minutes) -->
    <session-config>
        <session-timeout>30</session-timeout>
    </session-config>

    <!-- Welcome File -->
    <welcome-file-list>
        <welcome-file>index.jsp</welcome-file>
    </welcome-file-list>

    <!-- Error Page -->
    <error-page>
        <error-code>404</error-code>
        <location>/error.jsp</location>
    </error-page>

</web-app>
```

### Purpose:
- Maps URL patterns to Servlet classes
- Configures init parameters
- Sets session timeout
- Defines welcome and error pages
- Configures filters and listeners

---

## 5. What is ServletContext?

**ServletContext** represents the **entire web application**. It is shared by all servlets in the application and provides application-level information.

### Obtaining ServletContext:
```java
ServletContext ctx = getServletContext();
```

### Uses of ServletContext:
```java
// 1. Set/Get global attributes (shared between servlets)
ctx.setAttribute("totalUsers", 100);
int users = (int) ctx.getAttribute("totalUsers");

// 2. Get context parameters from web.xml
String dbUrl = ctx.getInitParameter("dbUrl");

// 3. Get real path on server
String path = ctx.getRealPath("/images/logo.png");

// 4. Get resource as stream
InputStream is = ctx.getResourceAsStream("/WEB-INF/config.properties");

// 5. Logging
ctx.log("Application started!");

// 6. Get application info
String appName = ctx.getServletContextName();
String serverInfo = ctx.getServerInfo();
```

---

## 6. What is ServletConfig? How is it Different from ServletContext?

**ServletConfig** provides **per-servlet** initialization parameters defined in `web.xml` for a specific servlet.

### Obtaining ServletConfig:
```java
ServletConfig config = getServletConfig();
String email = config.getInitParameter("adminEmail");
```

### Comparison Table:
| Feature | ServletConfig | ServletContext |
|---------|--------------|----------------|
| **Scope** | Single servlet | Entire web application |
| **Instance** | One per servlet | One per application |
| **Parameters** | `<init-param>` in servlet | `<context-param>` in web.xml |
| **Shared** | No – servlet-specific | Yes – all servlets share |
| **Method** | `getServletConfig()` | `getServletContext()` |
| **Use case** | Servlet-specific config | App-wide shared data |

---

## 7. Session Management Techniques in Servlets

**Session management** is used to maintain **user state** across multiple HTTP requests (since HTTP is stateless).

### Techniques:

#### 1. HttpSession (Most Common) ✅
```java
HttpSession session = request.getSession();
session.setAttribute("username", "Alice");
session.setMaxInactiveInterval(1800); // 30 min timeout

// Retrieve
String user = (String) session.getAttribute("username");

// Invalidate
session.invalidate();
```

#### 2. Cookies
```java
Cookie c = new Cookie("user", "Alice");
c.setMaxAge(60 * 60);  // 1 hour
response.addCookie(c);

// Read cookies
Cookie[] cookies = request.getCookies();
for (Cookie cookie : cookies) {
    if (cookie.getName().equals("user"))
        out.println("User: " + cookie.getValue());
}
```

#### 3. URL Rewriting
Appends session ID to URL – used when cookies are disabled.
```java
String encodedURL = response.encodeURL("/dashboard");
out.println("<a href='" + encodedURL + "'>Dashboard</a>");
// URL: /dashboard;jsessionid=ABC123
```

#### 4. Hidden Form Fields
```html
<form action="nextPage">
    <input type="hidden" name="username" value="Alice"/>
    <input type="submit"/>
</form>
```

### Comparison:
| Technique | Storage | Persistent | Secure |
|-----------|---------|-----------|--------|
| HttpSession | Server-side | Yes (until timeout) | Most secure |
| Cookies | Client-side | Yes (until expiry) | Less secure |
| URL Rewriting | URL | No | Least secure |
| Hidden Fields | HTML form | No | Medium |

---

## 8. Cookies in Servlets

A **Cookie** is a small piece of data stored on the **client's browser** by the server to maintain state.

### Creating and Sending Cookies:
```java
protected void doPost(HttpServletRequest request,
                      HttpServletResponse response)
        throws IOException {
    // Create a cookie
    Cookie userCookie = new Cookie("username", "Alice");
    Cookie ageCookie = new Cookie("age", "25");

    // Set expiry (in seconds)
    userCookie.setMaxAge(60 * 60 * 24);  // 1 day
    ageCookie.setMaxAge(60 * 60);         // 1 hour

    // Set path
    userCookie.setPath("/");

    // Make cookie HTTPS-only (secure)
    userCookie.setSecure(true);

    // Add cookie to response
    response.addCookie(userCookie);
    response.addCookie(ageCookie);

    response.getWriter().println("Cookie set!");
}
```

### Reading Cookies:
```java
protected void doGet(HttpServletRequest request,
                     HttpServletResponse response)
        throws IOException {
    Cookie[] cookies = request.getCookies();
    PrintWriter out = response.getWriter();

    if (cookies != null) {
        for (Cookie c : cookies) {
            out.println("Name: " + c.getName() +
                        ", Value: " + c.getValue());
        }
    } else {
        out.println("No cookies found.");
    }
}
```

### Deleting a Cookie:
```java
Cookie c = new Cookie("username", "");
c.setMaxAge(0);  // Set age to 0 = delete
response.addCookie(c);
```

---

## 9. Servlet Chaining

**Servlet Chaining** is a technique where the **output of one servlet becomes the input of another** servlet. This forms a chain of servlets processing the same request.

### How it Works:
```
Request → Servlet A → Servlet B → Servlet C → Response
```

### Implementation using RequestDispatcher:
```java
// FirstServlet.java
protected void doGet(HttpServletRequest req,
                     HttpServletResponse res)
        throws IOException, ServletException {
    req.setAttribute("data", "Hello from First Servlet");

    // Chain to second servlet
    RequestDispatcher rd = req.getRequestDispatcher("/SecondServlet");
    rd.forward(req, res);  // Forward to next servlet in chain
}
```

```java
// SecondServlet.java
protected void doGet(HttpServletRequest req,
                     HttpServletResponse res)
        throws IOException {
    String data = (String) req.getAttribute("data");
    PrintWriter out = res.getWriter();
    out.println("Received from chain: " + data);
    out.println(" → Processed by Second Servlet");
}
```

---

## 10. Servlet Filters

A **Filter** is a Java class that **intercepts requests and responses** before they reach a Servlet or after the response is sent. Filters are used for **cross-cutting concerns**.

### Purpose of Filters:
- Authentication and Authorization
- Logging and Auditing
- Request/Response Compression
- Encoding conversion
- Input validation / XSS prevention
- Performance monitoring

### Filter Implementation:
```java
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class AuthFilter implements Filter {

    @Override
    public void init(FilterConfig config) throws ServletException {
        System.out.println("Filter Initialized");
    }

    @Override
    public void doFilter(ServletRequest request,
                         ServletResponse response,
                         FilterChain chain)
            throws IOException, ServletException {

        HttpServletRequest req = (HttpServletRequest) request;
        HttpServletResponse res = (HttpServletResponse) response;

        HttpSession session = req.getSession(false);

        if (session != null && session.getAttribute("user") != null) {
            chain.doFilter(request, response);  // Allow request to proceed
        } else {
            res.sendRedirect("login.jsp");  // Block and redirect
        }
    }

    @Override
    public void destroy() {
        System.out.println("Filter Destroyed");
    }
}
```

### Register Filter in web.xml:
```xml
<filter>
    <filter-name>AuthFilter</filter-name>
    <filter-class>com.filters.AuthFilter</filter-class>
</filter>
<filter-mapping>
    <filter-name>AuthFilter</filter-name>
    <url-pattern>/dashboard/*</url-pattern>
</filter-mapping>
```

### Or use Annotation:
```java
@WebFilter("/dashboard/*")
public class AuthFilter implements Filter { ... }
```

---

## 11. File Upload and Download Using Servlets

### File Upload:

#### HTML Form:
```html
<form action="UploadServlet" method="post" enctype="multipart/form-data">
    Select File: <input type="file" name="file"/>
    <input type="submit" value="Upload"/>
</form>
```

#### Upload Servlet:
```java
@WebServlet("/UploadServlet")
@MultipartConfig(
    fileSizeThreshold = 1024 * 1024,   // 1 MB
    maxFileSize = 1024 * 1024 * 10,    // 10 MB
    maxRequestSize = 1024 * 1024 * 50  // 50 MB
)
public class UploadServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request,
                          HttpServletResponse response)
            throws IOException, ServletException {

        String uploadPath = getServletContext().getRealPath("/uploads");
        File uploadDir = new File(uploadPath);
        if (!uploadDir.exists()) uploadDir.mkdir();

        Part filePart = request.getPart("file");
        String fileName = filePart.getSubmittedFileName();
        filePart.write(uploadPath + File.separator + fileName);

        response.getWriter().println("File uploaded: " + fileName);
    }
}
```

### File Download:
```java
@WebServlet("/DownloadServlet")
public class DownloadServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request,
                         HttpServletResponse response)
            throws IOException {

        String fileName = request.getParameter("file");
        String filePath = getServletContext().getRealPath("/uploads/") + fileName;

        File file = new File(filePath);
        response.setContentType("application/octet-stream");
        response.setHeader("Content-Disposition",
                           "attachment; filename=\"" + fileName + "\"");
        response.setContentLength((int) file.length());

        FileInputStream fis = new FileInputStream(file);
        OutputStream os = response.getOutputStream();
        byte[] buffer = new byte[4096];
        int bytesRead;
        while ((bytesRead = fis.read(buffer)) != -1) {
            os.write(buffer, 0, bytesRead);
        }
        fis.close();
    }
}
```

---

## 12. Request Dispatching in Servlets

**Request Dispatching** allows a servlet to **forward or include** another resource (Servlet, JSP, HTML) in processing the request.

### Types:

#### 1. Forward (`forward()`)
- Completely forwards request to another resource
- **Browser URL does not change**
- Response from second resource sent to client

```java
RequestDispatcher rd = request.getRequestDispatcher("/result.jsp");
// Pass data
request.setAttribute("message", "Hello from Servlet");
rd.forward(request, response);
```

#### 2. Include (`include()`)
- **Includes** the output of another resource in current response
- Control returns to original servlet after include
- Both resources contribute to the response

```java
RequestDispatcher rd = request.getRequestDispatcher("/header.jsp");
rd.include(request, response);
// Continue processing in current servlet...
response.getWriter().println("<p>Main Content</p>");
```

### Forward vs Include:
| Feature | `forward()` | `include()` |
|---------|------------|------------|
| Control | Transferred completely | Returns to caller |
| URL | Unchanged | Unchanged |
| Response | From target only | Both contribute |
| Use Case | MVC controller forwarding | Inserting headers/footers |

### Using `sendRedirect()` (Client-side):
```java
response.sendRedirect("login.jsp");
// Browser URL CHANGES – new HTTP request made
```

### Forward vs Redirect:
| Feature | RequestDispatcher.forward() | response.sendRedirect() |
|---------|----------------------------|------------------------|
| Request | Same request | New request |
| URL change | No | Yes |
| Data sharing | Via request attributes | Via session/URL params |
| Speed | Faster | Slower (extra round trip) |

---

---

# 📘 MODULE 5 – JSP and Servlet Integration

---

## 1. Differentiate Between JSP and Servlet

| Feature | JSP | Servlet |
|---------|-----|---------|
| **Type** | Server-side scripting | Java class |
| **Extension** | `.jsp` | `.java` |
| **Code** | HTML + Java tags | Pure Java |
| **Compilation** | Auto-compiled to Servlet | Must be compiled manually |
| **Purpose** | Presentation (View) | Business logic (Controller) |
| **Readability** | Easier for HTML designers | Harder to write HTML in Java |
| **Modification** | No recompile needed for changes | Requires recompile |
| **MVC Role** | View | Controller |
| **Tag Support** | JSTL, EL, Custom Tags | No tag support |
| **Implicit Objects** | Available by default | Must create explicitly |
| **Performance** | Slightly slower (first load) | Faster (already compiled) |

---

## 2. How JSP and Servlets Work Together

In a real web application, JSP and Servlets **complement each other**:

```
Browser
  │
  │ HTTP Request (form submit / URL)
  ▼
┌──────────────────────────────┐
│         SERVLET              │  ← Controller
│  - Receives HTTP request     │
│  - Validates input           │
│  - Calls business logic      │
│  - Interacts with DB (JDBC)  │
│  - Sets request attributes   │
│  - Forwards to JSP           │
└──────────────┬───────────────┘
               │ forward(request, response)
               ▼
┌──────────────────────────────┐
│           JSP                │  ← View
│  - Receives attributes       │
│  - Renders HTML dynamically  │
│  - Uses EL and JSTL          │
│  - Sends HTML back to client │
└──────────────────────────────┘
               │ HTML Response
               ▼
            Browser
```

### Example Workflow (Login):
1. User submits login form → POST to `LoginServlet`
2. `LoginServlet` validates credentials using JDBC
3. Sets result as request attribute: `request.setAttribute("msg", "Welcome!")`
4. Forwards to `welcome.jsp`: `rd.forward(request, response)`
5. `welcome.jsp` displays: `${msg}`

---

## 3. Model–View–Controller (MVC) Architecture

**MVC** is a design pattern that separates an application into three components:

```
┌──────────────────────────────────────────────────────────────┐
│                        MVC PATTERN                          │
│                                                              │
│  ┌─────────┐    Request     ┌─────────────┐                 │
│  │  VIEW   │ ─────────────► │ CONTROLLER  │                 │
│  │  (JSP)  │               │  (Servlet)  │                 │
│  │         │ ◄───────────── │             │                 │
│  └─────────┘    Response    └──────┬──────┘                 │
│                                    │ Calls / Updates        │
│                                    ▼                        │
│                            ┌─────────────┐                 │
│                            │    MODEL    │                 │
│                            │  (Java Bean │                 │
│                            │  + JDBC/JPA)│                 │
│                            └─────────────┘                 │
└──────────────────────────────────────────────────────────────┘
```

### Three Components:

| Component | Technology | Responsibility |
|-----------|------------|---------------|
| **Model** | JavaBean + JDBC/JPA | Data + Business logic |
| **View** | JSP + JSTL + EL | UI Presentation |
| **Controller** | Servlet | Request handling + Flow control |

### MVC Flow:
1. **Client** sends request to Servlet (Controller)
2. **Servlet** processes request, calls Model (JavaBean/JDBC)
3. **Model** interacts with database, returns data
4. **Servlet** sets data as attribute, forwards to JSP (View)
5. **JSP** displays data as HTML response to client

---

## 4. Request Forwarding Between JSP and Servlet

### From Servlet to JSP:
```java
// In Servlet
request.setAttribute("students", studentList);
RequestDispatcher rd = request.getRequestDispatcher("/students.jsp");
rd.forward(request, response);
```

```jsp
<!-- In students.jsp -->
<c:forEach var="s" items="${students}">
    <p>${s.name} - ${s.marks}</p>
</c:forEach>
```

### From JSP to Servlet:
```jsp
<!-- In JSP: Forward to Servlet -->
<jsp:forward page="/ProcessServlet">
    <jsp:param name="action" value="save"/>
</jsp:forward>
```

### From Servlet to Servlet:
```java
RequestDispatcher rd = request.getRequestDispatcher("/AnotherServlet");
rd.forward(request, response);
```

---

## 5. Role of MVC in Web Application Design

### Why MVC?
| Problem Without MVC | Solution With MVC |
|---------------------|------------------|
| Mixed presentation and logic | Clear separation of concerns |
| Hard to maintain and modify | Easy to modify individual layers |
| Code duplication | Reusable Model across views |
| Not testable | Each layer can be unit tested |
| Not scalable | Easily scalable architecture |

### Benefits:
- **Separation of Concerns** – Each layer has one responsibility
- **Maintainability** – Changes in UI don't affect business logic
- **Testability** – Model and Controller can be tested independently
- **Team Work** – Frontend and backend developers can work in parallel
- **Reusability** – Same model can serve multiple views
- **Scalability** – Layers can be scaled independently

---

---

# 📘 MODULE 6 – Hibernate Framework

---

## 1. What is Hibernate? Explain its Features.

**Hibernate** is an open-source **ORM (Object-Relational Mapping)** framework for Java that maps Java objects to database tables and vice versa. It eliminates the need for manual JDBC code.

**Developed by:** Gavin King | **Current:** JBoss / Red Hat

### Features of Hibernate:
| Feature | Description |
|---------|-------------|
| **ORM** | Maps Java classes to DB tables automatically |
| **HQL** | Object-oriented query language (like SQL but for objects) |
| **Caching** | First-level (session) and second-level cache for performance |
| **Lazy Loading** | Loads associated data only when accessed |
| **Transaction Management** | Built-in transaction support |
| **Portability** | Database-independent (supports MySQL, Oracle, PostgreSQL, etc.) |
| **Automatic DDL** | Can auto-create/update database schema |
| **Association Mapping** | Supports One-to-One, One-to-Many, Many-to-Many |
| **Criteria API** | Type-safe programmatic queries |
| **Inheritance Mapping** | Supports Java inheritance in DB tables |

---

## 2. Advantages of ORM over JDBC

| Feature | JDBC | ORM (Hibernate) |
|---------|------|----------------|
| **SQL Required** | Manual SQL writing | Auto-generated SQL |
| **Code Volume** | More boilerplate code | Less code |
| **DB Portability** | DB-specific SQL | Database-independent |
| **Object Handling** | Manual mapping | Automatic mapping |
| **Caching** | No built-in caching | Built-in first/second level cache |
| **Transaction** | Manual management | Built-in / declarative |
| **Maintenance** | Harder | Easier |
| **Inheritance** | Not supported | Fully supported |
| **Query Language** | SQL (table-based) | HQL (object-based) |
| **Lazy Loading** | Not available | Available |
| **Association** | Manual joins | Automatic (One-to-Many, etc.) |

---

## 3. Hibernate Architecture and Core Components

```
┌──────────────────────────────────────────────────────────────┐
│                  HIBERNATE ARCHITECTURE                      │
│                                                              │
│  ┌────────────┐     Uses    ┌────────────────────────  ┐     │
│  │    Java    │ ──────────► │   Hibernate API          │     │
│  │ Application│             │  (Session, SessionFactory│     │
│  └────────────┘             │   Transaction, Query)    │     │
│                             └────────────┬─────────────┘     │
│                                          │                   │
│                      ┌───────────────────┼──────────────┐    │
│                      ▼                   ▼              ▼    │
│              ┌───────────┐    ┌──────────────┐  ┌───────┐    │
│              │Hibernate  │    │  Hibernate   │  │ ORM   │    │
│              │  Config   │    │  Mapping     │  │Engine │    │
│              │(XML/.prop)│    │  (XML/Anno.) │  │       │    │
│              └───────────┘    └──────────────┘  └───┬───┘    │
│                                                     │        │
│                                              ┌──────▼──────┐ │
│                                              │    JDBC     │ │
│                                              └──────┬──────┘ │
│                                                     │        │
│                                              ┌──────▼──────┐ │
│                                              │  DATABASE   │ │
│                                              └─────────────┘ │
└──────────────────────────────────────────────────────────────┘
```

### Core Components:

| Component | Description |
|-----------|-------------|
| **SessionFactory** | Creates `Session` objects; one per database; thread-safe |
| **Session** | Short-lived object; represents DB connection; not thread-safe |
| **Transaction** | Unit of work; wraps DB operations |
| **Query** | HQL or SQL queries (`session.createQuery()`) |
| **Criteria** | Type-safe programmatic queries |
| **Configuration** | Reads hibernate.cfg.xml settings |
| **First-Level Cache** | Session-level cache (automatic) |
| **Second-Level Cache** | SessionFactory-level cache (optional, e.g., EHCache) |

---

## 4. Steps to Set Up Hibernate in a Java Application

### Step 1: Add Dependencies (Maven)
```xml
<!-- pom.xml -->
<dependency>
    <groupId>org.hibernate</groupId>
    <artifactId>hibernate-core</artifactId>
    <version>5.6.15.Final</version>
</dependency>
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.30</version>
</dependency>
```

### Step 2: Create Entity Class
```java
// Student.java
@Entity
@Table(name = "students")
public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    private String name;
    private int marks;
    // Getters and setters...
}
```

### Step 3: Create hibernate.cfg.xml
```xml
<!-- src/main/resources/hibernate.cfg.xml -->
<hibernate-configuration>
    <session-factory>
        <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/mydb</property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">password</property>
        <property name="hibernate.dialect">org.hibernate.dialect.MySQL8Dialect</property>
        <property name="hibernate.hbm2ddl.auto">update</property>
        <property name="show_sql">true</property>
        <mapping class="com.model.Student"/>
    </session-factory>
</hibernate-configuration>
```

### Step 4: Create HibernateUtil (SessionFactory)
```java
public class HibernateUtil {
    private static SessionFactory factory;

    static {
        Configuration cfg = new Configuration().configure();
        factory = cfg.buildSessionFactory();
    }

    public static SessionFactory getSessionFactory() {
        return factory;
    }
}
```

### Step 5: Use Session for DB Operations
```java
Session session = HibernateUtil.getSessionFactory().openSession();
Transaction tx = session.beginTransaction();

Student s = new Student();
s.setName("Alice");
s.setMarks(90);
session.save(s);

tx.commit();
session.close();
```

---

## 5. Mapping – Java Classes to Database Tables

**Mapping** is the process of defining the relationship between Java class fields and database table columns.

### Two Approaches:

#### 1. XML Mapping (hbm.xml)
```xml
<!-- Student.hbm.xml -->
<hibernate-mapping>
    <class name="com.model.Student" table="students">
        <id name="id" column="id">
            <generator class="native"/>
        </id>
        <property name="name" column="name"/>
        <property name="marks" column="marks"/>
    </class>
</hibernate-mapping>
```

#### 2. Annotation Mapping (Modern) ✅
```java
@Entity
@Table(name = "students")
public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "id")
    private int id;

    @Column(name = "name", length = 50, nullable = false)
    private String name;

    @Column(name = "marks")
    private int marks;
}
```

### Key Annotations:
| Annotation | Purpose |
|-----------|---------|
| `@Entity` | Marks class as Hibernate entity |
| `@Table(name="")` | Maps to specific DB table |
| `@Id` | Primary key field |
| `@GeneratedValue` | Auto-generate ID |
| `@Column(name="")` | Maps to specific DB column |
| `@Transient` | Field not persisted to DB |
| `@OneToMany` | One-to-many relationship |
| `@ManyToOne` | Many-to-one relationship |
| `@ManyToMany` | Many-to-many relationship |

---

## 6. Hibernate Configuration Using XML

```xml
<!-- hibernate.cfg.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
    "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
    "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
    <session-factory>

        <!-- Database Connection Settings -->
        <property name="hibernate.connection.driver_class">
            com.mysql.cj.jdbc.Driver
        </property>
        <property name="hibernate.connection.url">
            jdbc:mysql://localhost:3306/school_db
        </property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">root</property>

        <!-- SQL Dialect -->
        <property name="hibernate.dialect">
            org.hibernate.dialect.MySQL8Dialect
        </property>

        <!-- Schema auto generation -->
        <!-- create | create-drop | update | validate | none -->
        <property name="hibernate.hbm2ddl.auto">update</property>

        <!-- Show generated SQL in console -->
        <property name="show_sql">true</property>
        <property name="format_sql">true</property>

        <!-- Connection Pool Size -->
        <property name="hibernate.connection.pool_size">10</property>

        <!-- Mapping classes -->
        <mapping class="com.model.Student"/>
        <mapping class="com.model.Course"/>

    </session-factory>
</hibernate-configuration>
```

---

## 7. Hibernate Configuration Using Annotations

With annotations, mapping is done directly in the entity class – **no separate hbm.xml needed**.

```java
// Student.java – Complete annotated entity
package com.model;

import javax.persistence.*;
import java.util.Date;

@Entity
@Table(name = "students",
       uniqueConstraints = @UniqueConstraint(columnNames = "email"))
public class Student {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "student_id")
    private int id;

    @Column(name = "full_name", length = 100, nullable = false)
    private String name;

    @Column(name = "email", unique = true)
    private String email;

    @Column(name = "marks")
    private int marks;

    @Temporal(TemporalType.DATE)
    @Column(name = "enroll_date")
    private Date enrollDate;

    @Transient  // Not stored in DB
    private String tempCode;

    // Default constructor required
    public Student() {}

    // Getters and Setters
    public int getId() { return id; }
    public void setId(int id) { this.id = id; }
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public int getMarks() { return marks; }
    public void setMarks(int marks) { this.marks = marks; }
}
```

### In hibernate.cfg.xml – Add mapping:
```xml
<mapping class="com.model.Student"/>
```

---

## 8. Basic CRUD Operations in Hibernate

### Complete CRUD Example:
```java
public class StudentDAO {
    SessionFactory factory = HibernateUtil.getSessionFactory();

    // CREATE – INSERT
    public void save(Student s) {
        Session session = factory.openSession();
        Transaction tx = session.beginTransaction();
        session.save(s);
        tx.commit();
        session.close();
    }

    // READ – SELECT by ID
    public Student getById(int id) {
        Session session = factory.openSession();
        Student s = session.get(Student.class, id);
        session.close();
        return s;
    }

    // READ – SELECT ALL
    public List<Student> getAll() {
        Session session = factory.openSession();
        List<Student> list = session.createQuery(
            "FROM Student", Student.class).list();
        session.close();
        return list;
    }

    // UPDATE
    public void update(Student s) {
        Session session = factory.openSession();
        Transaction tx = session.beginTransaction();
        session.update(s);
        tx.commit();
        session.close();
    }

    // DELETE
    public void delete(int id) {
        Session session = factory.openSession();
        Transaction tx = session.beginTransaction();
        Student s = session.get(Student.class, id);
        if (s != null) session.delete(s);
        tx.commit();
        session.close();
    }
}
```

### Usage:
```java
StudentDAO dao = new StudentDAO();

// Create
Student s = new Student();
s.setName("Alice");
s.setMarks(90);
dao.save(s);

// Read
Student found = dao.getById(1);
System.out.println(found.getName());

// Update
found.setMarks(95);
dao.update(found);

// Delete
dao.delete(1);
```

---

## 9. Hibernate Query Language (HQL)

**HQL** is Hibernate's object-oriented query language. It is similar to SQL but operates on **Java objects and properties** instead of database tables and columns.

### Key Features:
- Database-independent
- Works with Java class names and field names
- Supports `FROM`, `WHERE`, `ORDER BY`, `GROUP BY`, `JOIN`
- Returns Java objects (not raw ResultSets)

### HQL Examples:

```java
Session session = factory.openSession();

// 1. Select all students
List<Student> all = session.createQuery("FROM Student", Student.class).list();

// 2. Select with WHERE clause
List<Student> top = session.createQuery(
    "FROM Student WHERE marks > 75", Student.class).list();

// 3. Select specific columns (returns Object[])
List result = session.createQuery(
    "SELECT s.name, s.marks FROM Student s").list();

// 4. Order By
List<Student> sorted = session.createQuery(
    "FROM Student ORDER BY marks DESC", Student.class).list();

// 5. Named Parameter
Query<Student> q = session.createQuery(
    "FROM Student WHERE name = :n", Student.class);
q.setParameter("n", "Alice");
Student alice = q.uniqueResult();

// 6. Aggregate Functions
Long count = (Long) session.createQuery(
    "SELECT COUNT(*) FROM Student").uniqueResult();
Double avg = (Double) session.createQuery(
    "SELECT AVG(marks) FROM Student").uniqueResult();

// 7. UPDATE in HQL
session.createQuery(
    "UPDATE Student SET marks = 100 WHERE id = 1").executeUpdate();

// 8. DELETE in HQL
session.createQuery(
    "DELETE FROM Student WHERE marks < 40").executeUpdate();
```

---

## 10. Differentiate Between SQL and HQL

| Feature | SQL | HQL |
|---------|-----|-----|
| **Full Form** | Structured Query Language | Hibernate Query Language |
| **Operates On** | Database tables and columns | Java objects and properties |
| **Case Sensitive** | Table/column names may vary | Class/field names are case-sensitive |
| **Portability** | Database-specific | Database-independent |
| **Return Type** | Raw rows/columns | Java objects |
| **Select All** | `SELECT * FROM students` | `FROM Student` |
| **Column Names** | DB column names | Java field names |
| **Joins** | Table joins | Object associations |
| **Syntax** | `SELECT name FROM students` | `SELECT s.name FROM Student s` |
| **OOP Support** | No | Yes (Polymorphism, Inheritance) |
| **Aggregate** | `SUM(), AVG(), COUNT()` | Same functions |
| **Result** | `ResultSet` | `List<Entity>` |

### SQL vs HQL Example:
```sql
-- SQL
SELECT * FROM students WHERE marks > 75 ORDER BY name;
```

```java
// HQL
"FROM Student WHERE marks > 75 ORDER BY name"
```

---

# 📊 Quick Reference Summary

| Module | Key Topics |
|--------|-----------|
| **M1 – Java EE** | Architecture, Java SE vs EE, Roles of JDBC/JSP/Servlet |
| **M2 – JDBC** | Drivers, Steps, Statements, ResultSet, Transactions, Batch |
| **M3 – JSP** | Lifecycle, Tags, EL, JSTL, JavaBeans, Custom Tags |
| **M4 – Servlets** | Lifecycle, GET/POST, Filters, Sessions, Cookies, Dispatching |
| **M5 – Integration** | MVC, JSP+Servlet Collaboration, Request Forwarding |
| **M6 – Hibernate** | ORM, Architecture, CRUD, HQL, Annotations, Config |

---

> 💡 **Study Tip:** Focus on **practical examples** – write and run code for JDBC connections, Servlet requests, JSP with JSTL, and Hibernate CRUD. These modules are deeply interconnected and best understood through a complete MVC mini-project.