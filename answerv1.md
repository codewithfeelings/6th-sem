# Group B: Short Answer Questions

---

## 1. Define a Java EE Component and a Java EE Container. [2+3]

**Java EE Component (2 marks):**
A Java EE Component is a self-contained, functional software unit that is assembled into a Java EE application along with its related classes and files. It communicates with other components through well-defined interfaces. Examples include Servlets, JSP pages, EJBs, and Applets.

**Java EE Container (3 marks):**
A Java EE Container is a runtime environment that provides the infrastructure services (lifecycle management, security, transaction management, JNDI lookup, resource pooling) needed by Java EE components. The container acts as an intermediary between the component and the low-level platform functionality. Types include:
- **Web Container** – manages Servlets and JSP pages
- **EJB Container** – manages Enterprise JavaBeans
- **Application Client Container** – manages application client components

---

## 2. Responsibilities of Client Tier and Business Tier in Three-Tier Architecture. [2.5+2.5]

**Client Tier (2.5 marks):**
- Provides the **user interface** (browser, mobile app, desktop client).
- Captures user input and sends HTTP requests to the middle tier.
- Renders the response (HTML/CSS/JS) received from the server.
- Performs basic **client-side validation** (e.g., JavaScript form validation).
- Contains no business logic; it is purely a presentation layer.

**Business Tier (2.5 marks):**
- Contains the **core business logic** and rules of the application.
- Processes client requests received from the web/presentation tier.
- Manages **transactions**, security enforcement, and data validation at a deeper level.
- Interacts with the **Data/EIS Tier** (databases, legacy systems) to retrieve or persist data.
- Typically implemented using EJBs, POJOs, or managed beans.

---

## 3. Five Web Application or Enterprise Application Technologies Provided by Java EE. [5]

| # | Technology | Purpose |
|---|-----------|---------|
| 1 | **Java Servlet** | Server-side request/response handling |
| 2 | **JavaServer Pages (JSP)** | Dynamic HTML content generation |
| 3 | **Enterprise JavaBeans (EJB)** | Distributed business logic, transactions |
| 4 | **Java Persistence API (JPA)** | Object-relational mapping and data persistence |
| 5 | **JavaServer Faces (JSF)** | Component-based UI framework |

*(Other valid answers: JNDI, JMS, JAX-RS, JAX-WS, CDI, JTA, JavaMail, WebSocket API)*

---

## 4. Primary Role of a Java Servlet Acting as a Controller. [5]

A Servlet acting as a **Controller** in the MVC pattern serves as the central coordinator of request processing:

1. **Receives all incoming HTTP requests** from the client (browser).
2. **Parses and validates** the request parameters and headers.
3. **Invokes the appropriate business logic** (Model layer — JavaBeans, EJBs, service classes) based on the requested action.
4. **Selects the correct View** (JSP page) to render the response based on the outcome of business processing.
5. **Forwards the request** (via `RequestDispatcher.forward()`) to the chosen JSP, passing any model data through request attributes.

The Controller Servlet itself generates **no HTML**. It acts purely as a traffic cop — decoupling presentation from business logic and ensuring clean separation of concerns.

---

## 5. Mechanism of an HTTP Request Reaching an Executing HTTP Servlet. [5]

```
Browser → HTTP Request → Web Server → Web Container → Servlet
```

**Step-by-step mechanism:**

1. **Client sends an HTTP request** (GET/POST) with a specific URL to the web server.
2. **Web Server receives the request** and delegates it to the **Web Container** (e.g., Tomcat).
3. **Container consults `web.xml`** (or annotations like `@WebServlet`) to find the **URL-to-Servlet mapping**.
4. **Container creates/reuses a thread** and constructs the `HttpServletRequest` and `HttpServletResponse` objects.
5. If the Servlet is **not yet loaded**, the container:
   - Loads the Servlet class
   - Creates an instance
   - Calls `init(ServletConfig)` once
6. **Container calls `service()`**, which routes to `doGet()` or `doPost()` based on the HTTP method.
7. The Servlet processes the request and writes the response; the container sends it back to the client.

---

## 6. Compare `jspInit()` and `jspDestroy()` Methods. [2.5+2.5]

| Aspect | `jspInit()` | `jspDestroy()` |
|--------|------------|----------------|
| **When invoked** | Called **once** when the JSP page is first loaded/translated and the generated Servlet instance is initialized | Called **once** when the JSP page (Servlet instance) is being removed from service by the container |
| **Purpose** | Perform **one-time initialization** tasks: open DB connections, load configuration, initialize resources | Perform **cleanup** tasks: close DB connections, release resources, flush buffers |
| **Equivalent** | Analogous to `Servlet.init()` | Analogous to `Servlet.destroy()` |
| **Override** | Can be overridden using `<%! public void jspInit() { ... } %>` | Can be overridden using `<%! public void jspDestroy() { ... } %>` |
| **Frequency** | Once per Servlet instance lifetime (beginning) | Once per Servlet instance lifetime (end) |

---

## 7. Translation Phase of the JSP Lifecycle. [1+4]

**Explanation (1 mark):**
The Translation Phase is the initial stage where the Web Container converts a `.jsp` file into an equivalent Java Servlet source file (`.java`), and then compiles it into a `.class` file. This typically occurs on the **first request** or when the JSP file has been modified.

**Four Specific Steps (4 marks):**

1. **Parsing** — The container reads the entire JSP file and parses all directives (`<%@ ... %>`), scripting elements, standard actions, and template text.
2. **Translation** — The parsed JSP elements are converted into corresponding Java Servlet source code (e.g., template text → `out.write("...")`, expressions → `out.print(...)`).
3. **Compilation** — The generated `.java` source file is compiled by the Java compiler into a `.class` bytecode file.
4. **Class Loading** — The compiled Servlet class is loaded into the JVM by the container's class loader, ready for instantiation and initialization.

---

## 8. Differentiate JSP Scriptlet and JSP Expression. [2.5+2.5]

**JSP Scriptlet (2.5 marks):**
- Contains **one or more Java statements** that are executed when the page is requested.
- Code is placed directly inside the `_jspService()` method body.
- Can contain variable declarations, loops, conditionals, method calls, etc.
- **Does not** automatically produce output to the client.

**Syntax:**
```jsp
<%
    String name = request.getParameter("user");
    int count = 10;
    for (int i = 0; i < count; i++) {
        out.println(i);
    }
%>
```

**JSP Expression (2.5 marks):**
- Contains a **single Java expression** that is evaluated, converted to a `String`, and **automatically written** to the output stream.
- Equivalent to `out.print(expression)`.
- Must **not** end with a semicolon.

**Syntax:**
```jsp
<%= expression %>

<!-- Example -->
<p>Welcome, <%= request.getParameter("user") %></p>
```

| Feature | Scriptlet `<% ... %>` | Expression `<%= ... %>` |
|---------|----------------------|------------------------|
| Semicolons | Required | **Not** allowed |
| Output | Manual (`out.print()`) | Automatic |
| Content | Multiple statements | Single expression |

---

## 9. Purpose of the JSP Page Directive and Three Common Attributes. [2+3]

**Purpose (2 marks):**
The `page` directive provides **global instructions to the JSP container** about the overall properties of the JSP page. It affects how the container translates and processes the entire page. It applies to the current JSP file and any files included via the `include` directive.

**Syntax:** `<%@ page attribute="value" %>`

**Three Common Attributes (3 marks):**

| Attribute | Description | Example |
|-----------|------------|---------|
| `import` | Imports Java classes/packages (like Java `import` statement) | `<%@ page import="java.util.*, java.sql.Connection" %>` |
| `contentType` | Sets the MIME type and character encoding of the response | `<%@ page contentType="text/html; charset=UTF-8" %>` |
| `errorPage` | Specifies the URL of a JSP page to redirect to if an unhandled exception occurs | `<%@ page errorPage="error.jsp" %>` |

*(Other valid: `isErrorPage`, `session`, `language`, `isThreadSafe`, `buffer`, `autoFlush`, `extends`, `info`)*

---

## 10. Functional Difference Between `import` and `errorPage` Attributes. [2.5+2.5]

**`import` Attribute (2.5 marks):**
- Functions exactly like the Java `import` statement.
- Makes specified **Java classes and packages available** for use in the JSP page's scripting elements.
- It is the **only** page directive attribute that can appear **multiple times** in the same page.
- Default imports: `java.lang.*`, `javax.servlet.*`, `javax.servlet.http.*`, `javax.servlet.jsp.*`.

```jsp
<%@ page import="java.util.List, java.text.SimpleDateFormat" %>
```

**`errorPage` Attribute (2.5 marks):**
- Specifies a **URL to another JSP page** that acts as the error handler.
- When an **unhandled exception** is thrown during execution of the current page, the container automatically **forwards** the request to the specified error page.
- The target error page typically has `isErrorPage="true"` set, which makes the implicit `exception` object available.

```jsp
<%@ page errorPage="/errors/error.jsp" %>
```

**Key Difference:** `import` governs **compilation** (which classes are visible), while `errorPage` governs **runtime error handling** (where to redirect on failure).

---

## 11. How `<%@ include file="..." %>` Directive Operates During Translation. [5]

The `include` directive is a **static include** mechanism that operates at **translation time** (not at request time):

1. **At translation time**, when the JSP container encounters `<%@ include file="header.jsp" %>`, it **reads the entire content** of the specified file (`header.jsp`).
2. The content of the included file is **literally copy-pasted** (merged) into the including JSP page at the exact position where the directive appears.
3. The result is a **single, combined JSP source** that is then translated into **one Servlet class**.
4. Because the inclusion happens **before compilation**, the included file can contain JSP directives, declarations, scriptlets, and expressions that share the **same variable scope** as the parent page.
5. If the included file is modified, the **parent JSP must be retranslated** for changes to take effect (some containers detect this automatically).

```jsp
<%@ include file="header.jsp" %>    <!-- Merged at translation -->
<p>Main content here</p>
<%@ include file="footer.jsp" %>    <!-- Merged at translation -->
```

**Analogy:** It is like the C/C++ `#include` preprocessor directive — pure textual substitution before compilation.

---

## 12. Why Does the JSP Framework Discourage Heavy Use of Scriptlets? [5]

The JSP framework discourages heavy scriptlet use for several important reasons:

1. **Violation of Separation of Concerns (MVC):** Embedding Java business logic directly in JSP pages **mixes presentation with logic**, making it impossible to cleanly separate the Model, View, and Controller responsibilities.

2. **Maintainability Nightmare:** Pages with extensive scriptlets become "spaghetti code" — interleaved HTML and Java is extremely difficult for developers to read, debug, and maintain.

3. **Not Web-Designer Friendly:** Web designers who work with HTML/CSS cannot easily work with JSP pages cluttered with Java code. They may accidentally break Java logic.

4. **No Reusability:** Logic embedded in scriptlets cannot be reused across multiple pages. A Java method in a class can be called from anywhere; a scriptlet is trapped in one page.

5. **Better Alternatives Exist:**
   - **JSTL (JSP Standard Tag Library)** and **EL (Expression Language)** provide tag-based and expression-based alternatives.
   - **Custom Tags** allow encapsulating logic in reusable tag components.
   - The **MVC pattern** moves all logic into Servlets and JavaBeans.

**Modern best practice:** JSP pages should contain **only** template text, EL expressions, and JSTL tags — **zero scriptlets**.

---

## 13. Three Major Phases of a Servlet Life Cycle. [5]

### Phase 1: Loading and Initialization
- The **Web Container loads** the Servlet class (either on first request or at server startup if `<load-on-startup>` is configured).
- A **single instance** of the Servlet is created.
- The container calls **`init(ServletConfig)`** exactly once.
- The Servlet reads initialization parameters and acquires resources (DB pools, etc.).
- After `init()` completes, the Servlet is ready to handle requests.

### Phase 2: Request Processing (Service)
- For **each client request**, the container creates a **new thread** and constructs `HttpServletRequest` and `HttpServletResponse` objects.
- The container invokes the **`service()`** method, which dispatches to **`doGet()`**, **`doPost()`**, `doPut()`, `doDelete()`, etc., based on the HTTP method.
- This phase repeats for the **entire lifetime** of the Servlet — multiple concurrent threads share the same Servlet instance.

### Phase 3: Destruction
- When the container decides to remove the Servlet (server shutdown, application undeployment, or resource reclamation), it calls **`destroy()`** exactly once.
- The Servlet releases all held resources (connections, file handles, threads).
- After `destroy()`, the instance is eligible for **garbage collection**.

```
[Load Class] → [init()] → [service()/doGet()/doPost()] × N → [destroy()] → [GC]
```

---

## 14. Why Is It Dangerous to Store Per-Request Data in Servlet Instance Variables? [5]

This is dangerous because Servlets follow a **single-instance, multi-threaded** model:

1. **One Servlet instance** is created by the container and shared across **all concurrent requests**.
2. Each request is served by a **separate thread**, but all threads access the **same instance variables**.
3. If per-request data (e.g., a user's name, a shopping cart item) is stored in an instance variable, **multiple threads will read and overwrite the same variable simultaneously**.

**Concrete Problem — Race Condition:**
```java
public class DangerServlet extends HttpServlet {
    private String username; // INSTANCE VARIABLE — SHARED!

    protected void doGet(HttpServletRequest req, HttpServletResponse resp) {
        username = req.getParameter("user"); // Thread A writes "Alice"
        // Thread B writes "Bob" (overwrites!)
        resp.getWriter().println("Hello " + username); // Thread A prints "Bob" — WRONG!
    }
}
```

**Consequences:**
- **Data corruption:** User A sees User B's data.
- **Security breach:** Sensitive information leaks across sessions.
- **Non-deterministic bugs:** Errors occur intermittently and are extremely hard to reproduce.

**Solution:** Always use **local variables** (stack-scoped, thread-safe), request attributes, or session attributes for per-request data.

---

## 15. Functional Differences Between `HttpServletRequest` and `HttpServletResponse`. [2.5+2.5]

**`HttpServletRequest` (2.5 marks):**
- Represents the **incoming HTTP request** from the client to the server.
- Used to **read/extract** information:
  - Request parameters: `getParameter("name")`
  - HTTP headers: `getHeader("User-Agent")`
  - Session: `getSession()`
  - Request attributes: `getAttribute()` / `setAttribute()`
  - HTTP method: `getMethod()`
  - Cookies: `getCookies()`
  - Request URI, context path, uploaded parts
- It is **read-oriented** — the Servlet consumes data from it.

**`HttpServletResponse` (2.5 marks):**
- Represents the **outgoing HTTP response** from the server to the client.
- Used to **write/set** information:
  - Response body: `getWriter().println(...)` or `getOutputStream()`
  - Content type: `setContentType("text/html")`
  - HTTP status code: `setStatus(200)`, `sendError(404)`
  - Response headers: `setHeader("Cache-Control", "no-cache")`
  - Cookies: `addCookie(cookie)`
  - Redirects: `sendRedirect("url")`
- It is **write-oriented** — the Servlet constructs the response through it.

| Aspect | `HttpServletRequest` | `HttpServletResponse` |
|--------|---------------------|----------------------|
| Direction | Client → Server (IN) | Server → Client (OUT) |
| Primary Action | Read/Extract data | Write/Set data |
| Data Flow | Contains what client sent | Contains what server sends back |

---

## 16. Routing `doGet` and `doPost` Through a Common `processRequest` Method. [2+3]

**Pattern (2 marks):**
```java
public class MyServlet extends HttpServlet {

    protected void processRequest(HttpServletRequest req, HttpServletResponse resp)
            throws ServletException, IOException {
        // Common logic for both GET and POST
        String action = req.getParameter("action");
        // ... business logic, forwarding, response writing
    }

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp)
            throws ServletException, IOException {
        processRequest(req, resp);
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp)
            throws ServletException, IOException {
        processRequest(req, resp);
    }
}
```

**Why This Is Useful (3 marks):**

1. **Eliminates code duplication:** Without this pattern, identical logic would need to be written in both `doGet()` and `doPost()`, violating the DRY (Don't Repeat Yourself) principle.

2. **Flexibility for clients:** A form can switch between `method="GET"` and `method="POST"` without requiring any Servlet code changes. AJAX calls using either method are also handled uniformly.

3. **Single maintenance point:** Bug fixes and feature additions are made in **one place** (`processRequest`), reducing the risk of inconsistencies between GET and POST handling.

4. **Cleaner code:** `doGet()` and `doPost()` become simple one-line delegators, improving readability.

---

## 17. What Is `web.xml`? List Two Configurations It Handles. [3+2]

**Definition (3 marks):**
`web.xml` is the **Deployment Descriptor** of a Java web application. It is an XML configuration file located at `/WEB-INF/web.xml`. It provides the Web Container with **declarative metadata** about how the application should be configured, which components to load, how URLs map to Servlets, and what security/filter rules to apply — **without modifying source code**. It allows externalizing configuration from code.

**Two Specific Configurations (2 marks):**

**1. Servlet Mapping:**
```xml
<servlet>
    <servlet-name>HelloServlet</servlet-name>
    <servlet-class>com.example.HelloServlet</servlet-class>
</servlet>
<servlet-mapping>
    <servlet-name>HelloServlet</servlet-name>
    <url-pattern>/hello</url-pattern>
</servlet-mapping>
```

**2. Welcome File List:**
```xml
<welcome-file-list>
    <welcome-file>index.html</welcome-file>
    <welcome-file>index.jsp</welcome-file>
</welcome-file-list>
```

*(Other valid: context parameters, filter configuration, error pages, session timeout, security constraints, listener declarations, load-on-startup)*

---

## 18. Contrast `ServletConfig` with `ServletContext`. [2.5+2.5]

| Aspect | `ServletConfig` | `ServletContext` |
|--------|-----------------|------------------|
| **Scope** | **Per-Servlet** — each Servlet has its own `ServletConfig` | **Per-Application** — one `ServletContext` shared by the entire web application |
| **Accessibility** | Only the Servlet it belongs to can access its init parameters | All Servlets, JSPs, and Filters in the application can access it |
| **Configuration** | `<init-param>` inside `<servlet>` in `web.xml` | `<context-param>` at the top level of `web.xml` |
| **Typical Use** | Servlet-specific settings: DB table name for a particular Servlet, template path | Application-wide settings: DB connection string, application name, global flags |
| **Retrieved via** | `getServletConfig()` or `getInitParameter()` | `getServletContext()` or `getServletConfig().getServletContext()` |
| **Attribute Sharing** | Cannot share attributes with other Servlets | Can share attributes across all components via `setAttribute()`/`getAttribute()` |

**Example:**
```xml
<!-- ServletConfig (per-servlet) -->
<servlet>
    <servlet-name>ReportServlet</servlet-name>
    <servlet-class>com.app.ReportServlet</servlet-class>
    <init-param>
        <param-name>reportFormat</param-name>
        <param-value>PDF</param-value>
    </init-param>
</servlet>

<!-- ServletContext (application-wide) -->
<context-param>
    <param-name>dbURL</param-name>
    <param-value>jdbc:mysql://localhost:3306/mydb</param-value>
</context-param>
```

---

## 19. Why Is Session Management Necessary? List Two Strategies. [3+2]

**Why Session Management Is Necessary (3 marks):**

HTTP is a **stateless protocol** — each request-response cycle is independent, and the server has **no built-in memory** of previous interactions with the same client. This means:

- The server cannot identify whether two successive requests come from the **same user**.
- Without session management, features like **login authentication**, shopping carts, multi-step forms, and user preferences would be **impossible**.
- Session management provides a mechanism to **maintain conversational state** across multiple HTTP requests, effectively creating a logical "session" for each user.

**Two Common Session Management Strategies (2 marks):**

1. **Cookies:** The server sends a small piece of data (e.g., `JSESSIONID`) in a `Set-Cookie` response header. The browser automatically sends it back with every subsequent request, allowing the server to identify the user.

2. **HttpSession (Server-side sessions):** The container creates a `HttpSession` object on the server, associates it with a session ID (typically tracked via a cookie or URL rewriting), and stores user-specific data in key-value pairs on the server side.

*(Other valid: URL Rewriting, Hidden Form Fields)*

---

## 20. Compare Cookies and HttpSession (Storage Location and Security). [2.5+2.5]

| Aspect | **Cookies** | **HttpSession** |
|--------|------------|----------------|
| **Storage Location** | Stored on the **client side** (browser). Data travels back and forth with every HTTP request in the `Cookie` header. | Stored on the **server side** (in server memory or persistent store). Only the **session ID** is sent to the client (via cookie or URL). |
| **Security** | **Less secure** — data is visible and modifiable by the user. Can be intercepted in transit (unless using HTTPS). Vulnerable to **XSS** attacks if not marked `HttpOnly`. Cookie tampering is possible. | **More secure** — actual data remains on the server and is never exposed to the client. The client only holds an opaque session ID. Server-side data cannot be directly tampered with by the user. |
| **Data Size** | Limited (~4 KB per cookie, ~20 cookies per domain) | Virtually unlimited (bounded by server memory) |
| **Data Types** | Only **String** key-value pairs | Any **Java Object** |
| **Lifetime** | Can persist beyond browser session (`setMaxAge()`) | Typically expires after inactivity timeout (default ~30 min) |

**Summary:** Cookies are client-stored and less secure; HttpSession is server-stored and more secure. For sensitive data (user roles, authentication tokens), always prefer `HttpSession`.

---

## 21. Servlet Chaining: `forward()` vs `include()`. [2+3]

**What Is Servlet Chaining? (2 marks):**
Servlet Chaining is the mechanism of **passing a request through multiple Servlets/JSPs** in a sequence, where the output or processing of one component feeds into another. It is achieved using the `RequestDispatcher` interface, allowing Servlets to collaborate in handling a single request.

**Differences (3 marks):**

| Aspect | `RequestDispatcher.forward()` | `RequestDispatcher.include()` |
|--------|------------------------------|-------------------------------|
| **Control Flow** | **Transfers control completely** to the target resource. The calling Servlet **cannot** write to the response after forwarding. | **Temporarily delegates** to the target resource, then control **returns** to the calling Servlet. |
| **Response Buffer** | Response buffer is **cleared** before forwarding (any prior output is discarded). | Response is **not cleared**; the included resource's output is **inserted** into the calling Servlet's output. |
| **Use Case** | Controller Servlet forwards to a JSP View (MVC pattern). | Including a common header/footer/sidebar into the current response. |
| **After Call** | Writing to `response` after `forward()` throws `IllegalStateException`. | The calling Servlet can continue writing output after `include()`. |

```java
// Forward — full delegation
RequestDispatcher rd = request.getRequestDispatcher("/result.jsp");
rd.forward(request, response);

// Include — partial insertion
RequestDispatcher rd = request.getRequestDispatcher("/header.jsp");
rd.include(request, response);
out.println("<p>Main content continues here</p>");
```

---

## 22. Purpose of a Servlet Filter. What If `chain.doFilter()` Is Omitted? [3+2]

**Purpose of a Servlet Filter (3 marks):**
A Servlet Filter is a reusable component that **intercepts HTTP requests and responses** before they reach the target Servlet (or after the response leaves it). Filters perform **cross-cutting concerns** including:

- **Logging and auditing** every request
- **Authentication/Authorization** checks
- **Input validation** and sanitization
- **Response compression** (GZIP)
- **Character encoding** (setting UTF-8)
- **CORS header injection**

Filters are configured in `web.xml` or via `@WebFilter` and form a **filter chain** — multiple filters execute in sequence.

**What Happens If `chain.doFilter()` Is Omitted? (2 marks):**
If `chain.doFilter(request, response)` is not called, the **request processing chain is broken**. The request will **never reach the target Servlet** (or the next filter in the chain). The client will receive either:
- An **empty response** (blank page), or
- Whatever the filter itself writes to the response.

This behavior is actually **intentionally useful** for blocking unauthorized requests:

```java
public void doFilter(ServletRequest req, ServletResponse resp, FilterChain chain)
        throws IOException, ServletException {
    if (!isAuthenticated(req)) {
        ((HttpServletResponse) resp).sendError(403, "Forbidden");
        return; // chain.doFilter() deliberately NOT called — request blocked
    }
    chain.doFilter(req, resp); // Only reached if authenticated
}
```

---

## 23. Code Snippet: Reading an Uploaded File Part Using `@MultipartConfig`. [5]

```java
import javax.servlet.*;
import javax.servlet.annotation.*;
import javax.servlet.http.*;
import java.io.*;

@WebServlet("/upload")
@MultipartConfig(
    fileSizeThreshold = 1024 * 1024,      // 1 MB threshold before writing to disk
    maxFileSize       = 1024 * 1024 * 10,  // 10 MB max per file
    maxRequestSize    = 1024 * 1024 * 50   // 50 MB max total request
)
public class FileUploadServlet extends HttpServlet {

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {

        // Retrieve the file part from the multipart request
        Part filePart = request.getPart("file"); // "file" matches <input name="file">

        // Extract the submitted file name
        String fileName = filePart.getSubmittedFileName();

        // Read the file content using InputStream
        InputStream fileContent = filePart.getInputStream();

        // Save to a destination
        String uploadPath = getServletContext().getRealPath("/uploads");
        File uploadDir = new File(uploadPath);
        if (!uploadDir.exists()) uploadDir.mkdirs();

        // Write the file
        filePart.write(uploadPath + File.separator + fileName);

        response.getWriter().println("File '" + fileName + "' uploaded successfully.");
    }
}
```

**Corresponding HTML form:**
```html
<form action="upload" method="POST" enctype="multipart/form-data">
    <input type="file" name="file" />
    <button type="submit">Upload</button>
</form>
```

---

## 24. Principle of File Download Using `Content-Disposition` Header. [5]

When a Servlet needs to send a file to the client for **download** (rather than inline display), it uses the `Content-Disposition` HTTP response header:

**Mechanism:**

1. **Set the Content-Type** to match the file type (or use `application/octet-stream` for generic binary to force download).
2. **Set the `Content-Disposition` header** to `attachment; filename="filename.ext"` — this instructs the browser to **open a "Save As" dialog** instead of displaying the file inline.
3. **Stream the file bytes** from the server's file system (or database) to the response's `OutputStream`.

```java
protected void doGet(HttpServletRequest req, HttpServletResponse resp)
        throws ServletException, IOException {

    String filePath = "/server/files/report.pdf";
    File file = new File(filePath);

    // Step 1: Set content type
    resp.setContentType("application/pdf");

    // Step 2: Set Content-Disposition to trigger download
    resp.setHeader("Content-Disposition", "attachment; filename=\"" + file.getName() + "\"");

    // Step 3: Set content length (optional but recommended)
    resp.setContentLengthLong(file.length());

    // Step 4: Stream the file to the client
    try (InputStream in = new FileInputStream(file);
         OutputStream out = resp.getOutputStream()) {
        byte[] buffer = new byte[4096];
        int bytesRead;
        while ((bytesRead = in.read(buffer)) != -1) {
            out.write(buffer, 0, bytesRead);
        }
    }
}
```

**Key Points:**
- `attachment` → triggers download dialog; `inline` → displays in browser
- Without `Content-Disposition`, the browser may try to render the file (e.g., display a PDF inside the browser tab)

---

## 25. Define "Object-Relational Impedance Mismatch." [5]

**Object-Relational Impedance Mismatch** refers to the set of **fundamental conceptual and technical incompatibilities** between the Object-Oriented (OO) programming model (as used in Java) and the Relational Database model (as used in SQL/RDBMS).

These two paradigms represent and manipulate data in fundamentally different ways:

| OO World (Java) | Relational World (RDBMS) |
|-----------------|-------------------------|
| Objects with behavior + state | Rows in tables with columns |
| Inheritance hierarchies | No native inheritance (flat tables) |
| Object references (pointers) | Foreign keys (IDs) |
| Collections (List, Set, Map) | Join tables, normalized relations |
| Identity = `==` or `.equals()` | Identity = Primary Key |
| Navigational access (`order.getCustomer()`) | Declarative joins (`JOIN ... ON`) |
| Encapsulation (private fields + methods) | All columns publicly accessible |

**Impact in Hibernate's Context:**
Hibernate (and JPA) exist specifically to **bridge this mismatch**. They act as an **ORM (Object-Relational Mapping)** layer that transparently translates between Java objects and relational tables, so developers can work in a pure OO style while Hibernate handles the SQL translation behind the scenes.

---

## 26. Four Structural Incompatibilities Between Java OO and Relational Models. [5]

| # | Incompatibility | Java (OO) | RDBMS (Relational) |
|---|----------------|-----------|---------------------|
| 1 | **Granularity** | Fine-grained object models with many small classes (e.g., `Address` as a separate class embedded in `Person`) | Fewer, larger tables; no concept of embedding an object type within a row natively |
| 2 | **Inheritance / Subtyping** | Natural class hierarchies (`Animal → Dog → GoldenRetriever`) using `extends` | No native inheritance; must be simulated using strategies: single table, table-per-class, or joined tables |
| 3 | **Identity** | Two concepts: reference identity (`==`) and value equality (`.equals()`/`.hashCode()`) | Single concept: **primary key** equality |
| 4 | **Associations / Relationships** | Object references are **unidirectional** by default; bidirectional requires explicit code in both classes; uses direct references (`customer.getOrders()`) | Foreign keys are inherently **bidirectional** (can be queried from either side via JOINs); associations rely on FK columns, not object pointers |

*(Additional valid: navigational vs. declarative access, data type mismatches, encapsulation differences)*

---

## 27. Hibernate's "Transparent" and "Persistence" Concepts. [2.5+2.5]

**Transparent (2.5 marks):**
"Transparent" means that Hibernate operates **without requiring changes to the Java domain classes themselves**. The POJO (Plain Old Java Object) classes:
- Do **not** need to extend any Hibernate-specific superclass.
- Do **not** need to implement any special interface.
- Remain **completely unaware** of the persistence mechanism.
- Can be tested and used **outside** of Hibernate (in unit tests, other frameworks).

The persistence logic is kept **separate** from the business model — either via XML mapping files or annotations (which are metadata, not behavioral changes).

**Persistence (2.5 marks):**
"Persistence" means that Hibernate **automatically manages the storage and retrieval of Java objects to/from a relational database**. Specifically:
- Java objects (entities) can be **saved**, **loaded**, **updated**, and **deleted** from the database without the developer writing SQL manually.
- Hibernate tracks changes to objects (**dirty checking**) and synchronizes them with the database at the appropriate time (flush/commit).
- The object's state **survives beyond** the JVM process — it is stored permanently in the database.

**Together:** "Transparent Persistence" = Your Java objects are persisted to a database without the objects needing to know anything about how that happens.

---

## 28. How Hibernate Achieves Database Portability Through Dialects. [5]

Hibernate achieves database portability through its **Dialect** system, which abstracts away **vendor-specific SQL differences**:

**Mechanism:**

1. Each RDBMS (MySQL, PostgreSQL, Oracle, SQL Server, etc.) has its own **SQL syntax variations** — data types, pagination, auto-increment, identity generation, function names, and DDL syntax differ significantly.

2. Hibernate provides a **Dialect class for each database** (e.g., `org.hibernate.dialect.MySQLDialect`, `org.hibernate.dialect.PostgreSQLDialect`, `org.hibernate.dialect.OracleDialect`).

3. Each Dialect class encapsulates **all vendor-specific SQL details**:
   - How to generate primary keys (AUTO_INCREMENT vs. SEQUENCE vs. IDENTITY)
   - How to paginate results (LIMIT/OFFSET vs. ROWNUM vs. FETCH FIRST)
   - Native data type mappings (VARCHAR vs. VARCHAR2)
   - Lock syntax, function translations, etc.

4. The developer writes **only HQL (Hibernate Query Language)** or uses the Criteria API — which are **database-independent**.

5. At runtime, Hibernate's Dialect translates these into the **correct native SQL** for the configured database.

**Switching Databases:**
To switch from MySQL to PostgreSQL, the developer only changes **one line** in the configuration:
```xml
<!-- Before -->
<property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>

<!-- After -->
<property name="hibernate.dialect">org.hibernate.dialect.PostgreSQLDialect</property>
```

No application code or HQL queries need to change.

---

## 29. Compare Plain JDBC with Hibernate (Schema Changes and Code Volume). [2.5+2.5]

**Schema Changes (2.5 marks):**

| Aspect | Plain JDBC | Hibernate |
|--------|-----------|-----------|
| When a column is added/renamed/removed | **Every SQL query** referencing that table must be **manually located and updated** throughout the codebase | Only the **entity mapping** (annotation or XML) needs to be updated; HQL queries reference properties, not columns |
| Risk | High risk of **missing a query**, leading to runtime `SQLException` | Centralized mapping changes; compile-time or startup-time detection of issues |
| DDL Management | Developer manually writes `ALTER TABLE` scripts | `hibernate.hbm2ddl.auto` can **automatically update** the schema |

**Code Volume (2.5 marks):**

| Aspect | Plain JDBC | Hibernate |
|--------|-----------|-----------|
| For a simple CRUD operation | 30-50+ lines: open connection, create statement, write SQL, set parameters, execute, iterate ResultSet, map to object, handle exceptions, close resources in `finally` | 2-5 lines: `session.save(obj)`, `session.get(Class, id)`, `session.update(obj)`, `session.delete(obj)` |
| Boilerplate | Massive repetitive boilerplate for every query | Hibernate eliminates ~80-90% of data access boilerplate |
| SQL | Written manually, inline as Strings | Auto-generated from mappings; developer writes HQL only when needed |

**Example — Loading a User by ID:**
```java
// JDBC: ~20 lines
Connection conn = DriverManager.getConnection(url, user, pass);
PreparedStatement ps = conn.prepareStatement("SELECT * FROM users WHERE id = ?");
ps.setInt(1, userId);
ResultSet rs = ps.executeQuery();
if (rs.next()) {
    User u = new User();
    u.setId(rs.getInt("id"));
    u.setName(rs.getString("name"));
    // ... more fields
}
rs.close(); ps.close(); conn.close();

// Hibernate: 1 line
User u = session.get(User.class, userId);
```

---

## 30. First Four Manual Steps to Load a Single Row Using Plain JDBC. [5]

```java
// Step 1: Load the JDBC Driver
Class.forName("com.mysql.cj.jdbc.Driver");

// Step 2: Establish a Connection to the database
Connection conn = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/mydb", "username", "password"
);

// Step 3: Create a PreparedStatement with the SQL query
PreparedStatement ps = conn.prepareStatement(
    "SELECT id, name, email FROM users WHERE id = ?"
);
ps.setInt(1, 101); // Bind the parameter

// Step 4: Execute the query and obtain a ResultSet
ResultSet rs = ps.executeQuery();
```

**Summary of the four steps:**
1. **Load the JDBC Driver** — `Class.forName("...")`
2. **Open a Connection** — `DriverManager.getConnection(url, user, pass)`
3. **Create a Statement** — `conn.prepareStatement(sql)` and bind parameters
4. **Execute the Query** — `ps.executeQuery()` to get the `ResultSet`

*(Subsequent steps would involve: iterating the ResultSet, mapping columns to Java object fields, closing ResultSet/Statement/Connection in finally blocks.)*

---

## 31. Role of the `SessionFactory` in Hibernate Architecture. [5]

The `SessionFactory` is a **heavyweight, thread-safe, immutable factory object** that serves as the central hub of the Hibernate persistence infrastructure:

1. **Creates `Session` objects:** Its primary role is to produce lightweight `Session` instances via `sessionFactory.openSession()` or `sessionFactory.getCurrentSession()`.

2. **Holds all compiled mappings:** During construction, it reads and compiles all entity mappings (XML or annotations) into an internal optimized representation. This is why it is expensive to create.

3. **Manages the Second-Level Cache:** It owns and coordinates the optional second-level cache (shared across all sessions), improving performance by caching frequently accessed entities.

4. **Connection Pool Management:** It manages the underlying **database connection pool** (e.g., C3P0, HikariCP) and provides connections to `Session` objects.

5. **One per database:** Typically, there is **one `SessionFactory` per database** (per `DataSource`) in an application. It is created once at application startup and reused for the entire application lifecycle.

6. **Immutable configuration:** Once built, its configuration (dialect, mappings, settings) cannot be changed. To modify configuration, a new `SessionFactory` must be built.

```java
// Created ONCE at application startup
SessionFactory sessionFactory = new Configuration()
    .configure("hibernate.cfg.xml")
    .buildSessionFactory();

// Used throughout the application
Session session = sessionFactory.openSession();
```

---

## 32. Why Is `SessionFactory` Thread-Safe but `Session` Is Not? [5]

**`SessionFactory` — Thread-Safe:**

- The `SessionFactory` is **immutable** after construction — it holds read-only compiled mappings, configuration settings, and cache structures.
- Since its internal state **never changes** after initialization, multiple threads can safely access it concurrently without synchronization issues.
- It is designed to be a **shared, long-lived singleton** — one per application.
- Its thread safety is essential because the entire application (all user requests) shares the same `SessionFactory`.

**`Session` — Intentionally Not Thread-Safe:**

- The `Session` represents a **single unit of work** (a conversation with the database) — analogous to a single JDBC connection.
- It maintains **mutable internal state**:
  - **First-level cache (Persistence Context):** Tracks all loaded/managed entities
  - **Dirty-checking state:** Tracks which entities have been modified
  - **Action queue:** Pending SQL operations to be flushed
  - **JDBC connection reference:** One connection bound to the session
- If two threads shared the same `Session`, they could:
  - Corrupt the first-level cache
  - Cause conflicting flushes
  - Produce inconsistent transaction boundaries
- **Design pattern:** Each thread (each HTTP request) should have its **own `Session`** — typically opened at request start and closed at request end.

```
Application (many threads) ──→ ONE SessionFactory (shared, thread-safe)
    Thread A ──→ Session A (private, not thread-safe)
    Thread B ──→ Session B (private, not thread-safe)
    Thread C ──→ Session C (private, not thread-safe)
```

---

## 33. Layered View of Hibernate Architecture. [5]

```
┌──────────────────────────────┐
│      Application Code        │  ← Domain objects, business logic, DAOs
│   (POJOs / Entity Classes)   │
├──────────────────────────────┤
│     Hibernate Framework      │
│  ┌────────────────────────┐  │
│  │   Session Interface    │  │  ← Unit of work, first-level cache, CRUD API
│  ├────────────────────────┤  │
│  │  SessionFactory        │  │  ← Factory for sessions, second-level cache
│  ├────────────────────────┤  │
│  │  Transaction API       │  │  ← Abstracts JTA/JDBC transactions
│  ├────────────────────────┤  │
│  │  Query (HQL/Criteria)  │  │  ← Object-oriented query mechanism
│  ├────────────────────────┤  │
│  │  Configuration         │  │  ← Reads mapping + config files
│  └────────────────────────┘  │
├──────────────────────────────┤
│       JDBC / JTA Layer       │  ← Standard Java database connectivity
├──────────────────────────────┤
│          RDBMS               │  ← MySQL, PostgreSQL, Oracle, etc.
│   (Relational Database)      │
└──────────────────────────────┘
```

**Layer Descriptions:**
1. **Application Code:** Contains POJOs/entities and business logic. Interacts only with Hibernate APIs.
2. **Hibernate Framework:** The ORM engine — manages mapping, caching, query translation, and transaction coordination. Shields the application from JDBC complexity.
3. **JDBC/JTA Layer:** Hibernate internally uses JDBC to communicate with the database. The developer never touches JDBC directly.
4. **RDBMS:** The actual relational database where data is permanently stored.

---

## 34. Hibernate's "Transaction-Aware Flushing" Mechanism. [5]

**Transaction-aware flushing** is Hibernate's mechanism of **synchronizing the in-memory state** (Persistence Context / first-level cache) **with the database at strategically optimal times**, primarily tied to the transaction lifecycle:

**How It Works:**

1. When you modify entities within a `Session` (via `save()`, `update()`, `delete()`, or by modifying properties of managed entities), Hibernate **does not immediately execute SQL**.

2. Instead, changes are **queued** in the Session's action queue within the Persistence Context.

3. Hibernate **flushes** (sends SQL to the database) at specific trigger points:
   - **Before a transaction commits** — `transaction.commit()` triggers a flush, ensuring all changes are written to the DB before the commit.
   - **Before a query executes** — If you run an HQL/Criteria query, Hibernate flushes first to ensure the query sees up-to-date data.
   - **Explicit flush** — `session.flush()` called manually.

4. During a flush, Hibernate performs **dirty checking** — it compares the current state of each managed entity against a **snapshot** taken when the entity was first loaded. Only **actually modified** entities generate UPDATE SQL statements.

**Benefits:**
- **Minimizes database round-trips:** Multiple changes are batched into a single flush.
- **Ensures data consistency:** The database is always in sync before queries or commits.
- **Automatic optimization:** Unnecessary UPDATEs are avoided via dirty checking.

```java
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();

User user = session.get(User.class, 1);  // SQL SELECT
user.setName("Alice");                    // No SQL yet — just in-memory change
user.setEmail("alice@new.com");           // No SQL yet

tx.commit(); // FLUSH happens here → single UPDATE SQL is generated
session.close();
```

---

## 35. How Hibernate Implements "Lazy Loading" Using Proxies. [5]

**Lazy Loading** is Hibernate's strategy to **defer the loading of associated entities or collections** until they are actually accessed, thereby avoiding unnecessary database queries.

**Proxy Mechanism:**

1. When an entity has an association (e.g., `Order` has a `@ManyToOne Customer`), Hibernate does **not** immediately load the associated `Customer` when loading the `Order`.

2. Instead, Hibernate creates a **proxy object** — a dynamically generated subclass of `Customer` (using bytecode libraries like **Byte Buddy** or formerly **CGLIB/Javassist**).

3. This proxy object:
   - Has the **same class type** as `Customer` (so `instanceof` checks pass)
   - Contains only the **primary key (ID)** of the associated entity
   - **Intercepts all method calls** (except `getId()`)

4. When the application first accesses a property of the proxy (e.g., `order.getCustomer().getName()`), the proxy's **interceptor fires a SQL SELECT** query to load the real data from the database. This is called **proxy initialization**.

5. After initialization, the proxy delegates all subsequent calls to the loaded real data — no further SQL.

**Example:**
```java
Order order = session.get(Order.class, 1);
// order.customer is a PROXY — no SELECT for customer yet

String name = order.getCustomer().getName();
// NOW the proxy fires: SELECT * FROM customer WHERE id = ?
// Subsequent calls use the cached data
```

**Collections:** Similarly, collections (`@OneToMany List<OrderItem>`) are wrapped in **lazy collection proxies** (`PersistentBag`, `PersistentSet`). The actual items are loaded only when the collection is iterated or its `size()` is called.

**Caveat — `LazyInitializationException`:** If the `Session` is closed before the proxy is accessed, Hibernate throws this exception because it can no longer execute the query.

---

## 36. Model 1 vs. Model 2 Architectures. [2.5+2.5]

**Model 1 — Page-Centric (2.5 marks):**
- **JSP pages handle everything:** request processing, business logic, data access, AND presentation — all within the same JSP file.
- Each JSP page is directly accessed by the client URL.
- Control flow: `Client → JSP (does everything) → Response`
- No separate controller. The JSP itself determines what to do based on parameters.
- **Pros:** Simple for very small applications.
- **Cons:** Mixes concerns horribly; unscalable; difficult to maintain; spaghetti code.

**Model 2 — MVC Dispatcher-Centric (2.5 marks):**
- Follows the **MVC (Model-View-Controller)** pattern with clear separation:
  - **Controller (Servlet):** Receives all requests, processes parameters, invokes business logic, selects the view.
  - **Model (JavaBeans/POJOs):** Contains business data and logic.
  - **View (JSP):** Only renders the HTML presentation using data provided by the controller.
- Control flow: `Client → Controller Servlet → Model → Controller → View JSP → Response`
- Client **never directly accesses** JSP pages.
- **Pros:** Clean separation of concerns; scalable; testable; maintainable; team-friendly (designers work on JSPs, developers work on Servlets).

| Aspect | Model 1 | Model 2 |
|--------|---------|---------|
| Central control | No (each JSP is independent) | Yes (Controller Servlet) |
| Separation of concerns | Poor | Excellent |
| Scalability | Low | High |
| JSP responsibility | Everything | Only presentation |

---

## 37. Typical Java Artifacts for Model, View, and Controller in MVC. [5]

| MVC Component | Typical Java Artifacts |
|--------------|----------------------|
| **Model** | **JavaBeans / POJOs** (data carriers with getters/setters), **Entity Classes** (JPA/Hibernate annotated), **Service Classes** (business logic), **DAO Classes** (Data Access Objects for DB interaction) |
| **View** | **JSP (JavaServer Pages)** with JSTL and EL expressions, **HTML/CSS/JavaScript** templates, **Facelets** (in JSF), **Thymeleaf** templates |
| **Controller** | **HttpServlet** classes (annotated with `@WebServlet`), **Front Controller Servlet** (single entry point), **Framework Controllers** (e.g., Spring `@Controller` classes) |

**Typical Request Flow with Artifacts:**
```
Browser Request
    → Controller Servlet (HttpServlet)
        → Service Class (business logic)
            → DAO Class (data access)
                → Entity/POJO (data carrier)
    ← Controller sets Model data as request attributes
    → Forward to View JSP
        → JSP renders HTML using JSTL/EL from Model attributes
    ← HTML Response to Browser
```

---

## 38. Post/Redirect/Get (PRG) Idiom. What Bug Does It Prevent? [2+3]

**Explanation of PRG (2 marks):**
Post/Redirect/Get is a web development pattern where:
1. Client submits a form via **POST**.
2. Server processes the form, then responds with an **HTTP 302/303 Redirect** (not a forward, not direct HTML).
3. Browser follows the redirect and issues a new **GET** request to the specified URL.
4. The GET request displays the success/result page.

```
Client ──POST──→ Server (processes data)
Client ←─302 Redirect─ Server
Client ──GET──→ Server (displays result page)
```

**What Bug Does It Prevent? (3 marks):**

PRG prevents the **Duplicate Form Submission** bug:

- Without PRG: After a POST, the server returns the result page directly. If the user **refreshes the browser** (F5), the browser re-sends the **same POST request**, causing:
  - **Duplicate database inserts** (e.g., double order placement, double payment)
  - **Duplicate email notifications**
  - **Duplicate transactions**
  - The browser often shows a "Confirm Form Resubmission" warning dialog, confusing users.

- With PRG: After the redirect, the browser's last request is a **GET**. Refreshing the page simply re-executes the harmless GET, not the destructive POST. The form submission cannot be accidentally repeated.

- **Bonus:** PRG also produces a **clean, bookmarkable URL** in the address bar (the GET URL), rather than leaving a POST URL that can't be meaningfully bookmarked or shared.

---

## 39. `forward()` vs `sendRedirect()` — HTTP Round-Trips and URL Bar. [2.5+2.5]

| Aspect | `forward()` (Server-Side) | `sendRedirect()` (Client-Side) |
|--------|--------------------------|-------------------------------|
| **HTTP Round-Trips** | **One** round-trip. The forwarding happens entirely **within the server**. The client is unaware that a forward occurred. | **Two** round-trips. First: server sends 302 response. Second: browser sends new GET request to the redirect URL. |
| **URL in Address Bar** | **Does NOT change.** The browser still shows the **original request URL** because the client doesn't know about the internal forward. | **Changes** to the **new redirected URL.** The browser is fully aware of the new location. |
| **Request/Response Objects** | The **same** `HttpServletRequest` and `HttpServletResponse` objects are shared with the target resource. Request attributes are preserved. | A **brand new** request is created by the browser. All original request attributes and parameters are **lost** (unless passed via query string or session). |
| **Scope** | Can only forward to resources **within the same web application.** | Can redirect to **any URL** — same app, different app, or entirely different domain. |
| **Performance** | **Faster** — no extra network round-trip. | **Slower** — requires an additional HTTP request/response cycle. |
| **Typical Use** | Controller → JSP (internal MVC routing) | PRG pattern, cross-application navigation, post-login redirects |

```java
// Forward (server-side) — 1 round-trip, URL stays same
request.getRequestDispatcher("/result.jsp").forward(request, response);

// Redirect (client-side) — 2 round-trips, URL changes
response.sendRedirect("success.jsp");
```

---

## 40. Advantage of Placing View JSPs Under `/WEB-INF/`. [5]

The core architectural advantage is **enforcing Controller-mediated access** and **preventing direct client access** to View JSPs:

**How it works:**

The Servlet specification states that files under `/WEB-INF/` are **not directly accessible** via URL by clients. A browser request to `http://server/app/WEB-INF/views/user.jsp` will return a **404 error**.

**Architectural advantages:**

1. **Forces MVC discipline:** Every request **must** go through the Controller Servlet first. The Controller processes business logic, sets model attributes, and then **internally forwards** to the JSP. There is no way for users to bypass the controller.

2. **Security:** Prevents users from accessing JSP pages directly, which could:
   - Display **empty or broken pages** (since model data wouldn't be set)
   - Expose **internal application structure** and potentially sensitive information
   - Bypass **authentication and authorization** checks that the controller enforces

3. **Eliminates a class of bugs:** Since JSPs always receive properly prepared model data from the controller, there are no cases where a JSP runs with null/missing request attributes.

4. **Clean URL design:** Public URLs map only to Servlet endpoints (`/users`, `/orders`), not to implementation files (`user.jsp`).

```
/WEB-INF/
    /views/
        userList.jsp      ← NOT directly accessible
        userForm.jsp      ← NOT directly accessible
        error.jsp         ← NOT directly accessible

// Only the Controller can reach them:
request.getRequestDispatcher("/WEB-INF/views/userList.jsp").forward(req, resp);
```

---

## 41. Function of a Web Container in JSP Execution. Name Two Common Containers. [3+2]

**Primary Function (3 marks):**
A Web Container (also called Servlet Container) is responsible for the **complete lifecycle management** of JSP pages:

1. **Translation:** Converts the `.jsp` file into a Java Servlet source file (`.java`).
2. **Compilation:** Compiles the generated Servlet source into bytecode (`.class`).
3. **Class Loading & Instantiation:** Loads the compiled class, creates an instance, and calls `jspInit()`.
4. **Request Dispatching:** For each incoming request, creates a thread and invokes the `_jspService()` method on the generated Servlet.
5. **Lifecycle Management:** Handles initialization, re-translation when JSP is modified, and destruction (`jspDestroy()`).
6. **Provides implicit objects:** Supplies `request`, `response`, `session`, `out`, `application`, `config`, etc.

**Two Common Web Containers (2 marks):**

1. **Apache Tomcat** — The most widely used open-source Servlet/JSP container, maintained by the Apache Software Foundation.
2. **Eclipse Jetty** — Lightweight, embeddable Servlet container, popular for microservices and embedded deployments.

*(Other valid: GlassFish, WildFly/JBoss, IBM WebSphere, Oracle WebLogic, Undertow)*

---

## 42. Why Do Web Designers Find Servlets Difficult Compared to JSP? [5]

Web designers find Servlets difficult to maintain because:

1. **HTML is embedded inside Java code:** In a Servlet, HTML is written using `out.println("<html>...")` statements. Designers must navigate through Java syntax, string concatenation, escape characters, and programming constructs just to find and modify the visual layout.

```java
// Servlet — designer-hostile
out.println("<table class=\"user-table\">");
out.println("<tr><td>" + user.getName() + "</td></tr>");
out.println("</table>");
```

2. **No visual design tool support:** HTML inside `println()` strings cannot be rendered or previewed by web design tools (Dreamweaver, VS Code live preview, etc.). Designers work blind.

3. **Compilation required:** Any change — even a minor HTML tweak like changing a CSS class — requires **recompiling** the Java Servlet and **redeploying** the application. JSP pages, by contrast, are automatically retranslated on the next request.

4. **Not the designer's skill set:** Web designers know HTML, CSS, and JavaScript — not Java. Asking them to modify Java classes, handle exceptions, and understand inheritance is outside their expertise.

5. **No separation of concerns:** Servlet-based presentation mixes logic with markup, making it impossible for designers and developers to work on the same component independently.

**JSP's advantage:** JSP pages look like HTML with embedded tags (`${}`, `<c:forEach>`), allowing designers to work on presentation while developers handle logic in Servlets and beans.

---

## 43. How Does `_jspService()` Handle Multiple Concurrent Requests? [5]

The `_jspService()` method handles concurrent requests using a **single-instance, multi-threaded** model:

1. **One Servlet Instance:** The Web Container creates only **one instance** of the generated Servlet class for each JSP page.

2. **Thread Per Request:** When multiple clients request the same JSP simultaneously, the container allocates a **separate thread** for each request. Each thread calls the **same** `_jspService()` method on the **same** Servlet instance concurrently.

3. **Thread Safety via Local Variables:** The `_jspService()` method declares all implicit objects (`request`, `response`, `session`, `out`, `pageContext`) as **local variables**:
   ```java
   public void _jspService(HttpServletRequest request, HttpServletResponse response)
           throws ServletException, IOException {
       JspWriter out = null;          // LOCAL — thread-safe
       HttpSession session = null;     // LOCAL — thread-safe
       PageContext pageContext = null;  // LOCAL — thread-safe
       // ...
   }
   ```
   Since local variables exist on each **thread's own stack**, they are inherently **thread-safe** — each thread has its own copy.

4. **Danger with Declarations:** Variables and methods declared using `<%! ... %>` (JSP declarations) become **instance variables/methods** of the Servlet class — shared across all threads. These are **NOT thread-safe** and can cause data corruption if used for per-request data.

5. **Effective concurrency:** This model allows the container to serve **thousands of concurrent requests** efficiently with minimal memory overhead (threads are lighter than separate instances).

---

## 44. JSP Declaration Block Defining a Simple Java Method. [5]

```jsp
<%!
    public int calculate(int a) {
        // Example: returns the square of the input
        return a * a;
    }
%>
```

**Usage in the JSP page:**
```jsp
<html>
<body>
    <h2>Calculation Result</h2>
    <p>The square of 5 is: <%= calculate(5) %></p>
    <p>The square of 12 is: <%= calculate(12) %></p>
</body>
</html>
```

**Explanation:**
- The `<%! ... %>` tag is a **JSP Declaration** — code placed inside it becomes part of the **class body** of the generated Servlet (not inside `_jspService()`).
- This means `calculate()` becomes a **method of the Servlet class**, callable from scriptlets and expressions.
- Unlike scriptlets, declarations can define **instance methods** and **instance variables**.
- **Note:** Since this method is an instance method shared across threads, it must be **stateless** (no instance variable access) to remain thread-safe — this example is safe because it only uses its local parameter.

---

## 45. Three Typical HTTP Status Codes and Their Meanings. [5]

| Status Code | Name | Meaning |
|-------------|------|---------|
| **200** | **OK** | The request was **successful**. The server has processed the request and returned the expected resource or data in the response body. This is the standard response for successful GET, POST, PUT requests. |
| **404** | **Not Found** | The requested resource **does not exist** on the server. The URL does not map to any Servlet, JSP, or static file. Common causes: typo in URL, deleted resource, incorrect URL mapping in `web.xml`. |
| **500** | **Internal Server Error** | The server encountered an **unexpected error** while processing the request. This typically indicates an unhandled exception in the Servlet/JSP (e.g., `NullPointerException`, database connection failure, uncaught `RuntimeException`). |

**Additional commonly tested codes:**

| Code | Name | Meaning |
|------|------|---------|
| 301 | Moved Permanently | Resource permanently moved to a new URL |
| 302 | Found (Redirect) | Temporary redirect — used in PRG pattern |
| 403 | Forbidden | Server understood the request but refuses to authorize it |
| 405 | Method Not Allowed | HTTP method (e.g., POST) is not supported for this URL |

**Usage in Servlet code:**
```java
response.setStatus(HttpServletResponse.SC_OK);              // 200
response.sendError(HttpServletResponse.SC_NOT_FOUND);        // 404
response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR); // 500
```

---

## 46. How to Invalidate a Session and Why It's Critical During Logout. [5]

**How to Invalidate a Session:**
```java
protected void doPost(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {

    // Step 1: Get the existing session (don't create a new one)
    HttpSession session = request.getSession(false);

    // Step 2: Invalidate the session if it exists
    if (session != null) {
        session.invalidate(); // Destroys the session and all its attributes
    }

    // Step 3: Optionally clear the session cookie
    Cookie cookie = new Cookie("JSESSIONID", "");
    cookie.setMaxAge(0);  // Delete the cookie
    cookie.setPath("/");
    response.addCookie(cookie);

    // Step 4: Redirect to login page (PRG pattern)
    response.sendRedirect("login.jsp");
}
```

**Why It Is Critical During Logout:**

1. **Prevents Session Hijacking:** If the session is not invalidated, the session ID remains valid. An attacker who obtained the session ID (via XSS, sniffing, or shared computers) can continue to use it to impersonate the user.

2. **Clears Sensitive Data:** `session.invalidate()` immediately removes all session attributes (user credentials, roles, personal data, authentication tokens) from server memory.

3. **Prevents Unauthorized Access:** Without invalidation, pressing the **browser back button** or revisiting a protected URL could still work because the session is still active on the server.

4. **Resource Cleanup:** Frees server-side memory allocated for the session and its associated objects.

5. **Compliance & Best Practice:** Security standards (OWASP, PCI-DSS) require proper session termination during logout to prevent session fixation and reuse attacks.

---

## 47. Security Concerns (Path Traversal) in Multipart File Uploads. [5]

When handling multipart file uploads, several critical security concerns must be addressed:

### 1. Path Traversal Attack (Directory Traversal)
- An attacker submits a filename like `../../../etc/passwd` or `..\..\..\windows\system32\config`.
- If the server blindly uses this filename to save the file, the attacker can **overwrite arbitrary files** on the server.
- **Mitigation:** Always **sanitize the filename** — strip path separators, use only the base filename:
```java
String fileName = Paths.get(part.getSubmittedFileName()).getFileName().toString();
// Removes all path components, leaving only the file name
```

### 2. Unrestricted File Type Upload
- Attacker uploads a `.jsp`, `.sh`, or `.exe` file which could be executed on the server.
- **Mitigation:** Validate file extensions and MIME types against a **whitelist** (e.g., only `.jpg`, `.png`, `.pdf`). Never rely solely on the client-provided Content-Type.

### 3. File Size Denial of Service (DoS)
- Attacker uploads extremely large files to exhaust server disk space or memory.
- **Mitigation:** Use `@MultipartConfig` limits: `maxFileSize` and `maxRequestSize`. Reject oversized files.

### 4. Filename Collisions / Overwriting
- A user uploads a file with the same name as an existing file, overwriting it.
- **Mitigation:** Generate **unique filenames** (UUID + original extension) instead of using the original name.

### 5. Storage Location Security
- Files saved within the web application's document root could be **directly accessed via URL**.
- **Mitigation:** Store uploaded files **outside the web root** or under `/WEB-INF/` where they cannot be directly accessed.

---

## 48. Two Configuration Styles in Hibernate (XML vs. Annotations). [2.5+2.5]

**XML-Based Configuration (2.5 marks):**
- Uses **external XML files** to define entity-to-table mappings.
- Two types of XML files:
  - `hibernate.cfg.xml` — main configuration (DB connection, dialect, properties)
  - `EntityName.hbm.xml` — per-entity mapping files
- Mapping is **completely separate** from Java code — POJOs remain 100% clean.
- Changes to mapping can be made **without recompiling** Java code.

```xml
<!-- User.hbm.xml -->
<hibernate-mapping>
    <class name="com.example.User" table="users">
        <id name="id" column="user_id">
            <generator class="identity"/>
        </id>
        <property name="name" column="user_name" type="string"/>
        <property name="email" column="email" type="string"/>
    </class>
</hibernate-mapping>
```

**Annotation-Driven Configuration (2.5 marks):**
- Uses **JPA/Hibernate annotations** directly in the Java entity classes.
- Annotations like `@Entity`, `@Table`, `@Id`, `@Column`, `@GeneratedValue` are placed on the class and its fields/methods.
- Mapping is **co-located with the code** — easier to read and maintain since everything is in one place.
- More **concise** and the modern, preferred approach.

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "user_id")
    private int id;

    @Column(name = "user_name")
    private String name;

    @Column(name = "email")
    private String email;

    // Getters and setters
}
```

| Aspect | XML | Annotations |
|--------|-----|-------------|
| Location | External `.hbm.xml` files | Inside Java class |
| POJO cleanliness | 100% clean | Has annotation metadata |
| Verbosity | More verbose | More concise |
| Modern preference | Legacy | Preferred |
| Change without recompile | Yes | No |

---

## 49. Significance of `hibernate.hbm2ddl.auto` in Schema Management. [5]

The `hibernate.hbm2ddl.auto` configuration parameter controls **how Hibernate manages the database schema** (tables, columns, constraints) at **application startup**. It determines whether Hibernate should automatically create, update, validate, or drop the schema based on the entity mappings.

**Possible Values:**

| Value | Behavior |
|-------|----------|
| **`create`** | **Drops** all existing tables and **creates** new tables every time the SessionFactory starts. ⚠️ All data is destroyed. |
| **`create-drop`** | Same as `create`, but also **drops** all tables when the SessionFactory is **closed** (application shutdown). Used for unit testing. |
| **`update`** | **Compares** existing schema with entity mappings and **adds** new columns/tables. Does NOT remove existing columns. Data is preserved. |
| **`validate`** | Only **validates** that the existing schema matches entity mappings. Throws an exception if there's a mismatch. Makes **no changes** to the database. |
| **`none`** | Hibernate does nothing — schema management is completely manual. |

**Significance:**
1. **Development speed:** `update` or `create` during development eliminates manual DDL scripting — schema evolves automatically with entity changes.
2. **Testing:** `create-drop` ensures a **clean database** for each test run.
3. **Production safety:** `validate` or `none` must be used in production to prevent accidental data loss or unintended schema modifications.
4. **Bootstrap flow:** This parameter is one of the first things processed during `SessionFactory` construction, before any entity operations.

```xml
<!-- Development -->
<property name="hibernate.hbm2ddl.auto">update</property>

<!-- Production -->
<property name="hibernate.hbm2ddl.auto">validate</property>
```

---

## 50. What Is HQL and How Does Its Syntax Differ from Native SQL? [5]

**What Is HQL (Hibernate Query Language)?**

HQL is Hibernate's **object-oriented query language** that allows developers to write queries against **entity classes and their properties** rather than database tables and columns. It is syntactically similar to SQL but operates at the **object model level**.

**Fundamental Syntax Differences:**

| Aspect | HQL | Native SQL |
|--------|-----|-----------|
| **Operates on** | Java **entity classes** and their **property names** | Database **tables** and **column names** |
| **FROM clause** | Entity class name: `FROM User u` | Table name: `FROM users u` |
| **SELECT references** | Object properties: `SELECT u.firstName` | Column names: `SELECT first_name` |
| **Associations** | Object navigation: `u.department.name` | JOIN with foreign keys: `JOIN departments d ON u.dept_id = d.id` |
| **Polymorphism** | Supports polymorphic queries: `FROM Animal` returns Dogs, Cats, etc. | No inheritance concept |
| **Database independence** | HQL is **database-agnostic** — Hibernate translates it to native SQL via Dialect | SQL is vendor-specific |
| **Returns** | **Objects** (entity instances or projections) | **ResultSets** (rows of raw data) |

**Example Comparison:**
```sql
-- Native SQL (MySQL-specific)
SELECT u.user_name, u.email_address
FROM users_table u
WHERE u.dept_id = 5
LIMIT 10;

-- HQL (database-independent)
SELECT u.userName, u.email
FROM User u
WHERE u.department.id = 5
```

```java
// HQL in Hibernate code
Query<User> query = session.createQuery("FROM User u WHERE u.department.name = :deptName", User.class);
query.setParameter("deptName", "Engineering");
List<User> users = query.getResultList();
```

**Key takeaway:** HQL abstracts away the physical database schema, letting developers think in terms of their **Java object model** while Hibernate handles the translation to the appropriate SQL dialect.