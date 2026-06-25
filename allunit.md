# Java EE – Complete Study Guide (M1 to M6)

---

# 📘 MODULE 1 – Introduction to Java EE

---

## ✅ 5 Marks Questions

---

### 1. Differentiate between Java SE and Java EE

| Feature | Java SE (Standard Edition) | Java EE (Enterprise Edition) |
|---|---|---|
| Full Form | Java Standard Edition | Java Enterprise Edition |
| Purpose | Desktop/standalone applications | Web & enterprise applications |
| APIs | Core APIs (Collections, IO, etc.) | Servlets, JSP, EJB, JPA, etc. |
| Server | No server required | Requires Application Server (Tomcat, JBoss) |
| Scalability | Limited | Highly scalable |
| Usage | Simple programs | Large-scale distributed systems |
| Examples | Calculator, File Editor | Banking, E-commerce apps |
| Security | Basic | Advanced (JAAS, SSL) |
| Transaction | Not built-in | Built-in Transaction Management |
| Database | Via JDBC manually | JDBC + JPA + Hibernate |

**Summary:**
- Java SE = foundation platform for core Java development.
- Java EE = extends Java SE with enterprise features for server-side, web-based development.

---

### 2. What is Java EE Architecture?

Java EE Architecture is a **multi-tiered, distributed architecture** designed for developing and deploying enterprise-level web applications.

**It consists of 4 tiers:**

```
[Client Tier] → [Web Tier] → [Business Tier] → [EIS Tier]
```

| Tier | Description | Components |
|---|---|---|
| **Client Tier** | User interface layer | Browser, HTML, JS |
| **Web Tier** | Handles HTTP requests | Servlets, JSP, Filters |
| **Business Tier** | Business logic | EJB, JavaBeans |
| **EIS Tier** | Data persistence | Database, JDBC, JPA |

**Key Features:**
- Platform Independence
- Reusability of components
- Scalability and Security
- Supports distributed computing

---

### 3. Write the Role of JDBC in Web Applications

**JDBC (Java Database Connectivity)** is an API that enables Java applications to interact with relational databases.

**Role of JDBC in Web Applications:**

| Role | Description |
|---|---|
| **Database Connectivity** | Connects Java app to DB (MySQL, Oracle) |
| **Data Retrieval** | Fetch data using SELECT queries |
| **Data Manipulation** | Perform INSERT, UPDATE, DELETE |
| **Transaction Management** | Commit/Rollback operations |
| **PreparedStatement** | Prevents SQL injection |
| **Connection Pooling** | Improves performance via reuse |

**Flow:**
```
User Request → Servlet → JDBC → Database → Result → JSP (Response)
```

---

### 4. What is JSP? Mention its Uses

**JSP (JavaServer Pages)** is a server-side technology used to create dynamic web pages using Java embedded in HTML.

**JSP File Extension:** `.jsp`

**Uses of JSP:**

| Use | Description |
|---|---|
| Dynamic Web Pages | Generate HTML dynamically |
| Data Display | Display data from database |
| Form Handling | Process HTML form inputs |
| Session Management | Maintain user sessions |
| MVC View Layer | Acts as View in MVC pattern |
| Tag Libraries | Use JSTL for logic in HTML |

**Example:**
```jsp
<html>
  <body>
    Hello, <%= request.getParameter("name") %>!
  </body>
</html>
```

---

### 5. What is a Servlet? Why is it Used?

**Servlet** is a Java class that runs on a web server and handles HTTP requests and responses. It extends `HttpServlet`.

**Why Servlets are Used:**

| Reason | Description |
|---|---|
| Request Handling | Processes GET and POST requests |
| Dynamic Content | Generates dynamic HTML |
| Session Management | Tracks users via cookies/sessions |
| Business Logic | Implements application logic |
| Database Interaction | Connects to DB using JDBC |
| MVC Controller | Acts as Controller in MVC |
| Security | Handles authentication/authorization |

**Example:**
```java
public class HelloServlet extends HttpServlet {
    protected void doGet(HttpServletRequest req, HttpServletResponse res) 
                         throws IOException {
        res.getWriter().println("Hello World!");
    }
}
```

---

## ✅ 15 Marks Questions

---

### 1. Explain Java EE Architecture with Neat Diagram and Components

**Java EE Architecture** is a **multi-tier architecture** that provides a standardized way to develop enterprise-level applications.

---

#### 📊 Diagram:

```
┌─────────────────────────────────────────────────────────────────┐
│                      JAVA EE ARCHITECTURE                       │
├──────────────┬──────────────┬──────────────┬────────────────────┤
│  Client Tier │   Web Tier   │Business Tier │     EIS Tier       │
│              │              │              │                    │
│  ┌────────┐  │  ┌────────┐  │  ┌────────┐  │  ┌─────────────┐  │
│  │Browser │  │  │Servlet │  │  │  EJB   │  │  │  Database   │  │
│  │HTML/JS │◄─┼─►│  JSP   │◄─┼─►│JavaBean│◄─┼─►│  (MySQL/   │  │
│  │Applet  │  │  │Filters │  │  │  JPA   │  │  │   Oracle)  │  │
│  └────────┘  │  └────────┘  │  └────────┘  │  └─────────────┘  │
│              │   Web Server │  App Server  │   Legacy Systems  │
│              │  (Tomcat)   │  (JBoss)     │                    │
└──────────────┴──────────────┴──────────────┴────────────────────┘
                    ↕                ↕
              HTTP Protocol      RMI/IIOP
```

---

#### 📌 Components of Each Tier:

**1. Client Tier:**
- Represents the user interface
- Includes: Web Browser, HTML Pages, JavaScript, Java Applets
- Communicates with Web Tier via HTTP/HTTPS

**2. Web Tier:**
- Handles HTTP requests from client
- Components:
  - **Servlets:** Process requests and control flow
  - **JSP:** Generate dynamic HTML pages
  - **Filters:** Pre/post-process requests
  - **Listeners:** Monitor lifecycle events
- Runs on Web Container (Apache Tomcat)

**3. Business Tier:**
- Contains core business logic
- Components:
  - **EJB (Enterprise JavaBeans):** Stateless/Stateful beans for business logic
  - **JavaBeans:** Simple POJOs for data modeling
  - **JPA (Java Persistence API):** ORM for database
- Runs on Application Server (JBoss, GlassFish)

**4. EIS Tier (Enterprise Information System):**
- Handles data storage and retrieval
- Components:
  - **Relational Databases:** MySQL, Oracle, PostgreSQL
  - **JDBC:** Database connectivity
  - **Legacy Systems:** Existing enterprise systems
  - **ERP Systems:** SAP, etc.

---

#### 📌 Java EE Container Types:

| Container | Description |
|---|---|
| **Web Container** | Manages Servlets and JSP lifecycle |
| **EJB Container** | Manages EJB components |
| **Application Client Container** | Manages standalone clients |
| **Applet Container** | Manages Java Applets in browser |

---

#### 📌 Key Java EE Technologies:

| Technology | Purpose |
|---|---|
| JDBC | Database connectivity |
| Servlets | Request/Response handling |
| JSP | Dynamic web page creation |
| EJB | Business component model |
| JPA/Hibernate | ORM and data persistence |
| JNDI | Naming and directory services |
| JMS | Message-based communication |
| JAAS | Authentication and authorization |

---

#### 📌 Advantages of Java EE Architecture:
- ✅ Multi-tier separation of concerns
- ✅ Scalability and performance
- ✅ Platform independence
- ✅ Built-in security
- ✅ Transaction management
- ✅ Reusable components

---

### 2. Discuss the Roles of JDBC, JSP, and Servlets in Web Application Development

---

#### 🔷 JDBC (Java Database Connectivity):

**Definition:** API for connecting Java applications to relational databases.

**Role:**
```
Servlet/JSP → JDBC API → JDBC Driver → Database
```

| Function | Description |
|---|---|
| Connection | `DriverManager.getConnection()` |
| Query Execution | `Statement`, `PreparedStatement` |
| Result Processing | `ResultSet` |
| Transaction | `commit()`, `rollback()` |
| Batch Operations | `addBatch()`, `executeBatch()` |

**Code Example:**
```java
Connection con = DriverManager.getConnection(url, user, pass);
PreparedStatement ps = con.prepareStatement("SELECT * FROM users");
ResultSet rs = ps.executeQuery();
while(rs.next()) {
    System.out.println(rs.getString("name"));
}
```

---

#### 🔷 JSP (JavaServer Pages):

**Definition:** Server-side technology for building dynamic HTML pages using Java code.

**Role:**
| Function | Description |
|---|---|
| View Layer (MVC) | Displays data to user |
| Dynamic Content | Embeds Java in HTML |
| Form Display | Shows input forms |
| Data Presentation | Displays DB results |
| Tag Libraries | JSTL for logic |

**Code Example:**
```jsp
<%@ page import="java.util.*" %>
<html><body>
  <% String name = request.getParameter("name"); %>
  Welcome, <%= name %>!
</body></html>
```

---

#### 🔷 Servlets:

**Definition:** Java class that handles HTTP requests and responses from clients.

**Role:**
| Function | Description |
|---|---|
| Controller (MVC) | Controls flow of app |
| Request Processing | Handles GET/POST |
| Business Logic | Executes application logic |
| Session Management | Manages user sessions |
| Forward/Redirect | Routes to JSP pages |

**Code Example:**
```java
@WebServlet("/login")
public class LoginServlet extends HttpServlet {
    protected void doPost(HttpServletRequest req, 
                          HttpServletResponse res) throws Exception {
        String user = req.getParameter("username");
        // business logic
        req.setAttribute("user", user);
        req.getRequestDispatcher("welcome.jsp").forward(req, res);
    }
}
```

---

#### 🔷 How All Three Work Together:

```
User (Browser)
     ↓  HTTP Request
  Servlet (Controller)
     ↓  calls
  JDBC (Model - DB Layer)
     ↓  retrieves data
  Servlet sets attributes
     ↓  forwards
  JSP (View - displays result)
     ↓  HTTP Response
  User (Browser)
```

---

### 3. Compare Java SE and Java EE with Suitable Examples

| Aspect | Java SE | Java EE |
|---|---|---|
| **Definition** | Core Java Platform | Enterprise Extension of Java SE |
| **Purpose** | Desktop, command-line apps | Web, distributed enterprise apps |
| **Server** | Not required | Requires Tomcat/JBoss/GlassFish |
| **Core APIs** | java.lang, java.util, java.io | javax.servlet, javax.ejb, javax.persistence |
| **Database** | JDBC manually | JDBC + JPA + Hibernate |
| **Transaction** | Manual handling | Container-managed |
| **Security** | Basic file security | JAAS, SSL, Role-based |
| **Scalability** | Low | High |
| **Deployment** | JVM | Web/App Container |
| **Concurrency** | Threads manually | Container managed |

**Java SE Example:**
```java
// Simple standalone Java SE program
public class Calculator {
    public static void main(String[] args) {
        int a = 10, b = 20;
        System.out.println("Sum = " + (a+b));
    }
}
```

**Java EE Example:**
```java
// Java EE Servlet handling HTTP request
@WebServlet("/hello")
public class HelloServlet extends HttpServlet {
    public void doGet(HttpServletRequest req, 
                      HttpServletResponse res) throws IOException {
        res.getWriter().println("<h1>Hello from Java EE!</h1>");
    }
}
```

---

---

# 📘 MODULE 2 – JDBC

---

## ✅ 5 Marks Questions

---

### 1. What is JDBC?

**JDBC (Java Database Connectivity)** is a standard Java API (part of Java SE) that provides a set of interfaces and classes for connecting and executing queries with relational databases.

**Package:** `java.sql` and `javax.sql`

**Key Interfaces:**
| Interface | Description |
|---|---|
| `Driver` | Connects to database |
| `Connection` | Represents DB connection |
| `Statement` | Executes SQL queries |
| `PreparedStatement` | Executes parameterized queries |
| `ResultSet` | Holds query results |
| `CallableStatement` | Calls stored procedures |

**JDBC Architecture:**
```
Java Application → JDBC API → JDBC Driver Manager → JDBC Driver → Database
```

---

### 2. Write Different Types of JDBC Drivers

There are **4 types** of JDBC drivers:

| Type | Name | Description | Speed |
|---|---|---|---|
| **Type 1** | JDBC-ODBC Bridge Driver | Converts JDBC to ODBC calls | Slow |
| **Type 2** | Native API Driver | Uses native DB libraries | Moderate |
| **Type 3** | Network Protocol Driver | Middleware-based, DB-independent | Moderate |
| **Type 4** | Thin Driver (Pure Java) | Direct DB connection in Java | Fast ✅ |

**Type 4 (Most Used):**
```java
Class.forName("com.mysql.cj.jdbc.Driver");
Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/mydb", "root", "password");
```

---

### 3. Differentiate between Statement and PreparedStatement

| Feature | Statement | PreparedStatement |
|---|---|---|
| **Query Type** | Static SQL | Parameterized SQL |
| **Compilation** | Compiled every time | Compiled once |
| **Performance** | Slower | Faster (precompiled) |
| **SQL Injection** | Vulnerable | Safe (prevents injection) |
| **Parameters** | Hardcoded | Uses `?` placeholders |
| **Reusability** | Not reusable | Reusable with different values |
| **Use Case** | Simple queries | Dynamic queries |

**Statement Example:**
```java
Statement st = con.createStatement();
ResultSet rs = st.executeQuery("SELECT * FROM users");
```

**PreparedStatement Example:**
```java
PreparedStatement ps = con.prepareStatement(
    "SELECT * FROM users WHERE id=?");
ps.setInt(1, 101);
ResultSet rs = ps.executeQuery();
```

---

### 4. What is ResultSet?

**ResultSet** is an interface in JDBC that holds the data returned by executing a SELECT query. It acts as a cursor that points to rows of the query result.

**Types of ResultSet:**

| Type | Description |
|---|---|
| `TYPE_FORWARD_ONLY` | Default; moves forward only |
| `TYPE_SCROLL_INSENSITIVE` | Scrollable; not sensitive to changes |
| `TYPE_SCROLL_SENSITIVE` | Scrollable; reflects DB changes |

**Common Methods:**

| Method | Description |
|---|---|
| `next()` | Moves to next row |
| `getString(col)` | Gets string value |
| `getInt(col)` | Gets integer value |
| `getDouble(col)` | Gets double value |
| `first()` | Moves to first row |
| `last()` | Moves to last row |

```java
ResultSet rs = st.executeQuery("SELECT * FROM students");
while(rs.next()) {
    System.out.println(rs.getInt("id") + " " + rs.getString("name"));
}
```

---

### 5. What is Transaction Management?

**Transaction Management** in JDBC ensures a set of SQL operations are executed as a single unit. It follows **ACID properties**.

**ACID Properties:**
| Property | Meaning |
|---|---|
| **Atomicity** | All or nothing |
| **Consistency** | DB stays consistent |
| **Isolation** | Transactions don't interfere |
| **Durability** | Changes are permanent |

**Key Methods:**
| Method | Description |
|---|---|
| `setAutoCommit(false)` | Disables auto-commit |
| `commit()` | Saves all changes permanently |
| `rollback()` | Undoes all changes |
| `setSavepoint()` | Sets intermediate point |
| `rollback(savepoint)` | Rolls back to savepoint |

```java
con.setAutoCommit(false);
try {
    st.executeUpdate("UPDATE account SET bal=bal-500 WHERE id=1");
    st.executeUpdate("UPDATE account SET bal=bal+500 WHERE id=2");
    con.commit(); // Success
} catch(Exception e) {
    con.rollback(); // Failure - undo
}
```

---

## ✅ 15 Marks Questions

---

### 1. Explain JDBC Architecture and JDBC Drivers in Detail

#### 📊 JDBC Architecture Diagram:
```
┌──────────────────────────────────────────────────────┐
│                  JDBC ARCHITECTURE                   │
│                                                      │
│  ┌─────────────────────────────────────────────────┐ │
│  │            Java Application                     │ │
│  └──────────────────┬──────────────────────────────┘ │
│                     ↓                                │
│  ┌──────────────────────────────────────────────────┐ │
│  │           JDBC API (java.sql)                   │ │
│  │  Connection | Statement | ResultSet | Driver    │ │
│  └──────────────────┬──────────────────────────────┘ │
│                     ↓                                │
│  ┌──────────────────────────────────────────────────┐ │
│  │          JDBC Driver Manager                    │ │
│  └──────────────────┬──────────────────────────────┘ │
│                     ↓                                │
│  ┌──────────────────────────────────────────────────┐ │
│  │   Type1  |  Type2  |  Type3  |  Type4 Drivers  │ │
│  └──────────────────┬──────────────────────────────┘ │
│                     ↓                                │
│  ┌──────────────────────────────────────────────────┐ │
│  │          Database (MySQL/Oracle/DB2)             │ │
│  └──────────────────────────────────────────────────┘ │
└──────────────────────────────────────────────────────┘
```

---

#### 📌 JDBC Components:

**1. DriverManager:**
- Manages list of database drivers
- Establishes connection between app and DB
- `DriverManager.getConnection(url, user, pass)`

**2. Driver:**
- Interface implemented by each DB vendor
- Registered using `Class.forName()`

**3. Connection:**
- Represents session with database
- Used to create Statement objects

**4. Statement:**
- Executes SQL queries
- Types: `Statement`, `PreparedStatement`, `CallableStatement`

**5. ResultSet:**
- Stores result of SELECT query
- Provides row-by-row data access

---

#### 📌 JDBC Drivers in Detail:

**Type 1 – JDBC-ODBC Bridge Driver:**
```
Java App → JDBC API → ODBC Driver → Database
```
- Requires ODBC installed on client machine
- Platform-dependent, Slow
- Deprecated in Java 8+

**Type 2 – Native API Driver:**
```
Java App → JDBC API → Native DB Library → Database
```
- Uses native C/C++ libraries of DB
- Faster than Type 1
- Platform-dependent

**Type 3 – Network Protocol Driver:**
```
Java App → JDBC API → Middleware Server → Database
```
- Pure Java driver
- Platform-independent
- Good for internet-based apps

**Type 4 – Thin Driver (Pure Java):**
```
Java App → JDBC API → DB Protocol → Database
```
- 100% Pure Java
- Fastest and most popular
- Used with MySQL, Oracle

```java
// Type 4 MySQL Connection
Class.forName("com.mysql.cj.jdbc.Driver");
Connection con = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/mydb","root","1234");
```

---

### 2. Write a Java Program to Perform CRUD Operations Using JDBC

```java
import java.sql.*;

public class CRUDOperations {

    static final String URL  = "jdbc:mysql://localhost:3306/mydb";
    static final String USER = "root";
    static final String PASS = "1234";

    public static void main(String[] args) throws Exception {

        Class.forName("com.mysql.cj.jdbc.Driver");
        Connection con = DriverManager.getConnection(URL, USER, PASS);
        Statement st = con.createStatement();

        // ─────────────────────────────────────────
        // CREATE TABLE (Run once)
        // ─────────────────────────────────────────
        st.executeUpdate(
            "CREATE TABLE IF NOT EXISTS students(" +
            "id INT PRIMARY KEY, name VARCHAR(50), marks INT)"
        );
        System.out.println("Table created.");

        // ─────────────────────────────────────────
        // INSERT Operation
        // ─────────────────────────────────────────
        PreparedStatement psInsert = con.prepareStatement(
            "INSERT INTO students VALUES(?,?,?)");

        psInsert.setInt(1, 1);
        psInsert.setString(2, "Alice");
        psInsert.setInt(3, 90);
        psInsert.executeUpdate();

        psInsert.setInt(1, 2);
        psInsert.setString(2, "Bob");
        psInsert.setInt(3, 75);
        psInsert.executeUpdate();

        psInsert.setInt(1, 3);
        psInsert.setString(2, "Charlie");
        psInsert.setInt(3, 85);
        psInsert.executeUpdate();

        System.out.println("Records Inserted Successfully.");

        // ─────────────────────────────────────────
        // SELECT Operation
        // ─────────────────────────────────────────
        System.out.println("\n--- All Students ---");
        ResultSet rs = st.executeQuery("SELECT * FROM students");
        while(rs.next()) {
            System.out.println(
                "ID: "    + rs.getInt("id")     +
                ", Name: " + rs.getString("name") +
                ", Marks: "+ rs.getInt("marks")
            );
        }

        // ─────────────────────────────────────────
        // UPDATE Operation
        // ─────────────────────────────────────────
        PreparedStatement psUpdate = con.prepareStatement(
            "UPDATE students SET marks=? WHERE id=?");
        psUpdate.setInt(1, 95);
        psUpdate.setInt(2, 1);
        int rowsUpdated = psUpdate.executeUpdate();
        System.out.println("\nRows Updated: " + rowsUpdated);

        // Verify Update
        System.out.println("\n--- After Update ---");
        rs = st.executeQuery("SELECT * FROM students WHERE id=1");
        while(rs.next()) {
            System.out.println(
                "ID: "     + rs.getInt("id")     +
                ", Name: " + rs.getString("name") +
                ", Marks: "+ rs.getInt("marks")
            );
        }

        // ─────────────────────────────────────────
        // DELETE Operation
        // ─────────────────────────────────────────
        PreparedStatement psDelete = con.prepareStatement(
            "DELETE FROM students WHERE id=?");
        psDelete.setInt(1, 3);
        int rowsDeleted = psDelete.executeUpdate();
        System.out.println("\nRows Deleted: " + rowsDeleted);

        // Verify Delete
        System.out.println("\n--- After Delete ---");
        rs = st.executeQuery("SELECT * FROM students");
        while(rs.next()) {
            System.out.println(
                "ID: "     + rs.getInt("id")     +
                ", Name: " + rs.getString("name") +
                ", Marks: "+ rs.getInt("marks")
            );
        }

        // Close resources
        rs.close();
        st.close();
        con.close();
        System.out.println("\nConnection Closed.");
    }
}
```

**Output:**
```
Table created.
Records Inserted Successfully.

--- All Students ---
ID: 1, Name: Alice, Marks: 90
ID: 2, Name: Bob, Marks: 75
ID: 3, Name: Charlie, Marks: 85

Rows Updated: 1

--- After Update ---
ID: 1, Name: Alice, Marks: 95

Rows Deleted: 1

--- After Delete ---
ID: 1, Name: Alice, Marks: 95
ID: 2, Name: Bob, Marks: 75

Connection Closed.
```

---

### 3. Explain Commit, Rollback, and Savepoint with Examples

---

#### 🔷 Commit:
- Permanently saves all changes made during the current transaction
- Once committed, changes cannot be undone

```java
con.setAutoCommit(false); // Disable auto-commit
st.executeUpdate("UPDATE accounts SET balance=balance-1000 WHERE id=1");
st.executeUpdate("UPDATE accounts SET balance=balance+1000 WHERE id=2");
con.commit(); // Both updates saved permanently
System.out.println("Transaction Committed!");
```

---

#### 🔷 Rollback:
- Undoes all changes made since the last commit
- Used in exception handling to maintain data consistency

```java
con.setAutoCommit(false);
try {
    st.executeUpdate("UPDATE accounts SET balance=balance-1000 WHERE id=1");
    st.executeUpdate("UPDATE accounts SET balance=balance+1000 WHERE id=2");
    con.commit();
    System.out.println("Transfer successful!");
} catch(SQLException e) {
    con.rollback(); // Undo all changes
    System.out.println("Transaction failed! Rolled back.");
}
```

---

#### 🔷 Savepoint:
- Creates an intermediate checkpoint within a transaction
- Allows partial rollback to specific point

```java
con.setAutoCommit(false);

st.executeUpdate("INSERT INTO orders VALUES(1,'Laptop',50000)");
Savepoint sp1 = con.setSavepoint("SP1"); // Save point 1

st.executeUpdate("INSERT INTO orders VALUES(2,'Mouse',500)");
Savepoint sp2 = con.setSavepoint("SP2"); // Save point 2

st.executeUpdate("INSERT INTO orders VALUES(3,'Keyboard',1500)");

// Rollback to SP2 - only 3rd insert is undone
con.rollback(sp2);

con.commit(); // Commits records 1 and 2 only
System.out.println("Rolled back to SP2, committed 1 and 2.");

con.releaseSavepoint(sp1); // Release savepoint
```

---

#### 📊 Summary Table:

| Operation | Description | When to Use |
|---|---|---|
| `commit()` | Saves changes permanently | After successful operations |
| `rollback()` | Undoes all changes | On exception/failure |
| `rollback(sp)` | Undoes to savepoint | Partial undo |
| `setSavepoint()` | Creates checkpoint | Complex multi-step transaction |
| `releaseSavepoint()` | Removes savepoint | Cleanup |

---

### 4. Explain Batch Processing in JDBC with Suitable Examples

**Batch Processing** allows executing multiple SQL statements as a group (batch) in a single database call, improving performance.

---

#### 📌 Why Batch Processing?
- Reduces number of DB calls
- Faster execution for bulk operations
- Efficient for INSERT/UPDATE of large data

---

#### 📌 Methods Used:
| Method | Description |
|---|---|
| `addBatch(sql)` | Adds SQL to batch |
| `executeBatch()` | Executes all batched queries |
| `clearBatch()` | Clears all queued queries |

---

#### 📌 Example 1 – Batch using Statement:

```java
import java.sql.*;

public class BatchDemo {
    public static void main(String[] args) throws Exception {
        Connection con = DriverManager.getConnection(
            "jdbc:mysql://localhost:3306/mydb","root","1234");

        con.setAutoCommit(false); // Disable auto-commit

        Statement st = con.createStatement();

        // Add multiple queries to batch
        st.addBatch("INSERT INTO students VALUES(1,'Alice',90)");
        st.addBatch("INSERT INTO students VALUES(2,'Bob',80)");
        st.addBatch("INSERT INTO students VALUES(3,'Carol',85)");
        st.addBatch("INSERT INTO students VALUES(4,'Dave',75)");
        st.addBatch("UPDATE students SET marks=95 WHERE id=1");

        // Execute all at once
        int[] results = st.executeBatch();

        con.commit(); // Commit batch
        System.out.println("Batch executed. Total statements: " 
                            + results.length);

        con.close();
    }
}
```

---

#### 📌 Example 2 – Batch using PreparedStatement:

```java
import java.sql.*;

public class BatchPrepared {
    public static void main(String[] args) throws Exception {
        Connection con = DriverManager.getConnection(
            "jdbc:mysql://localhost:3306/mydb","root","1234");
        con.setAutoCommit(false);

        PreparedStatement ps = con.prepareStatement(
            "INSERT INTO products(id, name, price) VALUES(?,?,?)");

        // Adding 5 products in batch
        String[][] data = {
            {"1","Laptop","50000"},
            {"2","Mouse","500"},
            {"3","Keyboard","1200"},
            {"4","Monitor","15000"},
            {"5","Headphones","3000"}
        };

        for(String[] row : data) {
            ps.setInt(1, Integer.parseInt(row[0]));
            ps.setString(2, row[1]);
            ps.setDouble(3, Double.parseDouble(row[2]));
            ps.addBatch(); // Add to batch
        }

        int[] count = ps.executeBatch(); // Execute all
        con.commit();

        System.out.println("Total records inserted: " + count.length);
        con.close();
    }
}
```

---

#### 📊 Batch Processing vs Normal Processing:

| Feature | Normal Processing | Batch Processing |
|---|---|---|
| **DB Calls** | One per statement | One for all statements |
| **Performance** | Slow for bulk ops | Fast ✅ |
| **Use Case** | Few queries | Bulk INSERT/UPDATE |
| **Memory** | Less | More (stores batch) |
| **Commit** | After each statement | After all batch |

---

---

# 📘 MODULE 3 – JSP

---

## ✅ 5 Marks Questions

---

### 1. What is JSP?

**JSP (JavaServer Pages)** is a server-side web technology developed by Sun Microsystems that allows embedding Java code inside HTML pages to create dynamic web content.

**File Extension:** `.jsp`

**Features:**
| Feature | Description |
|---|---|
| Dynamic Content | Generates HTML dynamically |
| Java Integration | Embeds Java in HTML |
| Auto Compilation | Translated to Servlet by container |
| EL Support | Expression Language support |
| Tag Libraries | JSTL support |
| MVC View | Acts as View in MVC |

**Simple JSP Example:**
```jsp
<%@ page language="java" %>
<html>
<body>
    <h2>Current Time: <%= new java.util.Date() %></h2>
    <%
        String name = request.getParameter("name");
        if(name != null) {
    %>
        <h3>Hello, <%= name %>!</h3>
    <% } %>
</body>
</html>
```

---

### 2. Explain JSP Life Cycle

The JSP lifecycle describes how a JSP page is processed from loading to destruction.

---

#### 📊 JSP Life Cycle Diagram:
```
JSP File (.jsp)
      ↓
 Translation Phase
      ↓
Servlet Source (.java)
      ↓
 Compilation Phase
      ↓
Servlet Bytecode (.class)
      ↓
  jspInit()    ← Called once when loaded
      ↓
 _jspService() ← Called for every request
      ↓
 jspDestroy()  ← Called once when unloaded
```

---

#### 📌 Phases:

| Phase | Method | Description |
|---|---|---|
| **Translation** | – | JSP → Servlet source code |
| **Compilation** | – | Servlet source → Bytecode |
| **Loading** | – | Class loaded into JVM |
| **Instantiation** | – | Servlet object created |
| **Initialization** | `jspInit()` | Called once at startup |
| **Request Processing** | `_jspService()` | Called per HTTP request |
| **Destruction** | `jspDestroy()` | Called when JSP removed |

---

### 3. What are JSP Directives?

**JSP Directives** are instructions to the JSP container that affect the overall structure of the servlet generated from the JSP page.

**Syntax:** `<%@ directive attribute="value" %>`

**Three Types of Directives:**

---

**1. Page Directive:**
- Defines page-level properties

```jsp
<%@ page language="java" 
         contentType="text/html;charset=UTF-8"
         import="java.util.*"
         session="true"
         errorPage="error.jsp"
         isErrorPage="false" %>
```

**2. Include Directive:**
- Includes a file at translation time (static include)

```jsp
<%@ include file="header.jsp" %>
```

**3. Taglib Directive:**
- Declares a custom tag library or JSTL

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
```

---

### 4. What are Implicit Objects in JSP?

**Implicit Objects** are pre-defined objects in JSP that are automatically available without declaration.

| Object | Type | Description |
|---|---|---|
| `request` | `HttpServletRequest` | Holds client request data |
| `response` | `HttpServletResponse` | Holds server response |
| `out` | `JspWriter` | Writes output to browser |
| `session` | `HttpSession` | Manages user session |
| `application` | `ServletContext` | Application-wide context |
| `config` | `ServletConfig` | Servlet configuration |
| `pageContext` | `PageContext` | Access to all JSP data |
| `page` | `Object` | Current JSP page instance |
| `exception` | `Throwable` | Exception object (error pages) |

**Example:**
```jsp
<%
    String name = request.getParameter("name");  // request
    session.setAttribute("user", name);           // session
    out.println("Hello " + name);                 // out
%>
```

---

### 5. What is JSTL?

**JSTL (JavaServer Pages Standard Tag Library)** is a collection of custom tags that simplify common tasks in JSP like iteration, conditionals, and formatting.

**Taglib Declaration:**
```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
```

**JSTL Tag Libraries:**

| Library | URI Prefix | Description |
|---|---|---|
| **Core** | `c` | Variables, loops, conditionals |
| **Formatting** | `fmt` | Date, number formatting |
| **SQL** | `sql` | DB queries in JSP |
| **XML** | `x` | XML processing |
| **Functions** | `fn` | String utility functions |

**Example:**
```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html><body>
  <c:set var="name" value="Alice"/>
  <c:if test="${name == 'Alice'}">
      <p>Welcome, Admin Alice!</p>
  </c:if>
  <c:forEach var="i" begin="1" end="5">
      <p>Item: ${i}</p>
  </c:forEach>
</body></html>
```

---

## ✅ 15 Marks Questions

---

### 1. Explain JSP Life Cycle with Neat Diagram

#### 📊 Detailed JSP Lifecycle Diagram:

```
┌─────────────────────────────────────────────────────────────────┐
│                       JSP LIFE CYCLE                           │
│                                                                 │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────────────┐ │
│  │  JSP Page   │───►│ Translation │───►│ Servlet (.java)     │ │
│  │  (hello.jsp)│    │  by JSP     │    │ (hello_jsp.java)    │ │
│  └─────────────┘    │  Container  │    └──────────┬──────────┘ │
│                     └─────────────┘               ↓            │
│                                         ┌──────────────────┐   │
│                                         │  Compilation     │   │
│                                         │  (.class file)   │   │
│                                         └──────────┬───────┘   │
│                                                    ↓            │
│                                         ┌──────────────────┐   │
│                                         │  Class Loading   │   │
│                                         │  & Instantiation │   │
│                                         └──────────┬───────┘   │
│                                                    ↓            │
│                                         ┌──────────────────┐   │
│                                         │  jspInit()       │   │
│                                         │  (Once only)     │   │
│                                         └──────────┬───────┘   │
│                                                    ↓            │
│                        HTTP Request ──►  ┌──────────────────┐  │
│                        HTTP Response◄──  │  _jspService()   │  │
│                        (each request)    │  (every request) │  │
│                                         └──────────┬───────┘  │
│                                                    ↓            │
│                                         ┌──────────────────┐   │
│                                         │  jspDestroy()    │   │
│                                         │  (Once at end)   │   │
│                                         └──────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

---

#### 📌 Detailed Explanation of Each Phase:

---

**Phase 1: Translation**
- The JSP file (`.jsp`) is translated into a Servlet Java file (`.java`) by the JSP Container
- Happens when JSP is first accessed or modified
- The Servlet generated contains `_jspService()` method

---

**Phase 2: Compilation**
- The generated `.java` Servlet file is compiled into bytecode (`.class` file)
- Uses Java compiler (javac)

---

**Phase 3: Class Loading**
- The compiled class file is loaded into JVM memory

---

**Phase 4: Instantiation**
- An instance of the Servlet class is created by the container

---

**Phase 5: Initialization – `jspInit()`**
- Called only **once** after instantiation
- Used to initialize resources (DB connections, configurations)
- Override this method for custom initialization

```java
public void jspInit() {
    System.out.println("JSP Initialized!");
    // Load config, open connections
}
```

---

**Phase 6: Request Processing – `_jspService()`**
- Called **for every HTTP request**
- Contains the main JSP logic
- Handles both GET and POST requests
- Receives `HttpServletRequest` and `HttpServletResponse`

```java
public void _jspService(HttpServletRequest request, 
                         HttpServletResponse response) 
                         throws IOException, ServletException {
    // JSP page content processed here
    out.println("<h1>Hello JSP</h1>");
}
```

---

**Phase 7: Destruction – `jspDestroy()`**
- Called **once** when JSP is removed from service
- Used to release resources (close DB, close files)

```java
public void jspDestroy() {
    System.out.println("JSP Destroyed!");
    // Close connections, release resources
}
```

---

#### 📊 JSP Lifecycle Summary Table:

| Phase | Method | Times Called | Purpose |
|---|---|---|---|
| Translation | – | Once | Convert JSP to Servlet |
| Compilation | – | Once | Compile Servlet |
| Initialization | `jspInit()` | Once | Init resources |
| Request Handling | `_jspService()` | Every request | Process HTTP |
| Destruction | `jspDestroy()` | Once | Release resources |

---

### 2. Discuss JSP Syntax, Directives, Scriptlets, Expressions, and Declarations

---

#### 🔷 1. JSP Directives:
Provide global information about the JSP page.

**a) Page Directive:**
```jsp
<%@ page language="java" contentType="text/html" 
         import="java.util.*" session="true" %>
```

**b) Include Directive:**
```jsp
<%@ include file="navbar.jsp" %>
```

**c) Taglib Directive:**
```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
```

---

#### 🔷 2. Scriptlets:
Java code blocks embedded in HTML.

**Syntax:** `<% java code %>`

```jsp
<%
    int a = 10, b = 20;
    int sum = a + b;
    out.println("Sum = " + sum);
%>
```

---

#### 🔷 3. Expressions:
Used to output values directly to the browser.

**Syntax:** `<%= expression %>`

```jsp
<p>Current Date: <%= new java.util.Date() %></p>
<p>Sum: <%= 10 + 20 %></p>
<p>Name: <%= request.getParameter("name") %></p>
```
> Note: No semicolon inside `<%= ... %>`

---

#### 🔷 4. Declarations:
Used to declare variables and methods at class level (outside `_jspService()`).

**Syntax:** `<%! declaration %>`

```jsp
<%! 
    int count = 0;
    
    public int square(int n) {
        return n * n;
    }
%>

<p>Count: <%= count %></p>
<p>Square of 5: <%= square(5) %></p>
```

---

#### 🔷 5. JSP Comments:

```jsp
<!-- HTML Comment: visible in page source -->
<%-- JSP Comment: not visible in output --%>
```

---

#### 📊 Summary Table:

| Syntax | Tag | Translated To |
|---|---|---|
| **Directive** | `<%@ %>` | Class-level settings |
| **Scriptlet** | `<% %>` | Inside `_jspService()` |
| **Expression** | `<%= %>` | `out.print()` statement |
| **Declaration** | `<%! %>` | Class-level method/variable |
| **Comment** | `<%-- --%>` | Not included in output |

---

#### 🔷 Complete JSP Example:

```jsp
<%@ page language="java" contentType="text/html;charset=UTF-8" 
         import="java.util.Date" %>

<%! // Declaration
    int visitCount = 0;
    public String greet(String name) {
        return "Hello, " + name + "!";
    }
%>

<html>
<head><title>JSP Syntax Demo</title></head>
<body>
    <h1>JSP Syntax Demo</h1>

    <%-- JSP Comment - not visible in source --%>

    <% // Scriptlet
        visitCount++;
        String user = request.getParameter("name");
        if(user == null) user = "Guest";
    %>

    <p><%= greet(user) %></p>       <!-- Expression -->
    <p>Visit Count: <%= visitCount %></p>
    <p>Server Time: <%= new Date() %></p>
</body>
</html>
```

---

### 3. Explain JSP Core Tags with Examples

---

#### 📌 JSTL Core Tags Reference:

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
```

---

#### 🔷 1. `<c:set>` – Set a Variable:

```jsp
<c:set var="name" value="Alice"/>
<c:set var="age"  value="25"/>
<p>Name: ${name}, Age: ${age}</p>
```

---

#### 🔷 2. `<c:out>` – Output a Value:

```jsp
<c:set var="city" value="New York"/>
<c:out value="${city}"/>
<!-- Output: New York -->

<!-- Escaping HTML -->
<c:out value="<b>Bold</b>" escapeXml="true"/>
```

---

#### 🔷 3. `<c:if>` – Conditional Tag:

```jsp
<c:set var="marks" value="75"/>

<c:if test="${marks >= 60}">
    <p style="color:green;">✅ PASS</p>
</c:if>
<c:if test="${marks < 60}">
    <p style="color:red;">❌ FAIL</p>
</c:if>
```

---

#### 🔷 4. `<c:choose>`, `<c:when>`, `<c:otherwise>` – Switch-Case:

```jsp
<c:set var="grade" value="B"/>

<c:choose>
    <c:when test="${grade == 'A'}">
        <p>Excellent!</p>
    </c:when>
    <c:when test="${grade == 'B'}">
        <p>Very Good!</p>
    </c:when>
    <c:when test="${grade == 'C'}">
        <p>Good!</p>
    </c:when>
    <c:otherwise>
        <p>Needs Improvement</p>
    </c:otherwise>
</c:choose>
```

---

#### 🔷 5. `<c:forEach>` – Loop Tag:

**Simple Range Loop:**
```jsp
<ul>
<c:forEach var="i" begin="1" end="5" step="1">
    <li>Item ${i}</li>
</c:forEach>
</ul>
<!-- Output: Item 1, Item 2, Item 3, Item 4, Item 5 -->
```

**Iterating over a List (from Servlet):**
```java
// In Servlet:
List<String> fruits = Arrays.asList("Apple","Banana","Cherry","Mango");
request.setAttribute("fruits", fruits);
request.getRequestDispatcher("fruits.jsp").forward(req, res);
```

```jsp
<!-- In fruits.jsp: -->
<c:forEach var="fruit" items="${fruits}">
    <p>${fruit}</p>
</c:forEach>
```

**With varStatus (index access):**
```jsp
<c:forEach var="fruit" items="${fruits}" varStatus="status">
    <p>${status.index + 1}. ${fruit} 
       (First: ${status.first}, Last: ${status.last})</p>
</c:forEach>
```

---

#### 🔷 6. `<c:forTokens>` – Tokenize a String:

```jsp
<c:forTokens items="Red,Green,Blue,Yellow" delims="," var="color">
    <span style="color:${color}">${color} </span>
</c:forTokens>
```

---

#### 🔷 7. `<c:url>` – URL Construction:

```jsp
<c:url value="/profile" var="profileURL">
    <c:param name="id" value="101"/>
    <c:param name="view" value="full"/>
</c:url>
<a href="${profileURL}">View Profile</a>
<!-- Generates: /profile?id=101&view=full -->
```

---

#### 🔷 8. `<c:redirect>` – Redirect to URL:

```jsp
<c:redirect url="login.jsp"/>
<!-- Redirects browser to login.jsp -->
```

---

#### 🔷 9. `<c:remove>` – Remove a Variable:

```jsp
<c:set var="temp" value="Temporary"/>
<c:remove var="temp"/>
<!-- temp is now null -->
```

---

#### 🔷 10. `<c:import>` – Include External Content:

```jsp
<c:import url="header.jsp"/>
<c:import url="http://example.com/news"/>
```

---

#### 📊 JSTL Core Tags Summary:

| Tag | Description |
|---|---|
| `<c:set>` | Set variable value |
| `<c:out>` | Output value |
| `<c:remove>` | Remove variable |
| `<c:if>` | Conditional block |
| `<c:choose>` | Switch-case block |
| `<c:when>` | Case condition |
| `<c:otherwise>` | Default case |
| `<c:forEach>` | Loop over items/range |
| `<c:forTokens>` | Loop over tokens |
| `<c:url>` | Build URL |
| `<c:redirect>` | Redirect to URL |
| `<c:import>` | Import content |

---

### 4. Explain Expression Language (EL) and JavaBeans in JSP

---

#### 🔷 Expression Language (EL):

**Definition:** EL is a simple language used in JSP to access and display data from beans, request parameters, session attributes, and more, without using scriptlets.

**Syntax:** `${expression}`

---

**1. Accessing Request Parameters:**
```jsp
<!-- URL: page.jsp?name=Alice&age=25 -->
<p>Name: ${param.name}</p>
<p>Age:  ${param.age}</p>
```

**2. Accessing Scope Attributes:**
```jsp
<!-- Attribute set: request.setAttribute("user", "Bob") -->
<p>User: ${user}</p>
<p>Session User: ${sessionScope.user}</p>
<p>App Data: ${applicationScope.siteTitle}</p>
```

**3. Arithmetic Operators:**
```jsp
<p>Sum: ${10 + 20}</p>         <!-- 30 -->
<p>Div: ${100 / 4}</p>        <!-- 25.0 -->
<p>Mod: ${17 % 5}</p>         <!-- 2 -->
```

**4. Logical Operators:**
```jsp
<p>${10 > 5 and 3 < 8}</p>    <!-- true -->
<p>${10 == 10 or 5 > 9}</p>  <!-- true -->
<p>${not true}</p>             <!-- false -->
```

**5. Relational Operators:**
```jsp
${a == b}    ${a != b}
${a < b}     ${a > b}
${a <= b}    ${a >= b}
```

**6. Empty Operator:**
```jsp
<c:if test="${empty userList}">
    <p>No users found.</p>
</c:if>
```

---

#### 📌 EL Implicit Objects:

| Object | Description |
|---|---|
| `param` | Request parameters |
| `paramValues` | Multi-value parameters |
| `header` | Request headers |
| `cookie` | Cookie values |
| `requestScope` | Request scope attributes |
| `sessionScope` | Session scope attributes |
| `applicationScope` | Application scope attributes |
| `pageScope` | Page scope attributes |
| `initParam` | Initialization parameters |

---

#### 🔷 JavaBeans in JSP:

**Definition:** JavaBeans are reusable Java classes that follow certain conventions (private fields, public getters/setters, no-arg constructor).

**JavaBean Example:**
```java
// Student.java
public class Student {
    private int id;
    private String name;
    private double marks;

    // No-arg constructor
    public Student() {}

    // Constructor
    public Student(int id, String name, double marks) {
        this.id = id;
        this.name = name;
        this.marks = marks;
    }

    // Getters and Setters
    public int getId() { return id; }
    public void setId(int id) { this.id = id; }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public double getMarks() { return marks; }
    public void setMarks(double marks) { this.marks = marks; }
}
```

---

**Using JavaBeans in JSP with `<jsp:useBean>`:**

```jsp
<%@ page import="com.example.Student" %>

<!-- Method 1: JSP Standard Action -->
<jsp:useBean id="student" class="com.example.Student" scope="request"/>
<jsp:setProperty name="student" property="name" value="Alice"/>
<jsp:setProperty name="student" property="marks" value="92.5"/>

<p>Name:  <jsp:getProperty name="student" property="name"/></p>
<p>Marks: <jsp:getProperty name="student" property="marks"/></p>
```

---

**Using JavaBeans with EL (Recommended):**

```java
// In Servlet:
Student s = new Student(1, "Alice", 92.5);
request.setAttribute("student", s);
request.getRequestDispatcher("student.jsp").forward(req, res);
```

```jsp
<!-- In student.jsp: -->
<p>ID:    ${student.id}</p>
<p>Name:  ${student.name}</p>
<p>Marks: ${student.marks}</p>
```

---

**Iterating List of JavaBeans:**

```java
// In Servlet:
List<Student> students = new ArrayList<>();
students.add(new Student(1, "Alice", 92.5));
students.add(new Student(2, "Bob",   78.0));
students.add(new Student(3, "Carol", 85.5));
request.setAttribute("students", students);
```

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<table border="1">
    <tr><th>ID</th><th>Name</th><th>Marks</th></tr>
    <c:forEach var="s" items="${students}">
        <tr>
            <td>${s.id}</td>
            <td>${s.name}</td>
            <td>${s.marks}</td>
        </tr>
    </c:forEach>
</table>
```

---

---

# 📘 MODULE 4 – Servlet

---

## ✅ 5 Marks Questions

---

### 1. What is a Servlet?

**Servlet** is a Java class that runs on the server-side and handles client HTTP requests and generates HTTP responses. It extends `javax.servlet.http.HttpServlet`.

**Features:**
| Feature | Description |
|---|---|
| Server-side | Runs on web server/container |
| Platform independent | Pure Java |
| Protocol support | HTTP/HTTPS |
| Performance | Faster than CGI |
| Session management | Cookies, URL rewriting |
| Multithreading | Handles multiple requests |

**Servlet Hierarchy:**
```
Servlet (interface)
    └── GenericServlet (abstract)
            └── HttpServlet (abstract)
                    └── YourServlet (your class)
```

---

### 2. Explain Servlet Life Cycle

The **Servlet Life Cycle** defines the process from creation to destruction of a servlet.

**Three Main Methods:**

| Method | Called When | Times Called |
|---|---|---|
| `init()` | Servlet first loaded | Once |
| `service()` | Every HTTP request | Every request |
| `destroy()` | Servlet unloaded | Once |

```java
public class MyServlet extends HttpServlet {

    @Override
    public void init() throws ServletException {
        System.out.println("Servlet Initialized!");
    }

    @Override
    protected void service(HttpServletRequest req, 
                           HttpServletResponse res) 
                           throws IOException, ServletException {
        System.out.println("Request received!");
        doGet(req, res);
    }

    @Override
    protected void doGet(HttpServletRequest req, 
                         HttpServletResponse res) throws IOException {
        res.getWriter().println("Hello from Servlet!");
    }

    @Override
    public void destroy() {
        System.out.println("Servlet Destroyed!");
    }
}
```

---

### 3. Differentiate between GET and POST Methods

| Feature | GET | POST |
|---|---|---|
| **Data sent via** | URL (query string) | Request body |
| **Visibility** | Data visible in URL | Data hidden |
| **Security** | Less secure | More secure |
| **Data limit** | ~2048 characters | Unlimited |
| **Bookmarkable** | Yes | No |
| **Caching** | Can be cached | Not cached |
| **Idempotent** | Yes | No |
| **Use case** | Search, retrieve | Login, forms |
| **Method in Servlet** | `doGet()` | `doPost()` |

**GET Example (URL):**
```
http://example.com/search?query=java&page=1
```

**POST Example (Form):**
```html
<form action="/login" method="POST">
    <input type="password" name="pass">
</form>
```

---

### 4. What are ServletConfig and ServletContext?

---

**ServletConfig:**
- Provides configuration info to a **specific servlet**
- One per servlet
- Gets init parameters from `web.xml`

```xml
<!-- web.xml -->
<servlet>
    <servlet-name>MyServlet</servlet-name>
    <servlet-class>MyServlet</servlet-class>
    <init-param>
        <param-name>admin</param-name>
        <param-value>Alice</param-value>
    </init-param>
</servlet>
```

```java
// In Servlet
String admin = getServletConfig().getInitParameter("admin");
System.out.println("Admin: " + admin);
```

---

**ServletContext:**
- Shared across **all servlets** in the application
- Application-wide information

```xml
<!-- web.xml -->
<context-param>
    <param-name>siteName</param-name>
    <param-value>MyWebApp</param-value>
</context-param>
```

```java
// In Servlet
ServletContext ctx = getServletContext();
String site = ctx.getInitParameter("siteName");
ctx.setAttribute("visits", 100); // Shared across all servlets
```

---

| Feature | ServletConfig | ServletContext |
|---|---|---|
| **Scope** | Single Servlet | Entire Application |
| **Created by** | Container per servlet | Container per app |
| **Interface** | `ServletConfig` | `ServletContext` |
| **Access** | `getServletConfig()` | `getServletContext()` |
| **Parameters** | `<init-param>` | `<context-param>` |

---

### 5. What is a Cookie?

**Cookie** is a small text file stored on the client's browser by the server. Used for session tracking and storing user preferences.

**Cookie Flow:**
```
Server → Sends Cookie → Browser (stores it)
Browser → Sends Cookie → Server (on next request)
```

**Types:**
| Type | Description |
|---|---|
| **Session Cookie** | Lives until browser closes |
| **Persistent Cookie** | Lives until max-age expires |

**Creating & Reading Cookie:**
```java
// Servlet - Setting a Cookie
Cookie ck = new Cookie("username", "Alice");
ck.setMaxAge(60 * 60 * 24); // 1 day in seconds
response.addCookie(ck);

// Servlet - Reading a Cookie
Cookie[] cookies = request.getCookies();
if(cookies != null) {
    for(Cookie c : cookies) {
        if(c.getName().equals("username")) {
            System.out.println("User: " + c.getValue());
        }
    }
}

// Deleting a Cookie
Cookie del = new Cookie("username", "");
del.setMaxAge(0);
response.addCookie(del);
```

---

## ✅ 15 Marks Questions

---

### 1. Explain Servlet Life Cycle with Neat Diagram

#### 📊 Servlet Lifecycle Diagram:

```
┌──────────────────────────────────────────────────────────────────┐
│                    SERVLET LIFE CYCLE                            │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │                      web.xml / @WebServlet               │   │
│  │              (Servlet registered with container)         │   │
│  └──────────────────────────┬─────────────────────────────── ┘  │
│                             ↓                                    │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │            Loading & Instantiation                       │   │
│  │   Container loads class + creates Servlet instance       │   │
│  └──────────────────────────┬─────────────────────────────── ┘  │
│                             ↓ (Once)                            │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │                    init() Method                         │   │
│  │        - Called once after instantiation                 │   │
│  │        - Initialize resources (DB, configs)              │   │
│  └──────────────────────────┬─────────────────────────────── ┘  │
│                             ↓                                    │
│           ┌────────────────────────────────────┐                │
│           │  HTTP Request from Client           │                │
│           └────────────────┬───────────────────┘                │
│                            ↓  (For every request)               │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │                 service() Method                         │   │
│  │   Determines request type (GET/POST/PUT/DELETE)          │   │
│  │         ↓                    ↓                           │   │
│  │      doGet()              doPost()                       │   │
│  │   (GET request)         (POST request)                   │   │
│  └──────────────────────────┬─────────────────────────────── ┘  │
│                             ↓                                    │
│           ┌────────────────────────────────────┐                │
│           │  HTTP Response sent to Client       │                │
│           └────────────────────────────────────┘                │
│                             ↓ (Once - on shutdown)              │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │                   destroy() Method                       │   │
│  │        - Called once before servlet removed              │   │
│  │        - Release resources (close DB)                    │   │
│  └──────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────────┘
```

---

#### 📌 Complete Servlet Example with Full Lifecycle:

```java
import javax.servlet.*;
import javax.servlet.http.*;
import javax.servlet.annotation.*;
import java.io.*;
import java.sql.*;

@WebServlet("/lifecycle")
public class LifeCycleServlet extends HttpServlet {

    private Connection con;
    private int requestCount = 0;

    // ─────────────────────────────────────────
    // PHASE 1: init() - Called once
    // ─────────────────────────────────────────
    @Override
    public void init(ServletConfig config) throws ServletException {
        super.init(config);
        System.out.println(">>> init() called - Servlet Starting...");
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/mydb","root","1234");
            System.out.println(">>> Database connection established.");
        } catch(Exception e) {
            throw new ServletException("DB Connection failed", e);
        }
    }

    // ─────────────────────────────────────────
    // PHASE 2: service() - Called every request
    // ─────────────────────────────────────────
    @Override
    protected void service(HttpServletRequest req, 
                           HttpServletResponse res) 
                           throws ServletException, IOException {
        requestCount++;
        System.out.println(">>> service() called. Request #" 
                            + requestCount);
        super.service(req, res); // Delegates to doGet/doPost
    }

    // doGet handler
    @Override
    protected void doGet(HttpServletRequest req, 
                         HttpServletResponse res) 
                         throws IOException {
        res.setContentType("text/html");
        PrintWriter out = res.getWriter();
        out.println("<h2>Servlet Lifecycle Demo</h2>");
        out.println("<p>Total Requests: " + requestCount + "</p>");
    }

    // doPost handler
    @Override
    protected void doPost(HttpServletRequest req, 
                          HttpServletResponse res) 
                          throws IOException {
        res.setContentType("text/html");
        PrintWriter out = res.getWriter();
        out.println("<p>POST request received!</p>");
    }

    // ─────────────────────────────────────────
    // PHASE 3: destroy() - Called once
    // ─────────────────────────────────────────
    @Override
    public void destroy() {
        System.out.println(">>> destroy() called - Servlet Shutting down...");
        try {
            if(con != null && !con.isClosed()) {
                con.close();
                System.out.println(">>> Database connection closed.");
            }
        } catch(SQLException e) {
            e.printStackTrace();
        }
    }
}
```

---

#### 📊 Lifecycle Method Summary:

| Phase | Method | Called | Purpose | Override |
|---|---|---|---|---|
| Instantiation | Constructor | Once | Create object | No |
| Init | `init()` | Once | Setup resources | Optional |
| Request | `service()` | Every req | Route request | Optional |
| GET Request | `doGet()` | GET req | Handle GET | Yes |
| POST Request | `doPost()` | POST req | Handle POST | Yes |
| Destroy | `destroy()` | Once | Cleanup | Optional |

---

### 2. Explain Handling of HTTP Requests and Responses in Servlets

---

#### 🔷 HttpServletRequest:

**Definition:** Represents the HTTP request from the client. Contains all request data.

**Common Methods:**

| Method | Description |
|---|---|
| `getParameter(name)` | Gets form parameter |
| `getParameterValues(name)` | Gets multiple values |
| `getHeader(name)` | Gets request header |
| `getMethod()` | Returns GET/POST |
| `getSession()` | Gets session |
| `getAttribute(name)` | Gets attribute |
| `setAttribute(name, value)` | Sets attribute |
| `getRequestDispatcher(url)` | Gets dispatcher |
| `getRemoteAddr()` | Gets client IP |
| `getCookies()` | Gets cookies array |

---

#### 🔷 HttpServletResponse:

**Definition:** Represents the HTTP response to the client.

**Common Methods:**

| Method | Description |
|---|---|
| `setContentType(type)` | Sets MIME type |
| `getWriter()` | Gets PrintWriter for output |
| `sendRedirect(url)` | Redirects client |
| `setStatus(code)` | Sets HTTP status |
| `addCookie(cookie)` | Adds cookie |
| `addHeader(name, val)` | Adds response header |
| `setCharacterEncoding()` | Sets encoding |

---

#### 📌 Complete Request/Response Handling Example:

**HTML Form:**
```html
<!-- login.html -->
<form action="/LoginServlet" method="POST">
    <input type="text"     name="username" placeholder="Username">
    <input type="password" name="password" placeholder="Password">
    <input type="submit"   value="Login">
</form>
```

**Servlet:**
```java
@WebServlet("/LoginServlet")
public class LoginServlet extends HttpServlet {

    protected void doPost(HttpServletRequest req, 
                          HttpServletResponse res) 
                          throws IOException, ServletException {

        // ─── Read Request Data ───
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        String userAgent = req.getHeader("User-Agent");
        String clientIP  = req.getRemoteAddr();
        String method    = req.getMethod();

        System.out.println("Method:    " + method);
        System.out.println("Username:  " + username);
        System.out.println("Client IP: " + clientIP);
        System.out.println("Browser:   " + userAgent);

        // ─── Business Logic ───
        if(username.equals("admin") && password.equals("1234")) {
            // ─── Set Session ───
            HttpSession session = req.getSession();
            session.setAttribute("loggedUser", username);

            // ─── Set Cookie ───
            Cookie loginCookie = new Cookie("user", username);
            loginCookie.setMaxAge(3600); // 1 hour
            res.addCookie(loginCookie);

            // ─── Set Attribute for JSP ───
            req.setAttribute("message", "Login Successful!");
            req.setAttribute("user", username);

            // ─── Forward to JSP ───
            req.getRequestDispatcher("welcome.jsp")
               .forward(req, res);

        } else {
            // ─── Set Error and Redirect ───
            res.setStatus(HttpServletResponse.SC_UNAUTHORIZED);
            res.sendRedirect("login.html?error=Invalid+Credentials");
        }
    }

    // Handle direct GET access
    protected void doGet(HttpServletRequest req, 
                         HttpServletResponse res) 
                         throws IOException {
        res.setContentType("text/html");
        res.getWriter().println(
            "<h3>Please use POST method to login.</h3>");
    }
}
```

**JSP (welcome.jsp):**
```jsp
<%@ page language="java" %>
<html>
<body>
    <h2>Welcome, ${user}!</h2>
    <p>${message}</p>
    <p>Session User: ${sessionScope.loggedUser}</p>
</body>
</html>
```

---

### 3. Discuss Session Management Techniques

**Session Management** is the process of tracking a user across multiple requests since HTTP is stateless.

---

#### 🔷 Technique 1: Cookies

```java
// Set Cookie
Cookie ck = new Cookie("sessionId", "ABC123XYZ");
ck.setMaxAge(60 * 30); // 30 minutes
ck.setPath("/");
ck.setSecure(true); // HTTPS only
res.addCookie(ck);

// Read Cookie
Cookie[] cookies = req.getCookies();
if(cookies != null) {
    for(Cookie c : cookies) {
        if(c.getName().equals("sessionId")) {
            System.out.println("Session ID: " + c.getValue());
        }
    }
}

// Delete Cookie
Cookie del = new Cookie("sessionId", "");
del.setMaxAge(0);
res.addCookie(del);
```

**Pros:** Simple, widely supported
**Cons:** Stored on client, can be disabled, security risk

---

#### 🔷 Technique 2: URL Rewriting

Appends session ID to every URL.

```java
// Encode URL with session ID
String url = res.encodeURL("profile.jsp");
// Generates: profile.jsp;jsessionid=XYZ123

PrintWriter out = res.getWriter();
out.println("<a href='" + url + "'>View Profile</a>");

// Encode Redirect URL
res.sendRedirect(res.encodeRedirectURL("dashboard.jsp"));
```

**Pros:** Works even when cookies disabled
**Cons:** Session ID visible in URL, bookmarked URLs have stale IDs

---

#### 🔷 Technique 3: HttpSession (Most Popular)

```java
// ─── Create / Get Session ───
HttpSession session = req.getSession();       // Create if not exists
HttpSession session2 = req.getSession(false); // Only if exists

// ─── Set Session Attributes ───
session.setAttribute("user", "Alice");
session.setAttribute("role", "admin");
session.setAttribute("cart", new ArrayList<>());

// ─── Get Session Attributes ───
String user = (String) session.getAttribute("user");
String role = (String) session.getAttribute("role");

// ─── Session Info ───
String sessionId   = session.getId();
long creationTime  = session.getCreationTime();
long lastAccessed  = session.getLastAccessedTime();

// ─── Set Timeout (seconds) ───
session.setMaxInactiveInterval(30 * 60); // 30 minutes

// ─── Remove specific attribute ───
session.removeAttribute("cart");

// ─── Invalidate session (Logout) ───
session.invalidate();
```

**Complete Login/Logout Example:**
```java
// LoginServlet.java
@WebServlet("/login")
public class LoginServlet extends HttpServlet {
    protected void doPost(HttpServletRequest req, 
                          HttpServletResponse res) 
                          throws Exception {
        String user = req.getParameter("username");
        String pass = req.getParameter("password");
        if(user.equals("admin") && pass.equals("1234")) {
            HttpSession session = req.getSession();
            session.setAttribute("loggedIn", true);
            session.setAttribute("username", user);
            session.setMaxInactiveInterval(1800);
            res.sendRedirect("dashboard.jsp");
        } else {
            res.sendRedirect("login.jsp?error=1");
        }
    }
}

// LogoutServlet.java
@WebServlet("/logout")
public class LogoutServlet extends HttpServlet {
    protected void doGet(HttpServletRequest req, 
                         HttpServletResponse res) 
                         throws Exception {
        HttpSession session = req.getSession(false);
        if(session != null) {
            session.invalidate();
        }
        res.sendRedirect("login.jsp");
    }
}
```

---

#### 🔷 Technique 4: Hidden Form Fields

```html
<form action="/checkout" method="POST">
    <input type="hidden" name="userId" value="101">
    <input type="hidden" name="cartId" value="CART_XYZ">
    <!-- other form fields -->
    <button type="submit">Checkout</button>
</form>
```

```java
// In Servlet
String userId = req.getParameter("userId");
String cartId = req.getParameter("cartId");
```

**Pros:** Simple
**Cons:** Only works with form submission, not persistent

---

#### 📊 Session Management Comparison:

| Technique | Storage | Persistent | Works w/o Cookies | Security |
|---|---|---|---|---|
| **Cookies** | Client Browser | Yes | No | Medium |
| **URL Rewriting** | URL | No | Yes | Low |
| **HttpSession** | Server | No (RAM) | No | High |
| **Hidden Fields** | HTML Form | No | Yes | Low |

---

### 4. Explain Servlet Filters and Filter Chaining

---

#### 🔷 What is a Servlet Filter?

**Servlet Filter** is a Java class that intercepts HTTP requests and responses before/after they reach the Servlet. Used for preprocessing and postprocessing.

**Filter Interface:** `javax.servlet.Filter`

**Filter Methods:**

| Method | Description |
|---|---|
| `init(FilterConfig)` | Called once when filter is created |
| `doFilter(req, res, chain)` | Called for every request |
| `destroy()` | Called once when filter is removed |

---

#### 📌 Filter Lifecycle:

```
Client Request
      ↓
  Filter 1 (pre-processing)
      ↓
  Filter 2 (pre-processing)
      ↓
   Servlet
      ↓
  Filter 2 (post-processing)
      ↓
  Filter 1 (post-processing)
      ↓
Client Response
```

---

#### 📌 Example 1 – Authentication Filter:

```java
@WebFilter("/*") // Apply to all URLs
public class AuthFilter implements Filter {

    @Override
    public void init(FilterConfig config) throws ServletException {
        System.out.println("AuthFilter Initialized");
    }

    @Override
    public void doFilter(ServletRequest request, 
                         ServletResponse response, 
                         FilterChain chain) 
                         throws IOException, ServletException {

        HttpServletRequest  req = (HttpServletRequest)  request;
        HttpServletResponse res = (HttpServletResponse) response;

        String uri = req.getRequestURI();

        // Skip filter for login page
        if(uri.contains("login") || uri.contains("register")) {
            chain.doFilter(request, response); // Pass through
            return;
        }

        // Check session
        HttpSession session = req.getSession(false);
        if(session != null && session.getAttribute("loggedIn") != null) {
            chain.doFilter(request, response); // Authorized - pass through
        } else {
            res.sendRedirect(req.getContextPath() + "/login.jsp");
        }
    }

    @Override
    public void destroy() {
        System.out.println("AuthFilter Destroyed");
    }
}
```

---

#### 📌 Example 2 – Logging Filter:

```java
@WebFilter("/*")
public class LoggingFilter implements Filter {

    @Override
    public void doFilter(ServletRequest request, 
                         ServletResponse response, 
                         FilterChain chain) 
                         throws IOException, ServletException {

        HttpServletRequest req = (HttpServletRequest) request;

        long startTime = System.currentTimeMillis();
        System.out.println(">>> [LOG] Request: " + req.getMethod() 
                           + " " + req.getRequestURI()
                           + " | IP: " + req.getRemoteAddr());

        chain.doFilter(request, response); // Pass to next filter/servlet

        long endTime = System.currentTimeMillis();
        System.out.println(">>> [LOG] Response Time: " 
                           + (endTime - startTime) + "ms");
    }
}
```

---

#### 📌 Example 3 – Encoding Filter:

```java
@WebFilter("/*")
public class EncodingFilter implements Filter {

    @Override
    public void doFilter(ServletRequest req, ServletResponse res, 
                         FilterChain chain) 
                         throws IOException, ServletException {
        req.setCharacterEncoding("UTF-8");
        res.setCharacterEncoding("UTF-8");
        chain.doFilter(req, res);
    }
}
```

---

#### 📌 Filter Chaining Order (web.xml configuration):

```xml
<filter>
    <filter-name>EncodingFilter</filter-name>
    <filter-class>EncodingFilter</filter-class>
</filter>
<filter-mapping>
    <filter-name>EncodingFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>

<filter>
    <filter-name>LoggingFilter</filter-name>
    <filter-class>LoggingFilter</filter-class>
</filter>
<filter-mapping>
    <filter-name>LoggingFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>

<filter>
    <filter-name>AuthFilter</filter-name>
    <filter-class>AuthFilter</filter-class>
</filter>
<filter-mapping>
    <filter-name>AuthFilter</filter-name>
    <url-pattern>/secure/*</url-pattern>
</filter-mapping>
```

**Chain Flow:**
```
Request → EncodingFilter → LoggingFilter → AuthFilter → Servlet
Response ← EncodingFilter ← LoggingFilter ← AuthFilter ← Servlet
```

---

#### 📊 Common Filter Use Cases:

| Use Case | Description |
|---|---|
| Authentication | Check if user is logged in |
| Authorization | Check user permissions |
| Logging | Log request details |
| Encoding | Set character encoding |
| Compression | Compress response data |
| Caching | Add cache headers |
| XSS Prevention | Sanitize input |

---

### 5. Explain File Upload and Download in Servlet

---

#### 🔷 File Upload:

**HTML Form:**
```html
<!-- Must use multipart/form-data and POST -->
<form action="/upload" method="POST" enctype="multipart/form-data">
    <label>Choose File:</label>
    <input type="file" name="uploadFile" required>
    <br>
    <label>Description:</label>
    <input type="text" name="description">
    <br>
    <button type="submit">Upload File</button>
</form>
```

**Upload Servlet:**
```java
@WebServlet("/upload")
@MultipartConfig(
    fileSizeThreshold = 1024 * 1024,       // 1 MB
    maxFileSize       = 1024 * 1024 * 10,  // 10 MB
    maxRequestSize    = 1024 * 1024 * 50   // 50 MB
)
public class FileUploadServlet extends HttpServlet {

    private static final String UPLOAD_DIR = "uploads";

    protected void doPost(HttpServletRequest req, 
                          HttpServletResponse res) 
                          throws IOException, ServletException {

        res.setContentType("text/html");
        PrintWriter out = res.getWriter();

        // Get description field
        String desc = req.getParameter("description");

        // Get uploaded file part
        Part filePart = req.getPart("uploadFile");
        String fileName = filePart.getSubmittedFileName();
        long fileSize = filePart.getSize();
        String contentType = filePart.getContentType();

        if(fileName == null || fileName.isEmpty()) {
            out.println("<p style='color:red'>No file selected!</p>");
            return;
        }

        // Define save location
        String appPath = req.getServletContext()
                            .getRealPath("") + File.separator + UPLOAD_DIR;
        File uploadDir = new File(appPath);
        if(!uploadDir.exists()) uploadDir.mkdirs();

        String filePath = appPath + File.separator + fileName;

        // Save file to server
        filePart.write(filePath);

        out.println("<h3>File Uploaded Successfully!</h3>");
        out.println("<p>File Name: " + fileName + "</p>");
        out.println("<p>File Size: " + fileSize + " bytes</p>");
        out.println("<p>Type: " + contentType + "</p>");
        out.println("<p>Description: " + desc + "</p>");
        out.println("<a href='download?file=" + fileName + "'>Download</a>");
    }
}
```

---

#### 🔷 File Download:

```java
@WebServlet("/download")
public class FileDownloadServlet extends HttpServlet {

    protected void doGet(HttpServletRequest req, 
                         HttpServletResponse res) 
                         throws IOException {

        String fileName = req.getParameter("file");

        if(fileName == null || fileName.isEmpty()) {
            res.sendError(HttpServletResponse.SC_BAD_REQUEST, 
                          "File name is required.");
            return;
        }

        // Security: prevent directory traversal attacks
        fileName = new File(fileName).getName();

        String uploadPath = req.getServletContext().getRealPath("") 
                          + File.separator + "uploads";
        File file = new File(uploadPath + File.separator + fileName);

        if(!file.exists()) {
            res.sendError(HttpServletResponse.SC_NOT_FOUND, 
                          "File not found: " + fileName);
            return;
        }

        // Set response headers
        res.setContentType("application/octet-stream");
        res.setHeader("Content-Disposition", 
                      "attachment; filename=\"" + fileName + "\"");
        res.setContentLength((int) file.length());

        // Stream file to client
        try(FileInputStream fis = new FileInputStream(file);
            OutputStream out = res.getOutputStream()) {

            byte[] buffer = new byte[4096];
            int bytesRead;
            while((bytesRead = fis.read(buffer)) != -1) {
                out.write(buffer, 0, bytesRead);
            }
        }
    }
}
```

---

#### 📊 File Upload vs Download:

| Aspect | Upload | Download |
|---|---|---|
| **Direction** | Client → Server | Server → Client |
| **Form Method** | POST | GET (link/button) |
| **Encoding** | `multipart/form-data` | – |
| **Annotation** | `@MultipartConfig` | – |
| **API** | `Part` interface | `FileInputStream` |
| **Response Header** | – | `Content-Disposition` |
| **Content Type** | Varies | `application/octet-stream` |

---

---

# 📘 MODULE 5 – JSP + Servlet (MVC)

---

## ✅ 5 Marks Questions

---

### 1. What is MVC Architecture?

**MVC (Model-View-Controller)** is a software design pattern that separates an application into three interconnected components to promote organized code and separation of concerns.

| Component | Role | Technology in Java EE |
|---|---|---|
| **Model** | Business logic & Data | JavaBeans, JDBC, Hibernate |
| **View** | User Interface | JSP, HTML |
| **Controller** | Request handling & Routing | Servlet |

**MVC Flow:**
```
User → Controller (Servlet) → Model (JavaBean/JDBC) 
     ← View (JSP) ← Data ←────────────────────────
```

**Benefits:**
- ✅ Separation of concerns
- ✅ Easy maintenance
- ✅ Reusability
- ✅ Parallel development (UI + Logic)
- ✅ Scalability

---

### 2. What is Request Forwarding?

**Request Forwarding** is the process by which a Servlet forwards the current HTTP request and response to another resource (JSP, Servlet, or HTML) on the server side.

**Syntax:**
```java
RequestDispatcher rd = request.getRequestDispatcher("target.jsp");
rd.forward(request, response);
```

**Characteristics:**
- ✅ Happens server-side (invisible to client)
- ✅ URL in browser does NOT change
- ✅ Request attributes are preserved
- ✅ Shares same request and response objects
- ✅ Faster than redirect

**Example:**
```java
// In Servlet
request.setAttribute("data", "Hello from Servlet!");
RequestDispatcher rd = request.getRequestDispatcher("result.jsp");
rd.forward(request, response);
```

```jsp
<!-- In result.jsp -->
<p>${data}</p>  <!-- Prints: Hello from Servlet! -->
```

---

### 3. Differentiate between Redirect and Forward

| Feature | Forward (`rd.forward()`) | Redirect (`res.sendRedirect()`) |
|---|---|---|
| **Where occurs** | Server-side | Client-side |
| **URL in browser** | Does NOT change | Changes to new URL |
| **Request object** | Same (shared) | New request |
| **Data sharing** | Via request attributes | Via session/URL params |
| **Speed** | Faster | Slower (extra round trip) |
| **External URL** | Cannot forward outside app | Can redirect anywhere |
| **HTTP code** | – | 302 (Redirect) |
| **Use case** | Same app forwarding | Cross-app, logout redirect |

**Forward:**
```java
request.setAttribute("msg", "Success");
request.getRequestDispatcher("success.jsp").forward(request, response);
// URL still shows /OriginalServlet
```

**Redirect:**
```java
response.sendRedirect("https://www.google.com");
// URL changes to google.com
```

---

### 4. Why are JSP and Servlet Combined in Web Applications?

JSP and Servlet are complementary technologies that work best together:

| Technology | Strength | Weakness |
|---|---|---|
| **Servlet** | Business logic, request processing | Poor for generating HTML |
| **JSP** | Presentation, HTML generation | Poor for complex logic |

**Reasons to Combine:**
- ✅ **Separation of Concerns:** Servlet handles logic, JSP handles display
- ✅ **MVC Pattern:** Natural Model-View-Controller implementation
- ✅ **Maintainability:** UI and logic can be changed independently
- ✅ **Designer Friendly:** JSP allows HTML designers to work alongside developers
- ✅ **Reusability:** Same Servlet can forward to different JSPs
- ✅ **Security:** Business logic stays hidden in Servlet, not visible in JSP

**Combined Flow:**
```
User → JSP Form → Servlet (logic + DB) → JSP (display result) → User
```

---

### 5. Explain the Role of Controller in MVC Architecture

In MVC, the **Controller** is the central coordinator:

| Responsibility | Description |
|---|---|
| **Receive Requests** | Accepts HTTP GET/POST from browser |
| **Input Validation** | Validates form data |
| **Call Model** | Invokes business logic/DB operations |
| **Prepare Data** | Sets attributes for View |
| **Choose View** | Forwards to appropriate JSP |
| **Handle Errors** | Manages exceptions and error pages |
| **Session Management** | Manages user session |

**Controller (Servlet) Code:**
```java
@WebServlet("/student/save")
public class StudentController extends HttpServlet {

    private StudentDAO dao = new StudentDAO(); // Model

    protected void doPost(HttpServletRequest req, 
                          HttpServletResponse res) 
                          throws Exception {

        // 1. Receive input
        String name  = req.getParameter("name");
        int    marks = Integer.parseInt(req.getParameter("marks"));

        // 2. Validate
        if(name == null || name.isEmpty()) {
            req.setAttribute("error", "Name is required");
            req.getRequestDispatcher("form.jsp").forward(req, res);
            return;
        }

        // 3. Call Model
        Student student = new Student(0, name, marks);
        dao.save(student);

        // 4. Prepare data for View
        req.setAttribute("message", "Student saved successfully!");
        req.setAttribute("student", student);

        // 5. Choose View
        req.getRequestDispatcher("success.jsp").forward(req, res);
    }
}
```

---

## ✅ 15 Marks Questions

---

### 1. Explain MVC Architecture with Neat Diagram

#### 📊 MVC Architecture Diagram:

```
┌──────────────────────────────────────────────────────────────────┐
│                  MVC ARCHITECTURE (Java EE)                      │
│                                                                  │
│  ┌──────────┐   1.Request   ┌───────────────────────────────┐   │
│  │  Client  │──────────────►│    CONTROLLER (Servlet)       │   │
│  │ Browser  │               │  - Receives HTTP Request      │   │
│  └──────────┘               │  - Validates Input            │   │
│       ▲                     │  - Calls Model                │   │
│       │ 6.Response          │  - Forwards to View           │   │
│       │   (HTML)            └──────────────┬────────────────┘   │
│  ┌──────────┐                              │ 2.Call             │
│  │  VIEW    │                              ▼                    │
│  │  (JSP)   │               ┌───────────────────────────────┐   │
│  │          │               │         MODEL                 │   │
│  │ - HTML   │               │  - JavaBeans (Data)           │   │
│  │ - JSTL   │◄──────────────│  - DAO (Database Access)      │   │
│  │ - EL     │  5.Forward    │  - JDBC / Hibernate           │   │
│  └──────────┘               └──────────────┬────────────────┘   │
│                                            │ 3.DB Operation     │
│                             ┌──────────────▼────────────────┐   │
│                             │         DATABASE               │   │
│                             │   (MySQL / Oracle / H2)       │   │
│                             └───────────────────────────────┘   │
│                                            │ 4.Return Data      │
│                             ┌──────────────▼────────────────┐   │
│                             │    Model returns data to      │   │
│                             │    Controller (DAO result)    │   │
│                             └───────────────────────────────┘   │
└──────────────────────────────────────────────────────────────────┘
```

---

#### 📌 MVC Components in Detail:

---

**1. MODEL:**
```java
// Student.java (JavaBean)
public class Student {
    private int id;
    private String name;
    private int marks;
    // Constructors, Getters, Setters
}

// StudentDAO.java (Data Access Object)
public class StudentDAO {
    private Connection con;

    public StudentDAO() throws Exception {
        con = DriverManager.getConnection(
            "jdbc:mysql://localhost:3306/mydb","root","1234");
    }

    public List<Student> getAllStudents() throws Exception {
        List<Student> list = new ArrayList<>();
        ResultSet rs = con.createStatement()
                         .executeQuery("SELECT * FROM students");
        while(rs.next()) {
            list.add(new Student(rs.getInt("id"),
                                 rs.getString("name"),
                                 rs.getInt("marks")));
        }
        return list;
    }

    public void addStudent(Student s) throws Exception {
        PreparedStatement ps = con.prepareStatement(
            "INSERT INTO students(name,marks) VALUES(?,?)");
        ps.setString(1, s.getName());
        ps.setInt(2, s.getMarks());
        ps.executeUpdate();
    }
}
```

---

**2. VIEW (JSP):**
```jsp
<!-- students.jsp -->
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head><title>Students List</title></head>
<body>
    <h2>All Students</h2>
    <table border="1">
        <tr><th>ID</th><th>Name</th><th>Marks</th></tr>
        <c:forEach var="s" items="${students}">
            <tr>
                <td>${s.id}</td>
                <td>${s.name}</td>
                <td>${s.marks}</td>
            </tr>
        </c:forEach>
    </table>
    <br>
    <a href="addStudent.jsp">Add New Student</a>
</body>
</html>
```

---

**3. CONTROLLER (Servlet):**
```java
@WebServlet("/students")
public class StudentController extends HttpServlet {
    StudentDAO dao;

    public void init() throws ServletException {
        try { dao = new StudentDAO(); }
        catch(Exception e) { throw new ServletException(e); }
    }

    // GET - List all students
    protected void doGet(HttpServletRequest req, 
                         HttpServletResponse res) 
                         throws Exception {
        List<Student> students = dao.getAllStudents();
        req.setAttribute("students", students);
        req.getRequestDispatcher("students.jsp").forward(req, res);
    }

    // POST - Add new student
    protected void doPost(HttpServletRequest req, 
                          HttpServletResponse res) 
                          throws Exception {
        String name  = req.getParameter("name");
        int    marks = Integer.parseInt(req.getParameter("marks"));
        dao.addStudent(new Student(0, name, marks));
        res.sendRedirect("students");
    }
}
```

---

### 2. Explain How JSP and Servlet Work Together in Web Application

---

#### 📌 Complete Working Example – Student Management System:

**File Structure:**
```
WebApp/
├── WEB-INF/
│   ├── web.xml
│   └── classes/
│       ├── Student.java
│       ├── StudentDAO.java
│       └── StudentServlet.java
├── index.jsp
├── addStudent.jsp
├── studentList.jsp
└── error.jsp
```

---

**Step 1: Model – Student.java:**
```java
public class Student {
    private int id;
    private String name;
    private int marks;

    public Student() {}
    public Student(int id, String name, int marks) {
        this.id = id; this.name = name; this.marks = marks;
    }
    // Getters and Setters
    public int    getId()    { return id;    }
    public String getName()  { return name;  }
    public int    getMarks() { return marks; }
    public void   setId(int id)          { this.id = id;       }
    public void   setName(String name)   { this.name = name;   }
    public void   setMarks(int marks)    { this.marks = marks; }
}
```

---

**Step 2: DAO – StudentDAO.java:**
```java
import java.sql.*;
import java.util.*;

public class StudentDAO {
    private Connection con;

    public StudentDAO() throws Exception {
        Class.forName("com.mysql.cj.jdbc.Driver");
        con = DriverManager.getConnection(
            "jdbc:mysql://localhost:3306/mydb","root","1234");
    }

    public List<Student> getAll() throws Exception {
        List<Student> list = new ArrayList<>();
        ResultSet rs = con.createStatement()
                         .executeQuery("SELECT * FROM students");
        while(rs.next())
            list.add(new Student(rs.getInt(1),rs.getString(2),rs.getInt(3)));
        return list;
    }

    public void insert(Student s) throws Exception {
        PreparedStatement ps = con.prepareStatement(
            "INSERT INTO students(name,marks) VALUES(?,?)");
        ps.setString(1, s.getName());
        ps.setInt(2, s.getMarks());
        ps.executeUpdate();
    }
}
```

---

**Step 3: Controller – StudentServlet.java:**
```java
@WebServlet("/student/*")
public class StudentServlet extends HttpServlet {
    StudentDAO dao;

    public void init() throws ServletException {
        try { dao = new StudentDAO(); }
        catch(Exception e) { throw new ServletException(e); }
    }

    protected void doGet(HttpServletRequest req, 
                         HttpServletResponse res) 
                         throws Exception {
        String action = req.getPathInfo();
        if("/list".equals(action)) {
            req.setAttribute("students", dao.getAll());
            req.getRequestDispatcher("/studentList.jsp")
               .forward(req, res);
        } else if("/add".equals(action)) {
            req.getRequestDispatcher("/addStudent.jsp")
               .forward(req, res);
        }
    }

    protected void doPost(HttpServletRequest req, 
                          HttpServletResponse res) 
                          throws Exception {
        String name  = req.getParameter("name");
        int    marks = Integer.parseInt(req.getParameter("marks"));
        dao.insert(new Student(0, name, marks));
        res.sendRedirect(req.getContextPath() + "/student/list");
    }
}
```

---

**Step 4: View – addStudent.jsp:**
```jsp
<html>
<head><title>Add Student</title></head>
<body>
    <h2>Add New Student</h2>
    <form action="/student/" method="POST">
        <label>Name:</label>
        <input type="text" name="name" required>
        <br>
        <label>Marks:</label>
        <input type="number" name="marks" min="0" max="100" required>
        <br>
        <button type="submit">Add Student</button>
    </form>
    <a href="/student/list">View All Students</a>
</body>
</html>
```

---

**Step 5: View – studentList.jsp:**
```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head><title>Student List</title></head>
<body>
    <h2>Student List</h2>
    <a href="/student/add">+ Add Student</a>
    <br><br>
    <table border="1" cellpadding="5">
        <tr>
            <th>ID</th><th>Name</th><th>Marks</th><th>Grade</th>
        </tr>
        <c:forEach var="s" items="${students}">
            <tr>
                <td>${s.id}</td>
                <td>${s.name}</td>
                <td>${s.marks}</td>
                <td>
                    <c:choose>
                        <c:when test="${s.marks >= 90}">A</c:when>
                        <c:when test="${s.marks >= 75}">B</c:when>
                        <c:when test="${s.marks >= 60}">C</c:when>
                        <c:otherwise>F</c:otherwise>
                    </c:choose>
                </td>
            </tr>
        </c:forEach>
    </table>
    <p>Total Students: ${students.size()}</p>
</body>
</html>
```

---

#### 📊 Request Flow Summary:

```
User visits /student/list
      ↓
StudentServlet.doGet() receives request
      ↓
Calls StudentDAO.getAll() (Model)
      ↓
DAO queries database (SELECT * FROM students)
      ↓
Returns List<Student> to Servlet
      ↓
Servlet sets list as request attribute
      ↓
Servlet forwards to studentList.jsp (View)
      ↓
JSP renders HTML with JSTL c:forEach
      ↓
HTML sent to browser (User sees table)
```

---

### 3. Write and Explain Program Flow for Request Forwarding Between JSP and Servlet

---

#### 📌 Complete Request Forwarding Example:

**Flow:**
```
index.jsp (form) → CalculatorServlet → result.jsp
```

---

**Step 1: index.jsp (View – Input Form):**
```jsp
<%@ page language="java" %>
<html>
<head><title>Calculator</title></head>
<body>
    <h2>Simple Calculator</h2>

    <!-- Error message from previous failed request -->
    <c:if test="${not empty error}">
        <p style="color:red">${error}</p>
    </c:if>

    <form action="calculate" method="POST">
        <input type="number" name="num1" placeholder="Number 1" required>
        <select name="operator">
            <option value="+">Addition (+)</option>
            <option value="-">Subtraction (-)</option>
            <option value="*">Multiply (*)</option>
            <option value="/">Divide (/)</option>
        </select>
        <input type="number" name="num2" placeholder="Number 2" required>
        <button type="submit">Calculate</button>
    </form>
</body>
</html>
```

---

**Step 2: CalculatorServlet.java (Controller):**
```java
@WebServlet("/calculate")
public class CalculatorServlet extends HttpServlet {

    protected void doPost(HttpServletRequest req, 
                          HttpServletResponse res) 
                          throws IOException, ServletException {

        // Step 1: Read Parameters
        String num1Str = req.getParameter("num1");
        String num2Str = req.getParameter("num2");
        String operator = req.getParameter("operator");

        // Step 2: Validate
        if(num1Str.isEmpty() || num2Str.isEmpty()) {
            req.setAttribute("error", "Please enter both numbers!");
            req.getRequestDispatcher("index.jsp").forward(req, res);
            return;
        }

        // Step 3: Business Logic
        double num1   = Double.parseDouble(num1Str);
        double num2   = Double.parseDouble(num2Str);
        double result = 0;
        String errorMsg = null;

        switch(operator) {
            case "+": result = num1 + num2; break;
            case "-": result = num1 - num2; break;
            case "*": result = num1 * num2; break;
            case "/":
                if(num2 == 0) {
                    errorMsg = "Cannot divide by zero!";
                } else {
                    result = num1 / num2;
                }
                break;
        }

        if(errorMsg != null) {
            // Step 4a: Forward back with error
            req.setAttribute("error", errorMsg);
            req.getRequestDispatcher("index.jsp").forward(req, res);
        } else {
            // Step 4b: Set result attributes
            req.setAttribute("num1",     num1);
            req.setAttribute("num2",     num2);
            req.setAttribute("operator", operator);
            req.setAttribute("result",   result);

            // Step 5: Forward to result.jsp
            req.getRequestDispatcher("result.jsp").forward(req, res);
        }
    }

    protected void doGet(HttpServletRequest req, 
                         HttpServletResponse res) 
                         throws IOException, ServletException {
        req.getRequestDispatcher("index.jsp").forward(req, res);
    }
}
```

---

**Step 3: result.jsp (View – Output):**
```jsp
<%@ page language="java" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head><title>Result</title></head>
<body>
    <h2>Calculation Result</h2>

    <p><b>Expression:</b> 
       ${num1} ${operator} ${num2} = <b>${result}</b>
    </p>

    <c:choose>
        <c:when test="${result > 100}">
            <p style="color:blue">Result is greater than 100</p>
        </c:when>
        <c:when test="${result < 0}">
            <p style="color:red">Result is negative</p>
        </c:when>
        <c:otherwise>
            <p style="color:green">Result is between 0 and 100</p>
        </c:otherwise>
    </c:choose>

    <br>
    <a href="index.jsp">← Calculate Again</a>
</body>
</html>
```

---

#### 📊 Request Forwarding Flow Diagram:

```
Browser
  │
  │  POST /calculate (num1=10, operator=+, num2=20)
  ▼
CalculatorServlet.doPost()
  │  Reads parameters
  │  Validates input
  │  Computes: 10 + 20 = 30
  │  req.setAttribute("result", 30)
  │  req.setAttribute("num1", 10)
  │  req.setAttribute("operator", "+")
  │  req.setAttribute("num2", 20)
  │
  │  req.getRequestDispatcher("result.jsp").forward(req, res)
  ▼
result.jsp
  │  Reads ${result} → 30
  │  Reads ${num1} → 10
  │  Reads ${operator} → +
  │  Renders HTML
  ▼
Browser receives HTML response
URL still shows: /calculate  (URL does NOT change with forward!)
```

---

---

# 📘 MODULE 6 – Hibernate

---

## ✅ 5 Marks Questions

---

### 1. What is Hibernate?

**Hibernate** is an open-source, lightweight **ORM (Object-Relational Mapping)** framework for Java that simplifies database interactions by mapping Java objects to database tables.

**Developed by:** Red Hat (originally by Gavin King, 2001)
**Current Version:** Hibernate 6.x

| Feature | Description |
|---|---|
| ORM Framework | Maps Java classes to DB tables |
| HQL | Hibernate Query Language |
| Caching | First-level and second-level cache |
| Lazy Loading | Loads data only when needed |
| Auto DDL | Can create/update tables automatically |
| Transaction | Manages DB transactions |
| DB Independent | Works with MySQL, Oracle, PostgreSQL |

```
Java Objects ←──────── Hibernate ──────────→ Database Tables
   Employee                                     employee_table
   Product                                      product_table
```

---

### 2. What is ORM?

**ORM (Object-Relational Mapping)** is a programming technique that converts data between incompatible type systems (Java objects ↔ Relational DB tables).

**Problem Without ORM:**
```java
// Manual JDBC - verbose and tedious
PreparedStatement ps = con.prepareStatement(
    "INSERT INTO employee(id,name,salary) VALUES(?,?,?)");
ps.setInt(1, emp.getId());
ps.setString(2, emp.getName());
ps.setDouble(3, emp.getSalary());
ps.executeUpdate();
```

**Solution With ORM (Hibernate):**
```java
// Hibernate - simple and clean
session.save(emp); // One line!
```

**ORM Mapping Example:**

| Java Class | Database Table |
|---|---|
| `class Employee {}` | `employee` table |
| `int id` | `INT id` column |
| `String name` | `VARCHAR name` column |
| `double salary` | `DOUBLE salary` column |
| Object instance | Table row |
| Getter method | Column value |

---

### 3. Explain the Advantages of Hibernate over JDBC

| Feature | JDBC | Hibernate |
|---|---|---|
| **Code Length** | Lengthy, repetitive | Concise, minimal |
| **SQL Knowledge** | Required | Optional (HQL) |
| **DB Portability** | Requires SQL changes | DB independent |
| **Mapping** | Manual | Automatic via annotations |
| **Object Handling** | Result to Object manually | Automatic |
| **Caching** | Not built-in | Built-in (L1 & L2) |
| **Lazy Loading** | Not available | Available |
| **Transactions** | Manual | Automatic |
| **Exception Handling** | Checked exceptions | Runtime exceptions |
| **Connection Pool** | Manual setup | Built-in via c3p0 |

**Code Comparison:**
```java
// JDBC - 15+ lines for simple insert
Connection con = DriverManager.getConnection(url, user, pass);
PreparedStatement ps = con.prepareStatement(
    "INSERT INTO employee(name,salary) VALUES(?,?)");
ps.setString(1, emp.getName());
ps.setDouble(2, emp.getSalary());
ps.executeUpdate();
ps.close(); con.close();

// Hibernate - 3 lines for same insert
Session session = factory.openSession();
session.beginTransaction();
session.save(emp);
session.getTransaction().commit();
session.close();
```

---

### 4. What is Hibernate Configuration File?

**Hibernate Configuration File (`hibernate.cfg.xml`)** is an XML file that provides Hibernate with:
- Database connection settings
- Hibernate properties
- Mapping class references

```xml
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
            jdbc:mysql://localhost:3306/mydb
        </property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">1234</property>

        <!-- Hibernate Settings -->
        <property name="hibernate.dialect">
            org.hibernate.dialect.MySQL8Dialect
        </property>
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>
        <property name="hibernate.hbm2ddl.auto">update</property>

        <!-- Mapping Classes -->
        <mapping class="com.example.Employee"/>
        <mapping class="com.example.Product"/>
    </session-factory>
</hibernate-configuration>
```

**hbm2ddl.auto options:**
| Value | Description |
|---|---|
| `create` | Drop and create tables each run |
| `create-drop` | Drop tables on session close |
| `update` | Update existing tables |
| `validate` | Validate schema only |
| `none` | Do nothing |

---

### 5. What is Mapping in Hibernate?

**Mapping** in Hibernate is the process of defining the relationship between Java class attributes and database table columns.

**Two Ways to Map:**

**1. Annotation-based (Recommended):**
```java
import javax.persistence.*;

@Entity
@Table(name = "employee")
public class Employee {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "emp_id")
    private int id;

    @Column(name = "emp_name", length = 50, nullable = false)
    private String name;

    @Column(name = "emp_salary")
    private double salary;
    // Getters and Setters
}
```

**2. XML-based mapping (`.hbm.xml`):**
```xml
<!-- employee.hbm.xml -->
<hibernate-mapping>
    <class name="com.example.Employee" table="employee">
        <id name="id" column="emp_id">
            <generator class="identity"/>
        </id>
        <property name="name"   column="emp_name"/>
        <property name="salary" column="emp_salary"/>
    </class>
</hibernate-mapping>
```

---

## ✅ 15 Marks Questions

---

### 1. Explain Hibernate Architecture and its Core Components

#### 📊 Hibernate Architecture Diagram:

```
┌────────────────────────────────────────────────────────────────────┐
│                    HIBERNATE ARCHITECTURE                          │
│                                                                    │
│  ┌─────────────────────────────────────────────────────────────┐  │
│  │                  Java Application                           │  │
│  └──────────────────────────┬──────────────────────────────────┘  │
│                             ↓                                      │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │                 HIBERNATE FRAMEWORK                          │  │
│  │  ┌─────────────┐  ┌──────────────┐  ┌──────────────────┐   │  │
│  │  │Configuration│  │SessionFactory│  │     Session      │   │  │
│  │  │    Object   │─►│   (One/App)  │─►│  (One/Request)   │   │  │
│  │  └─────────────┘  └──────────────┘  └────────┬─────────┘   │  │
│  │                                              │               │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────▼────────────┐ │  │
│  │  │  Query / HQL │  │  Transaction │  │  Criteria API     │ │  │
│  │  └──────────────┘  └──────────────┘  └───────────────────┘ │  │
│  └──────────────────────────┬──────────────────────────────────┘  │
│                             ↓                                      │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │              JDBC / Connection Pool                          │  │
│  └──────────────────────────┬──────────────────────────────────┘  │
│                             ↓                                      │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │              Database (MySQL / Oracle / PostgreSQL)          │  │
│  └──────────────────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────────────────┘
```

---

#### 📌 Core Components:

---

**1. Configuration:**
- First class to be created
- Reads `hibernate.cfg.xml` or properties file
- Builds `SessionFactory`

```java
Configuration config = new Configuration();
config.configure("hibernate.cfg.xml");  // Reads config file
config.addAnnotatedClass(Employee.class);
```

---

**2. ServiceRegistry:**
- Manages services required by Hibernate
- Introduced in Hibernate 4+

```java
ServiceRegistry registry = new StandardServiceRegistryBuilder()
    .applySettings(config.getProperties())
    .build();
```

---

**3. SessionFactory:**
- Heavy-weight object; created **once** per application
- Thread-safe; used to create `Session` objects
- Acts as connection pool

```java
SessionFactory factory = config.buildSessionFactory(registry);
```

---

**4. Session:**
- Light-weight; created **per transaction/request**
- Not thread-safe
- Main interface for DB operations
- Manages first-level cache

```java
Session session = factory.openSession();
// Use session for CRUD operations
session.close();
```

---

**5. Transaction:**
- Manages database transactions
- Must commit or rollback

```java
Transaction tx = session.beginTransaction();
try {
    session.save(obj);
    tx.commit();
} catch(Exception e) {
    tx.rollback();
}
```

---

**6. Query / HQL:**
- HQL = Hibernate Query Language (object-based)
- Independent of database

```java
Query query = session.createQuery("FROM Employee WHERE salary > :sal");
query.setParameter("sal", 50000);
List<Employee> list = query.list();
```

---

**7. Criteria API:**
- Type-safe programmatic query builder

```java
CriteriaBuilder cb = session.getCriteriaBuilder();
CriteriaQuery<Employee> cq = cb.createQuery(Employee.class);
Root<Employee> root = cq.from(Employee.class);
cq.select(root).where(cb.gt(root.get("salary"), 50000));
List<Employee> list = session.createQuery(cq).getResultList();
```

---

**8. Cache:**

| Level | Type | Scope |
|---|---|---|
| **L1 Cache** | Session Cache | Per Session (default, always enabled) |
| **L2 Cache** | SessionFactory Cache | Across Sessions (optional) |
| **Query Cache** | Caches query results | Specific queries |

---

#### 📊 Component Summary Table:

| Component | Purpose | Scope |
|---|---|---|
| `Configuration` | Load settings | Once |
| `ServiceRegistry` | Manage services | Once |
| `SessionFactory` | Create sessions | Application-wide |
| `Session` | DB operations | Per request |
| `Transaction` | ACID operations | Per transaction |
| `Query` | Execute HQL | Per query |
| `Criteria` | Type-safe queries | Per query |
| `Cache (L1)` | Session-level cache | Per session |
| `Cache (L2)` | App-level cache | Application-wide |

---

### 2. Explain ORM and Advantages of Hibernate over JDBC

*(Covered in 5-mark answers above — expanded below)*

#### 📌 ORM (Object-Relational Mapping) in Detail:

**The Impedance Mismatch Problem:**

| Java World | Database World |
|---|---|
| Objects | Rows |
| Classes | Tables |
| Attributes | Columns |
| References | Foreign Keys |
| Inheritance | No direct equivalent |
| Polymorphism | No direct equivalent |

ORM bridges this gap automatically.

---

#### 📌 ORM Mapping Types:

**1. One-to-One:**
```java
@Entity public class Person {
    @Id int id;
    String name;

    @OneToOne(cascade = CascadeType.ALL)
    @JoinColumn(name = "passport_id")
    Passport passport;
}
```

**2. One-to-Many:**
```java
@Entity public class Department {
    @Id int id;
    String name;

    @OneToMany(mappedBy = "department", cascade = CascadeType.ALL)
    List<Employee> employees;
}
```

**3. Many-to-One:**
```java
@Entity public class Employee {
    @Id int id;
    String name;

    @ManyToOne
    @JoinColumn(name = "dept_id")
    Department department;
}
```

**4. Many-to-Many:**
```java
@Entity public class Student {
    @Id int id;
    String name;

    @ManyToMany
    @JoinTable(name = "student_course",
        joinColumns = @JoinColumn(name = "student_id"),
        inverseJoinColumns = @JoinColumn(name = "course_id"))
    List<Course> courses;
}
```

---

#### 📊 Hibernate vs JDBC – Detailed Comparison:

| Aspect | JDBC | Hibernate |
|---|---|---|
| **Code Volume** | ~20 lines per operation | ~5 lines |
| **SQL Dependency** | High | Low (HQL) |
| **DB Switch** | Requires SQL rewrite | Change dialect only |
| **Caching** | None | L1 + L2 cache |
| **Object Mapping** | Manual ResultSet to Object | Automatic |
| **Connection Pool** | Manual | Built-in |
| **Lazy Loading** | Not available | Available |
| **Learning Curve** | Low | Medium |
| **Performance** | High (fine-tuned SQL) | High (with cache) |
| **Exception** | Checked (verbose) | Runtime (cleaner) |
| **Schema Generation** | Manual SQL scripts | `hbm2ddl.auto` |
| **HQL** | Not available | Available |
| **Pagination** | Manual LIMIT/OFFSET | `setFirstResult()` |

---

### 3. Explain Steps to Set Up Hibernate in Java Application

---

#### 📋 Step-by-Step Setup:

---

**Step 1: Create Maven Project and Add Dependencies (pom.xml):**
```xml
<dependencies>
    <!-- Hibernate Core -->
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>5.6.15.Final</version>
    </dependency>

    <!-- MySQL Connector -->
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.32</version>
    </dependency>
</dependencies>
```

---

**Step 2: Create Database:**
```sql
CREATE DATABASE hibernatedb;
USE hibernatedb;
-- Hibernate will auto-create tables with hbm2ddl.auto=update
```

---

**Step 3: Create hibernate.cfg.xml:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
    "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
    "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
    <session-factory>
        <property name="hibernate.connection.driver_class">
            com.mysql.cj.jdbc.Driver
        </property>
        <property name="hibernate.connection.url">
            jdbc:mysql://localhost:3306/hibernatedb
        </property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">1234</property>
        <property name="hibernate.dialect">
            org.hibernate.dialect.MySQL8Dialect
        </property>
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>
        <property name="hibernate.hbm2ddl.auto">update</property>

        <mapping class="com.example.Employee"/>
    </session-factory>
</hibernate-configuration>
```

---

**Step 4: Create Entity Class – Employee.java:**
```java
package com.example;

import javax.persistence.*;

@Entity
@Table(name = "employee")
public class Employee {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "emp_id")
    private int id;

    @Column(name = "emp_name", nullable = false, length = 100)
    private String name;

    @Column(name = "emp_dept")
    private String department;

    @Column(name = "emp_salary")
    private double salary;

    // No-arg constructor (required by Hibernate)
    public Employee() {}

    // Parameterized constructor
    public Employee(String name, String department, double salary) {
        this.name       = name;
        this.department = department;
        this.salary     = salary;
    }

    // Getters and Setters
    public int    getId()          { return id;         }
    public String getName()        { return name;       }
    public String getDepartment()  { return department; }
    public double getSalary()      { return salary;     }
    public void   setId(int id)            { this.id = id;             }
    public void   setName(String n)        { this.name = n;            }
    public void   setDepartment(String d)  { this.department = d;      }
    public void   setSalary(double s)      { this.salary = s;          }

    @Override
    public String toString() {
        return "Employee[id=" + id + ", name=" + name +
               ", dept=" + department + ", salary=" + salary + "]";
    }
}
```

---

**Step 5: Create HibernateUtil.java (SessionFactory):**
```java
package com.example;

import org.hibernate.*;
import org.hibernate.cfg.Configuration;
import org.hibernate.boot.registry.StandardServiceRegistryBuilder;
import org.hibernate.service.ServiceRegistry;

public class HibernateUtil {

    private static SessionFactory sessionFactory;

    static {
        try {
            Configuration config = new Configuration();
            config.configure("hibernate.cfg.xml");

            ServiceRegistry registry = new StandardServiceRegistryBuilder()
                .applySettings(config.getProperties())
                .build();

            sessionFactory = config.buildSessionFactory(registry);

        } catch(Exception e) {
            throw new ExceptionInInitializerError(e);
        }
    }

    public static SessionFactory getSessionFactory() {
        return sessionFactory;
    }

    public static void shutdown() {
        getSessionFactory().close();
    }
}
```

---

**Step 6: Perform CRUD Operations – Main.java:**
```java
package com.example;

import org.hibernate.*;
import java.util.List;

public class Main {

    public static void main(String[] args) {
        SessionFactory factory = HibernateUtil.getSessionFactory();

        // ─────── INSERT ───────
        Session s1 = factory.openSession();
        s1.beginTransaction();
        s1.save(new Employee("Alice", "IT",      85000));
        s1.save(new Employee("Bob",   "HR",      65000));
        s1.save(new Employee("Carol", "Finance", 75000));
        s1.getTransaction().commit();
        s1.close();
        System.out.println("✅ Employees Inserted");

        // ─────── SELECT ALL ───────
        Session s2 = factory.openSession();
        List<Employee> list = s2.createQuery(
            "FROM Employee", Employee.class).list();
        System.out.println("\n📋 All Employees:");
        for(Employee e : list) System.out.println(e);
        s2.close();

        // ─────── SELECT BY ID ───────
        Session s3 = factory.openSession();
        Employee emp = s3.get(Employee.class, 1);
        System.out.println("\n🔍 Employee with ID 1: " + emp);
        s3.close();

        // ─────── UPDATE ───────
        Session s4 = factory.openSession();
        s4.beginTransaction();
        Employee toUpdate = s4.get(Employee.class, 1);
        toUpdate.setSalary(95000);
        s4.update(toUpdate);
        s4.getTransaction().commit();
        s4.close();
        System.out.println("\n✏️ Updated Salary of ID 1 to 95000");

        // ─────── DELETE ───────
        Session s5 = factory.openSession();
        s5.beginTransaction();
        Employee toDelete = s5.get(Employee.class, 2);
        if(toDelete != null) {
            s5.delete(toDelete);
            System.out.println("\n🗑️ Deleted Employee: " + toDelete.getName());
        }
        s5.getTransaction().commit();
        s5.close();

        // ─────── HQL QUERY ───────
        Session s6 = factory.openSession();
        List<Employee> highPaid = s6.createQuery(
            "FROM Employee WHERE salary > :minSal", Employee.class)
            .setParameter("minSal", 70000.0)
            .list();
        System.out.println("\n💰 High-Paid Employees (>70000):");
        for(Employee e : highPaid) System.out.println(e);
        s6.close();

        HibernateUtil.shutdown();
    }
}
```

---

#### 📊 Setup Summary:

| Step | Task |
|---|---|
| 1 | Add Maven dependencies |
| 2 | Create database |
| 3 | Create `hibernate.cfg.xml` |
| 4 | Create entity class with `@Entity` |
| 5 | Create `HibernateUtil` for `SessionFactory` |
| 6 | Use `Session` for CRUD operations |

---

### 4. Explain Mapping Java Classes to Database Tables with Examples

---

#### 📌 Core Mapping Annotations:

| Annotation | Description |
|---|---|
| `@Entity` | Marks class as Hibernate entity |
| `@Table(name="...")` | Specifies table name |
| `@Id` | Marks primary key |
| `@GeneratedValue` | Auto-generates primary key |
| `@Column(name="...")` | Maps field to column |
| `@Transient` | Field not persisted in DB |
| `@Temporal` | Maps Date/Time types |
| `@Lob` | For large objects (BLOB/CLOB) |
| `@OneToOne` | One-to-One relationship |
| `@OneToMany` | One-to-Many relationship |
| `@ManyToOne` | Many-to-One relationship |
| `@ManyToMany` | Many-to-Many relationship |

---

#### 📌 Example 1 – Basic Mapping:

```java
@Entity
@Table(name = "product")
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "prod_id")
    private int id;

    @Column(name = "prod_name", nullable = false, unique = true, length = 100)
    private String name;

    @Column(name = "prod_price", precision = 10, scale = 2)
    private double price;

    @Column(name = "prod_stock")
    private int stock;

    @Transient  // NOT stored in DB
    private double discountedPrice;

    @Temporal(TemporalType.DATE)
    @Column(name = "manufacture_date")
    private java.util.Date manufactureDate;

    @Lob
    @Column(name = "description")
    private String description;

    // Constructors, Getters, Setters
}
```

**Generated Table:**
```sql
CREATE TABLE product (
    prod_id         INT         AUTO_INCREMENT PRIMARY KEY,
    prod_name       VARCHAR(100) NOT NULL UNIQUE,
    prod_price      DECIMAL(10,2),
    prod_stock      INT,
    manufacture_date DATE,
    description     LONGTEXT
);
```

---

#### 📌 Example 2 – One-to-Many Mapping:

```java
// Department (One) ←──── Employee (Many)

@Entity
@Table(name = "department")
public class Department {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    @Column(name = "dept_name")
    private String name;

    @OneToMany(mappedBy = "department", 
               cascade = CascadeType.ALL,
               fetch = FetchType.LAZY)
    private List<Employee> employees = new ArrayList<>();

    // Getters, Setters
}

@Entity
@Table(name = "employee")
public class Employee {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    @Column(name = "emp_name")
    private String name;

    @ManyToOne
    @JoinColumn(name = "dept_id", nullable = false)
    private Department department;

    // Getters, Setters
}
```

**Usage:**
```java
Session session = factory.openSession();
session.beginTransaction();

Department dept = new Department();
dept.setName("Information Technology");

Employee e1 = new Employee();
e1.setName("Alice");
e1.setDepartment(dept);

Employee e2 = new Employee();
e2.setName("Bob");
e2.setDepartment(dept);

dept.getEmployees().add(e1);
dept.getEmployees().add(e2);

session.save(dept); // Cascades to employees

session.getTransaction().commit();
session.close();
```

---

#### 📌 Example 3 – Many-to-Many Mapping:

```java
// Student (Many) ↔ Course (Many)

@Entity
@Table(name = "student")
public class Student {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    private String name;

    @ManyToMany(cascade = CascadeType.ALL)
    @JoinTable(
        name = "student_course",
        joinColumns = @JoinColumn(name = "student_id"),
        inverseJoinColumns = @JoinColumn(name = "course_id")
    )
    private List<Course> courses = new ArrayList<>();
    // Getters, Setters
}

@Entity
@Table(name = "course")
public class Course {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    private String title;

    @ManyToMany(mappedBy = "courses")
    private List<Student> students = new ArrayList<>();
    // Getters, Setters
}
```

**Generated Tables:**
```sql
CREATE TABLE student       (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(50));
CREATE TABLE course        (id INT AUTO_INCREMENT PRIMARY KEY, title VARCHAR(100));
CREATE TABLE student_course(student_id INT, course_id INT,
                            PRIMARY KEY(student_id, course_id));
```

---

#### 📊 Mapping Strategies Summary:

| Strategy | Annotation | Use Case |
|---|---|---|
| **Basic** | `@Entity`, `@Table`, `@Column` | Simple class → table |
| **Primary Key** | `@Id`, `@GeneratedValue` | Auto-generate PK |
| **One-to-One** | `@OneToOne` | Person ↔ Passport |
| **One-to-Many** | `@OneToMany` | Department → Employees |
| **Many-to-One** | `@ManyToOne` | Employee → Department |
| **Many-to-Many** | `@ManyToMany` | Student ↔ Course |
| **Inheritance** | `@Inheritance` | Class hierarchy |
| **Embedded** | `@Embedded` | Address inside Person |

---

> 📌 **Note:** This complete guide covers all 6 modules (M1–M6) with all 5-mark and 15-mark questions. Each answer includes theoretical explanations, diagrams, code examples, and comparison tables for exam preparation. Good luck! 🎓