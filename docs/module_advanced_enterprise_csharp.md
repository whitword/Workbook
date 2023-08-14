# Enterprise module (C# branch)

## ASP.NET Core

### What Is the difference between .NET Core and .NET Standard? How do them relate to the "classic" .NET Framework?
.NET Core and .NET Standard are both frameworks within the larger .NET ecosystem, and they serve different purposes. Here's a breakdown of their differences and their relationship to the "classic" .NET Framework:

* .NET Framework: The "classic" .NET Framework is a mature and widely used framework that has been around for many years. It is primarily designed for building Windows desktop applications and provides a comprehensive set of libraries and APIs for various development needs. It is tied to the Windows operating system and does not run on other platforms.

* .NET Core: .NET Core is an open-source, cross-platform framework that was introduced by Microsoft to address the limitations of the .NET Framework. It is designed to build applications that can run on different platforms, including Windows, macOS, and Linux. .NET Core offers a streamlined and modular approach, allowing developers to use only the necessary components for their applications. It is optimized for modern cloud-based and containerized scenarios.

* .NET Standard: .NET Standard is a specification that defines a set of APIs that all .NET platforms should implement. It acts as a common ground between different flavors of .NET, including .NET Core, Xamarin, and the "classic" .NET Framework. The goal of .NET Standard is to provide a consistent set of APIs that developers can rely on when building cross-platform applications. By targeting the .NET Standard, developers can ensure that their libraries and code can be used across multiple .NET implementations.

In summary, .NET Core is a specific implementation of the .NET platform that is cross-platform and optimized for modern scenarios. .NET Standard is a specification that defines a common set of APIs across different .NET implementations, including .NET Core. The "classic" .NET Framework is a Windows-specific framework that has a larger set of APIs but is not cross-platform.

### What is ASP.NET MVC?
ASP.NET MVC (Model-View-Controller) is a web development framework within the larger ASP.NET ecosystem. It follows the MVC architectural pattern, which separates an application into three main components: 

* Model
* View
* Controller

ASP.NET MVC promotes the separation of concerns and provides a structured approach to building web applications. It enables developers to write clean, maintainable, and testable code. The framework includes features like routing, which maps URLs to controller actions, and model binding, which automatically binds user input to model properties.

ASP.NET MVC has been widely adopted for building web applications, and it integrates seamlessly with other ASP.NET features and technologies. However, it's worth noting that with the introduction of .NET Core, Microsoft has also released a new web framework called ASP.NET Core MVC, which is the evolution of ASP.NET MVC for cross-platform development.

### Can you explain Model, Controller and View in MVC?
* Model: The model represents the application's data and business logic. It encapsulates the data and provides methods to manipulate and access it. In ASP.NET MVC, models typically represent the entities and data structures used in the application.

* View: The view is responsible for presenting the data to the user. It defines the user interface and displays the information obtained from the model. Views in ASP.NET MVC are typically written using HTML, CSS, and Razor syntax (a view engine provided by ASP.NET).

* Controller: The controller handles user input, processes requests, and interacts with both the model and the view. It receives input from the user, invokes appropriate actions on the model, and determines which view should be rendered. Controllers in ASP.NET MVC are responsible for coordinating the flow of data between the model and the view.

### Explain the request lifecycle of ASP.NET Core.
The request lifecycle of ASP.NET Core can be summarized in the following steps:

* Routing: When a request is received, ASP.NET Core's routing system matches the requested URL to a specific endpoint defined in the application's routing configuration. This determines which controller and action method will handle the request.

* Model Binding: Once the routing determines the appropriate action method, ASP.NET Core automatically maps the incoming request data (such as query strings, form values, and route parameters) to the parameters of the action method, using model binding. This simplifies the process of extracting data from the request.

* Authorization: After model binding, the framework checks if the user has the necessary permissions to access the requested resource. It performs authorization checks based on the configured authorization policies and attributes applied to the action methods or controllers.

* Action Execution: If the user is authorized, the action method associated with the request is invoked. This method contains the business logic for processing the request, such as fetching data from a database, performing calculations, or executing other operations.

* Result Execution: Once the action method completes its execution, it typically returns a result object representing the response to be sent back to the client. This result can be a view, a JSON object, a file, or any other type of response. ASP.NET Core then executes the result, which may involve rendering a view, serializing an object, or sending a file as the response.

* Middleware Execution: Throughout the request lifecycle, ASP.NET Core allows the registration of middleware components that can intercept and process requests and responses at different stages. Middleware can perform tasks such as logging, authentication, caching, compression, and more. The middleware pipeline is processed in a specific order, and each middleware component can modify the request or response.

* Response: Once the result has been executed and any middleware processing is completed, the generated response is sent back to the client, which could be a web browser, a mobile app, or any other type of client.

This summary provides an overview of the key steps involved in the request lifecycle of ASP.NET Core. It demonstrates how the framework handles routing, model binding, authorization, action execution, result execution, and middleware processing to generate and deliver the appropriate response for a given request.

### What is Razor View Engine?
The Razor View Engine is a markup syntax and templating engine used in ASP.NET Core for generating dynamic HTML views. It combines HTML markup with server-side code to create dynamic content. Razor views allow developers to seamlessly embed C# or VB.NET code within HTML, making it easier to generate dynamic content and interact with the underlying data models. Razor provides a clean and intuitive syntax that promotes code readability and maintainability, making it a popular choice for building web applications in ASP.NET Core.

### What you mean by Routing in ASP.NET Core?
Routing in ASP.NET Core refers to the process of mapping incoming URLs to specific actions or endpoints within an application. It determines how requests are handled and which code will be executed to generate the appropriate response.

The routing system in ASP.NET Core uses a set of rules and patterns to match incoming URLs with registered routes. These routes are defined in the application's route configuration, typically done in the Startup class during application startup.

The routing configuration specifies the URL patterns and the corresponding controllers and actions that should handle requests matching those patterns. For example, a route might specify that requests with a URL like "/products" should be handled by the ProductsController and its Index action.

The routing system analyzes the incoming URL and attempts to find a matching route based on the defined patterns. If a match is found, the associated controller and action method are invoked to process the request. The routing system also allows for the extraction of parameters from the URL, which can be passed as arguments to the action methods.

### What is Layout in ASP.NET MVC?
In ASP.NET MVC, a layout is a shared template or master page that defines the overall structure and common elements of a web page. It allows to define a consistent layout for multiple pages in your application.
The layout typically contains HTML markup that remains constant across multiple views, such as the header, footer, navigation menu, and other common elements. By using a layout, you can centralize the definition of these elements and avoid duplicating code in every individual view.
In ASP.NET MVC, you define a layout using a special view file with the extension .cshtml. Within the layout, you can use placeholders called "sections" to specify where the content from individual views will be inserted. Views that use the layout can provide their content to these sections.
When a view is rendered, ASP.NET MVC combines the content of the view with the layout to create the final HTML output. The view's content replaces the designated sections in the layout, and the merged result is sent to the client's browser.
Layouts provide a way to maintain a consistent look and feel across multiple pages in an MVC application, allowing to manage shared UI elements efficiently. They promote code reusability, improve maintainability, and make it easier to update the overall design of the application in a centralized manner.

### What are the three possible lifecycles for an object created by the ASP.NET Dependency Injection module? 
The ASP.NET Dependency Injection (DI) module provides three possible lifecycles for objects created through dependency injection:

* Transient: In the transient lifecycle, a new instance of the object is created every time it is requested from the DI container. Each request receives a separate instance, and the object is not shared across different parts of the application. Transient objects are typically used when you want to ensure that each request or usage receives a fresh instance of the object.

* Scoped: In the scoped lifecycle, a single instance of the object is created and shared within the scope of an HTTP request. When multiple objects within the same HTTP request request the same type of dependency, they receive the same instance. Once the request is completed, the scoped objects are disposed of. Scoped objects are commonly used for maintaining state or data specific to a particular HTTP request.

* Singleton: In the singleton lifecycle, a single instance of the object is created and shared across the entire application. The same instance is returned for every request or usage of the dependency. Singleton objects are created once and live throughout the lifetime of the application. They are often used for sharing resources, services, or data that need to be available globally.

These three lifecycles provided by the ASP.NET Dependency Injection module allow developers to control the creation and sharing of objects within an application, ensuring the appropriate level of scope and state management based on the specific needs of the dependencies.

### What is wwwroot folder in ASP.NET Core?
The wwwroot folder in ASP.NET Core is a special folder used to store static files that are intended to be served directly to clients (such as web browsers) without any processing from the server-side code.

The name "wwwroot" is derived from the traditional "www" prefix used in URLs to denote the World Wide Web. The folder is located at the root level of an ASP.NET Core project, alongside other folders like "Controllers" and "Views".

Static files, such as HTML, CSS, JavaScript, images, and other client-side assets, are placed inside the wwwroot folder. When a client requests a file from the server, the ASP.NET Core runtime directly serves the file from the wwwroot folder without any server-side processing.

For example, if a file named styles.css is placed in the wwwroot/css subdirectory, it can be accessed by the client using the URL /css/styles.css.

The wwwroot folder provides a convenient and standardized location to organize and serve static content. It ensures that the files within this folder are readily accessible to clients and can be efficiently delivered by web servers or content delivery networks (CDNs).

It's important to note that the wwwroot folder is not intended for server-side code files or views. Server-side code files should be placed in appropriate folders like "Controllers" or "Views", respectively, while the wwwroot folder is specifically meant for static files to be served directly to clients.

### What’s the usage of [InternalsVisibleTo] attribute? What are pros and cons of it?
The [InternalsVisibleTo] attribute is used in .NET to control the visibility of types and members within an assembly to another specific assembly. By applying this attribute, you can grant access to internal types and members to a specific assembly that would otherwise be inaccessible.

The main usage of the [InternalsVisibleTo] attribute is to enable unit testing or to allow selected assemblies to access internal implementation details for specific scenarios. It is particularly useful when you want to test internal classes or expose internal members to a specific trusted assembly without making them publicly accessible.

Pros of using [InternalsVisibleTo]:

Unit Testing: It allows you to expose internal types or members to your unit test project, enabling comprehensive testing of the internal implementation details.

Encapsulation: It helps maintain encapsulation by keeping internal types and members hidden from unintended access while still providing controlled access to trusted assemblies.

Flexibility: It provides a fine-grained control mechanism, allowing you to specify which specific assemblies should have access to internals, instead of making everything public.

Cons of using [InternalsVisibleTo]:

Reduced Encapsulation: It breaks the encapsulation to some extent by exposing internal types and members to external assemblies, potentially allowing them to access and modify internal implementation details.

Increased Complexity: It adds complexity to the project configuration and management, as you need to carefully define and maintain the list of assemblies with access to internals.

Dependency and Coupling: It introduces a dependency between the target assembly and the assembly specified in [InternalsVisibleTo], making it less flexible to change the internal implementation without affecting the dependent assemblies.

When using [InternalsVisibleTo], it's important to consider the trade-offs between increased testability and encapsulation. It should be used judiciously, and the decision to expose internals should be based on the specific requirements and risks of the project.

## Object Relational Mapping, Entity Framework

### What is an ORM? What are benefits, when to use?
Object-Relational Mapping is a technique used in software development to bridge the gap between object-oriented programming languages and relational databases. An ORM tool provides a way to map database tables and queries to object-oriented models and operations, making it easier to work with persistent data.

The benefits of using an ORM include:

* Productivity: ORM tools automate the process of mapping database tables to object models, reducing the amount of manual code you need to write. This can greatly increase developer productivity by eliminating the need to write repetitive and error-prone data access code.

* Abstraction: ORM tools provide an abstraction layer that shields developers from the complexities of database-specific operations and query languages. Developers can work with object-oriented code and use familiar programming paradigms, while the ORM handles the translation between objects and database tables.

* Portability: With an ORM, you can write database-agnostic code that can work with different database systems. The ORM tool handles the database-specific details, allowing your application to be easily switched between different database backends without requiring significant code changes.

* Maintainability: ORM tools provide a consistent and structured approach to database access, making it easier to manage and maintain the codebase. Changes to the database schema can be handled by updating the ORM mappings, reducing the impact on the rest of the application.

* Performance: ORM tools often provide performance optimization features, such as caching, lazy loading, and query optimization. These features help improve the efficiency and speed of database operations.

ORMs are particularly beneficial in applications that involve complex data models, require frequent database interactions, or need to support multiple database platforms. They can be used in a wide range of scenarios, including web applications, desktop applications, and enterprise systems.

However, it's important to consider the trade-offs of using an ORM. While it provides convenience and productivity, there may be cases where low-level control over database operations or fine-tuned query performance is required. It's also crucial to understand the ORM's capabilities, configuration options, and best practices to make the most effective use of the tool and avoid potential pitfalls.

### What is Entity Framework? What are the advantages, limitations?
Entity Framework (EF) is an Object-Relational Mapping (ORM) framework provided by Microsoft for .NET applications. It simplifies the process of working with relational databases by allowing developers to work with database entities as regular .NET objects, abstracting away the complexities of database access.

Advantages of Entity Framework:

* Productivity: EF reduces the amount of manual data access code, enabling faster development and reducing development time.

* Object-Oriented Approach: EF allows developers to work with database entities as objects, leveraging object-oriented programming principles and providing a more intuitive way to interact with data.

* LINQ Integration: EF seamlessly integrates with LINQ (Language Integrated Query), allowing developers to write strongly typed queries against the database using familiar syntax.

* Cross-Database Support: EF supports multiple database providers, enabling developers to switch between different database systems without significant code changes.

* Automatic Mapping: EF automatically maps database tables to object models, eliminating the need for manual mapping code.

Limitations of Entity Framework:

* Performance: EF may introduce performance overhead due to its abstraction layer. In certain scenarios, hand-tuned SQL queries may offer better performance.

* Learning Curve: EF has a learning curve, especially for complex scenarios and performance optimization techniques. Understanding the framework's features and configurations is essential to make efficient use of EF.

* Limited Control: EF abstracts away low-level database operations, which can limit fine-grained control over SQL queries and database optimizations.

* Database-First Challenges: While EF supports database-first development, there can be challenges when dealing with complex databases or when the database schema frequently changes.

Overall, Entity Framework is a powerful ORM framework that provides productivity gains, abstraction, and integration with LINQ. However, it's important to consider the limitations and trade-offs, especially in performance-critical scenarios where low-level control over database operations is required.

### What is lazy loading?
Lazy loading is a technique used in software development, particularly in the context of database access and object-relational mapping (ORM). It defers the loading of data or objects until the point at which they are actually needed.

In the context of database access, lazy loading is often associated with ORM frameworks like Entity Framework. When lazy loading is enabled for a particular entity or navigation property, the related data is not loaded from the database immediately when the parent entity is retrieved. Instead, the related data is loaded on-demand, typically when it is accessed for the first time.

Lazy loading offers several benefits:

*  Reduced Memory Usage: By loading related data only when it is required, lazy loading helps minimize the amount of memory consumed by an application. It avoids unnecessary loading of large datasets and improves memory efficiency.

* Performance Optimization: Lazy loading can improve the performance of data retrieval by deferring the loading of related data until it is actually needed. This allows for faster initial data fetching and reduces the overall number of database queries executed.

* Simplified Development: Lazy loading simplifies the coding process by automatically loading related data when accessed, eliminating the need for explicit queries or joins in many cases. This reduces the amount of manual code that needs to be written and maintained.

However, lazy loading also has some considerations and potential drawbacks:

* Additional Database Queries: Lazy loading can lead to additional database queries being executed as related data is loaded on-demand. If not used judiciously, it can result in excessive database round trips and impact performance.

* Potential Performance Pitfalls: Lazy loading can introduce performance issues if not used carefully. It's important to consider the impact of lazy loading on query execution, database access patterns, and overall performance requirements.

* Proxy Objects: In many ORM frameworks, lazy loading is achieved through the use of proxy objects that are dynamically generated at runtime. These proxy objects can add complexity and may require additional consideration for serialization, equality comparisons, and other aspects of object-oriented programming.

It's essential to understand the implications of lazy loading and carefully evaluate its usage based on specific application requirements, performance considerations, and data access patterns.

### What is the difference between code first and DB first approach?
The code-first and database-first approaches are two different strategies for developing applications with regards to the design and creation of the database schema and the corresponding object model in an ORM framework like Entity Framework.

1. Code-First Approach:
In the code-first approach, the focus is on defining the application's object model (classes, properties, relationships) first. The database schema is then generated automatically based on these classes. Developers write the code for entities and their relationships using annotations or fluent API configurations, and then use tools or migrations to generate the database schema. Code-first allows for a more object-oriented development experience, where the database structure is derived from the code.

2. Database-First Approach:
In the database-first approach, the emphasis is on an existing database schema. Developers start with an existing database or create a database schema separately using database management tools. They then use tools like Entity Framework to generate the corresponding object model based on the schema. This approach involves reverse engineering the database schema to create entity classes and their relationships. Developers can also make modifications to the generated code to add customizations or mappings.

Key Differences:

* In code-first, the database schema is generated based on the code, while in database-first, the code is generated based on an existing database schema.
* Code-first puts more emphasis on the object model and allows for easier control over the database schema through code annotations or configurations.
* Database-first starts with an existing database schema and generates the code to match it, which is useful when working with legacy databases or databases created by other tools.
* Code-first is generally preferred when starting a project from scratch or when the focus is on the application's object model design, while database-first is suitable for scenarios where the database schema already exists or when working with databases managed externally.

Both approaches have their advantages and considerations, and the choice between them depends on factors such as project requirements, team preferences, existing infrastructure, and development workflows.

### What is a migration script?
A migration script is a set of instructions or code that defines changes to a database schema over time. It is commonly used in the context of database migrations, which are the process of applying these changes to an existing database to keep it in sync with the evolving application.

Migration scripts are typically written in a database-specific scripting language or a database migration tool's syntax. They describe the modifications required to the database schema, such as creating or altering tables, adding or removing columns, defining indexes or constraints, and other schema-related operations.

Some key aspects of migration scripts:

* Versioning: Migration scripts are usually organized into versions or sequential steps. Each migration script corresponds to a specific version or step in the database schema evolution. By applying these scripts in order, the database can be incrementally updated to reflect the latest schema.

* Up and Down Scripts: Migration scripts typically have two parts: the "up" script and the "down" script. The "up" script applies the changes to the database schema, while the "down" script reverts or rolls back those changes, allowing for easy database rollback or reverting to a previous schema version if needed.

* Idempotent Execution: Migration scripts should be designed to be idempotent, meaning that they can be safely executed multiple times without causing unintended side effects. This allows for safe re-execution of migrations during deployment or rollback scenarios.

* Source Control: Migration scripts are often stored in source control along with the application's codebase. This ensures version control, traceability, and collaboration among developers working on the project.

Migration scripts are commonly used in various frameworks and tools for database schema management, such as Entity Framework Migrations, Liquibase, Flyway, and Django's database migrations. These tools help automate the application of migration scripts and provide mechanisms to track and manage the database schema changes over time.

### What is a navigation property?
A navigation property refers to a property or reference that represents a relationship between entities in an object model. It allows you to navigate or traverse between related entities and access the associated data.

In most ORM frameworks, such as Entity Framework, navigation properties are defined in entity classes and are used to establish relationships between entities. These properties provide a convenient way to access associated entities or collections of entities without explicitly writing complex join queries.

For example, consider two entity classes: Author and Book. The Author class may have a navigation property called Books, which represents the collection of books written by that author. Similarly, the Book class may have a navigation property called Author, representing the author of that book.

With navigation properties, you can easily access related entities and perform operations like eager loading (loading related entities in a single query), lazy loading (loading related entities on-demand), and defining cascade delete behavior (deleting related entities when the parent entity is deleted).

### Name 3 different attributes used in EF Core, what can they do for you?
* The [Key] attribute is used to specify the primary key property in an entity class. It marks a property as the unique identifier for the entity. By using the [Key] attribute, Entity Framework Core can determine which property represents the primary key in the corresponding database table.

* The [Column] attribute is used to specify the database column name for a property in an entity class. By default, Entity Framework Core maps property names to column names, but the [Column] attribute allows you to explicitly define the column name when it differs from the property name.

* The [ForeignKey] attribute is used to specify the foreign key property in a dependent entity class that corresponds to the primary key property in the principal entity class. It establishes a relationship between entities and allows Entity Framework Core to generate the appropriate foreign key constraints in the database.

These attributes help define the mapping between the object model and the database schema in Entity Framework Core. By using these attributes, you can customize the mapping behavior, specify primary keys, define column names, and establish relationships between entities. They provide a way to override the default conventions and control the database schema generation process, ensuring that the database reflects the desired structure and relationships as defined in the entity classes.

## Databases - Advanced

### What are aggregate functions? Could you give a few examples?
Aggregate functions are used to perform calculations on a set of values within a table or a group of rows and return a single result. These functions operate on a column or a group of columns in a database table and produce a summarized value as the output. Aggregate functions are commonly used in SQL queries to perform calculations and generate meaningful insights from the data. Here are some common aggregate functions in database concepts:

1. COUNT: The COUNT function is used to count the number of rows or non-null values in a column. It returns the total count as the output.
2. SUM: The SUM function calculates the sum of values in a column, typically numeric values. It returns the total sum as the output.
3. AVG: The AVG function calculates the average value of a column, typically numeric values. It returns the average as the output.
4. MAX: The MAX function returns the maximum value from a column.
5. MIN: The MIN function returns the minimum value from a column.
6. GROUP BY: The GROUP BY clause is not a specific aggregate function, but it is used in conjunction with aggregate functions to group rows based on specified columns. It allows for the calculation of aggregate functions for each group separately.

Here's an example SQL query that demonstrates the use of aggregate functions:

```sql
SELECT COUNT(*) as TotalCustomers, AVG(Age) as AverageAge, MAX(Salary) as HighestSalary
FROM Customers
WHERE Country = 'USA'
GROUP BY Country;
```

### What does GROUP BY do?
The GROUP BY clause is not a specific aggregate function, but it is used in conjunction with aggregate functions to group rows based on specified columns. It allows for the calculation of aggregate functions for each group separately.
### When would you use HAVING?
The HAVING clause in SQL is used in conjunction with the GROUP BY clause to filter the results of a query based on a condition that applies to the grouped data. It allows you to apply a condition to the result of an aggregate function or to the grouped data itself. The HAVING clause is used when you want to filter the result set based on aggregate calculations.

Here are a few scenarios where you would use the HAVING clause:

* Filtering grouped data: When using the GROUP BY clause to group rows based on a column or set of columns, you can use the HAVING clause to filter the groups based on aggregate conditions. For example, if you have grouped data by category and you want to filter only those categories that have more than a certain number of products, you can use the HAVING clause to specify the condition.

* Filtering based on aggregate calculations: If you have performed aggregate calculations on a column, such as calculating the sum or average, and you want to filter the result based on a condition involving that aggregate calculation, you can use the HAVING clause. For example, if you want to retrieve only those sales regions where the total sales amount is greater than a specific value, you can use the HAVING clause to apply that condition.

* Combining aggregate conditions: The HAVING clause allows you to combine multiple aggregate conditions using logical operators such as AND and OR. This can be useful when you want to apply complex filtering criteria to the grouped data.

Here's an example to illustrate the usage of the HAVING clause:
```sql
SELECT category, SUM(quantity) as total_quantity
FROM products
GROUP BY category
HAVING SUM(quantity) > 100;
```
In this example, the query groups the products by category and calculates the total quantity for each category. The HAVING clause filters the result to include only those categories where the total quantity is greater than 100.

Overall, the HAVING clause is used to filter the result set based on aggregate conditions or grouped data, allowing you to apply additional filtering criteria beyond what the WHERE clause provides.

### What does a LEFT OUTER JOIN do and how does it differ from an INNER JOIN? Give an example for a result table for each JOIN type.
In SQL, the LEFT OUTER JOIN and INNER JOIN are two types of join operations used to combine rows from multiple tables based on a related column or condition. Here's an explanation of each join type and an example result table for both:

1. INNER JOIN:
An INNER JOIN returns only the rows that have matching values in both tables based on the specified join condition. It discards the non-matching rows from both tables.
Example:
Consider two tables: Customers and Orders.

Customers table:

```diff
CustomerID | CustomerName
-----------|-------------
1          | John
2          | Mary
3          | Lisa
```

Orders table:

```yaml
OrderID | CustomerID | OrderDate
--------|------------|-----------
101     | 1          | 2023-05-01
102     | 2          | 2023-05-02
103     | 1          | 2023-05-03
```

INNER JOIN query:

```sql
SELECT Customers.CustomerName, Orders.OrderDate
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

Result table:

```yaml
CustomerName | OrderDate
-------------|-----------
John         | 2023-05-01
John         | 2023-05-03
Mary         | 2023-05-02
```

In this example, the INNER JOIN retrieves only the matching rows between the Customers and Orders tables based on the common CustomerID column.

2. LEFT OUTER JOIN:
A LEFT OUTER JOIN returns all the rows from the left (or first) table and the matching rows from the right (or second) table. If there is no match, NULL values are included for the right table columns.
Example:
Consider two tables: Customers and Orders.

Customers table:

```diff
CustomerID | CustomerName
-----------|-------------
1          | John
2          | Mary
3          | Lisa
```

Orders table:

```yaml
OrderID | CustomerID | OrderDate
--------|------------|-----------
101     | 1          | 2023-05-01
102     | 2          | 2023-05-02
```

LEFT OUTER JOIN query:

```sql
SELECT Customers.CustomerName, Orders.OrderDate
FROM Customers
LEFT OUTER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

Result table:

```yaml
CustomerName | OrderDate
-------------|-----------
John         | 2023-05-01
Mary         | 2023-05-02
Lisa         | NULL
```

In this example, the LEFT OUTER JOIN retrieves all the rows from the Customers table and the matching rows from the Orders table. Since there is no matching row for Lisa in the Orders table, the OrderDate is shown as NULL for her.

To summarize, the main difference between a LEFT OUTER JOIN and an INNER JOIN is that the LEFT OUTER JOIN includes all rows from the left table and only matching rows from the right table, while the INNER JOIN only includes matching rows from both tables.

### Can you insert multiple records with a single INSERT statement?
Yes, it is possible to insert multiple records with a single INSERT statement in SQL. This can be achieved by using the INSERT INTO statement with a comma-separated list of values or by using a SELECT statement to insert data from another table. Here are two common approaches:

1. We can use INSERT-SELECT-UNION query to insert data into multiple rows of the table. The SQL UNION query helps to select all the data that has been enclosed by the SELECT query through the INSERT statement.

Example:
```sql
create table Info(id integer, Cost integer);
INSERT INTO Info (id, Cost)  
SELECT 1, '123'  
UNION ALL   
SELECT 2, '234'  
UNION ALL  
SELECT 3, '456';
```
```sql
select * from Info;
```
Output:

```sql
1	123
2	234
3	456
```

2. Or we can use row construction to insert multiple records. The SQL INSERT query is used in a manner wherein we make use of a single INSERT query to insert multiple records within a single point of execution.

Example:
```sql
create table Info(id integer, Cost integer,city nvarchar(200));
INSERT INTO Info (id,Cost,city)  
VALUES (1,200, 'Pune'), (2, 150,'USA'), (3,345, 'France');  
```

```sql
select * from Info;
```

Output:

```sql
1	200	Pune
2	150	USA
3	345	France
```

### When do you use the DISTINCT keyword?
The DISTINCT keyword in SQL is used to eliminate duplicate rows from the result set of a query. It ensures that only unique values are returned for the specified columns. The DISTINCT keyword is commonly used in scenarios where you want to retrieve unique values or perform calculations based on distinct values. Here are a few cases where you might use the DISTINCT keyword:

1. Retrieving unique values:
If you have a column with duplicate values and you want to retrieve only the distinct values, you can use the DISTINCT keyword in your SELECT statement. This is useful when you want to get a list of unique names, cities, or any other attribute from a table.

Example:

```sql
SELECT DISTINCT city
FROM customers;
```
In this example, the DISTINCT keyword ensures that only unique city values are returned from the "customers" table.

2. Counting distinct values:
When you need to count the number of distinct values in a column, you can use the COUNT function in combination with the DISTINCT keyword. This allows you to calculate the count of unique occurrences rather than counting all occurrences, which would include duplicates.
Example:
```sql
SELECT COUNT(DISTINCT country)
FROM customers;
```
In this example, the COUNT(DISTINCT) statement returns the count of distinct country values in the "customers" table.

3. Filtering based on distinct values:
If you want to filter your query results based on distinct values, you can use the DISTINCT keyword in combination with the WHERE clause. This allows you to apply conditions on unique values rather than considering duplicate values.
Example:
```sql
SELECT DISTINCT product_name
FROM orders
WHERE order_date >= '2023-01-01';
```
In this example, the DISTINCT keyword ensures that only distinct product names are returned for orders placed after January 1, 2023.

Overall, the DISTINCT keyword is used when you want to work with unique values and eliminate duplicates from your query results. It helps you retrieve unique records, calculate distinct counts, or apply filters based on unique values.

### What would you use the CASCADE keyword for?
The CASCADE keyword in SQL is used in the context of foreign key constraints to define the actions to be taken when a referenced record in the parent table is updated or deleted. It allows you to automatically propagate changes from the parent table to the child table(s) that have a foreign key relationship. The CASCADE keyword ensures that the integrity and consistency of data are maintained across related tables. Here are two common scenarios where you might use the CASCADE keyword:

1. Cascading updates:
When a referenced record in the parent table is updated, the CASCADE keyword allows you to specify that the corresponding foreign key values in the child table(s) should be updated automatically. This ensures that the foreign key values remain synchronized with the updated values in the parent table.

Example:

Consider two tables: Customers and Orders. The Orders table has a foreign key constraint referencing the CustomerID column in the Customers table.
```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50)
);
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATE,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID) ON UPDATE CASCADE
);
```
In this example, if the CustomerID of a customer in the Customers table is updated, the CASCADE keyword ensures that the corresponding CustomerID values in the Orders table are automatically updated as well.

2. Cascading deletes:
When a referenced record in the parent table is deleted, the CASCADE keyword allows you to specify that the corresponding child records in the child table(s) should be deleted automatically. This ensures that associated records in the child table(s) are removed when the referenced record is deleted.

Example:

Consider the same Customers and Orders tables as mentioned before. The Orders table has a foreign key constraint referencing the CustomerID column in the Customers table.
```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50)
);
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATE,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID) ON DELETE CASCADE
);
```

In this example, if a customer record in the Customers table is deleted, the CASCADE keyword ensures that all associated orders in the Orders table with the corresponding CustomerID are automatically deleted.

The CASCADE keyword provides a convenient way to maintain referential integrity and handle changes across related tables in a database. It simplifies data management by automating the handling of updates and deletions in child tables based on changes in the parent table.

### What are database transactions?
Database transactions are units of work or operations performed on a database that need to be treated as a single, indivisible operation. A transaction groups multiple database operations into a logical unit, ensuring that either all the operations within the transaction are executed successfully, or none of them are executed at all. The purpose of transactions is to maintain data integrity, consistency, and recoverability in database systems. Here are some key characteristics and concepts related to database transactions:

1. ACID Properties:
Transactions adhere to the ACID properties, which stand for:
   - Atomicity: A transaction is an atomic operation, meaning it is treated as a single indivisible unit. It either completes successfully, or if any part fails, the entire transaction is rolled back, and the database is left unchanged.
   - Consistency: A transaction ensures that the database moves from one consistent state to another. It enforces data integrity rules and constraints.
   - Isolation: Transactions are isolated from each other, meaning that the intermediate state of a transaction is not visible to other concurrent transactions until it is committed.
   - Durability: Once a transaction is committed, its changes are permanently stored in the database and are not lost even in the event of a system failure.

2. Transaction Control Statements:
Transactions are managed using transaction control statements provided by database systems. The main control statements are:
   - BEGIN TRANSACTION: Begins a new transaction.
   - COMMIT: Ends a transaction and makes all the changes made within the transaction permanent.
   - ROLLBACK: Ends a transaction and undoes all the changes made within the transaction, reverting the database to its state before the transaction began.
   - SAVEPOINT: Sets a marker within a transaction, allowing for partial rollback to that specific point.

3. Concurrency Control:
Database systems implement concurrency control mechanisms to handle multiple transactions executing concurrently. Concurrency control ensures that transactions do not interfere with each other, maintaining data consistency and preventing conflicts.

4. Error Handling and Recovery:
In case of system failures or errors, database systems provide mechanisms for transaction recovery. Transaction logs are maintained, allowing the system to restore the database to a consistent state by replaying or undoing the logged transactions.

5. Transaction Isolation Levels:
Database systems offer different isolation levels that define the level of concurrency and isolation among concurrent transactions. Common isolation levels include READ UNCOMMITTED, READ COMMITTED, REPEATABLE READ, and SERIALIZABLE.

Transactions are essential for maintaining data integrity, ensuring consistency, and providing fault tolerance in database systems. They allow multiple operations to be treated as a single logical unit, providing reliability and recoverability in complex data management scenarios.
### What is an inner/nested query?
An inner or nested query, also known as a subquery, is a query that is embedded within another query. It is used to retrieve data from one or more tables based on the results of another query. The result of the inner query is used as input or criteria for the outer query.

An inner query can be used in various parts of a SQL statement, including the SELECT, FROM, WHERE, HAVING, and INSERT clauses. Here are a few common use cases of inner queries:

1. Filtering based on a subquery:
You can use an inner query in the WHERE clause to filter the result set of the outer query based on certain conditions derived from the inner query.

Example:
```sql
SELECT product_name, unit_price
FROM products
WHERE unit_price > (SELECT AVG(unit_price) FROM products);
```

In this example, the inner query calculates the average unit price from the "products" table. The outer query retrieves products with a unit price greater than the calculated average.

2. Subquery in the SELECT clause:
An inner query can be used within the SELECT clause to perform calculations or retrieve additional information for each row of the outer query.

Example:
```sql
SELECT customer_name, (SELECT COUNT(*) FROM orders WHERE customer_id = customers.customer_id) AS order_count
FROM customers;
```

In this example, the inner query counts the number of orders for each customer in the "orders" table. The outer query retrieves the customer name along with the corresponding order count.

3. Subquery in the FROM clause:
You can use an inner query in the FROM clause to create a derived table, also known as an inline view. The inner query acts as a temporary table that can be referenced in the outer query.

Example:
```sql
SELECT *
FROM (SELECT product_name, unit_price FROM products) AS temp_table
WHERE unit_price > 100;
```

In this example, the inner query selects the product name and unit price from the "products" table. The outer query retrieves rows from the derived table where the unit price is greater than 100.

Inner queries provide flexibility and allow you to perform complex queries by breaking them down into smaller, manageable parts. They can be powerful tools to retrieve data based on dynamic conditions, perform calculations, or create temporary tables for further analysis.

### What is a database index?
A database index is a data structure that improves the speed and efficiency of data retrieval operations in a database. It is created on one or more columns of a table to allow for faster searching, sorting, and filtering of data. An index provides a way to quickly locate records based on the values stored in the indexed columns.

The primary purpose of creating an index is to enhance query performance by reducing the amount of data that needs to be scanned or processed. When a query is executed, the database can utilize the index to locate the relevant data more efficiently, resulting in faster query execution times.

Here are some key points about database indexes:

1. Structure and Organization: Indexes are typically implemented as balanced tree structures, such as B-trees or hash tables, that enable efficient lookup and traversal of the indexed data.

2. Indexed Columns: An index can be created on one or multiple columns of a table. Indexing commonly involves columns used in query conditions, JOIN operations, or ORDER BY clauses.

3. Unique and Non-Unique Indexes: Indexes can be defined as unique or non-unique. A unique index enforces uniqueness for the indexed column(s), while a non-unique index allows duplicate values.

4. Index Maintenance: Indexes need to be maintained as the underlying data changes. When records are inserted, updated, or deleted, the index must be updated to reflect these modifications. This maintenance operation incurs overhead and can impact performance.

5. Trade-Offs: While indexes improve query performance, they come with trade-offs. Indexes occupy disk space and require additional processing during data modification operations. Creating too many indexes on a table can lead to increased storage requirements and slower data modification operations.

6. Index Selection: The choice of which columns to index and which indexes to create depends on the specific database schema, the types of queries executed, and the balance between read and write operations.

Database indexes play a crucial role in optimizing query performance and enhancing the overall efficiency of a database system. By properly defining and maintaining indexes, database administrators and developers can significantly improve the speed of data retrieval and ensure the responsiveness of database applications.

### What entity/table relationship types do you know?
There are several common entity/table relationship types that are important to understand when working with databases. These relationships define how tables are connected and interact with each other. Here are the most common types of relationships:

1. One-to-One (1:1) Relationship:
In a one-to-one relationship, each record in one table is associated with exactly one record in another table, and vice versa. This relationship is typically represented by a foreign key in one table that references the primary key in the other table.

Example:
Consider two tables: Employee and EmployeeDetails. Each employee has exactly one corresponding record in the EmployeeDetails table, and each record in the EmployeeDetails table is associated with only one employee.

2. One-to-Many (1:N) Relationship:
In a one-to-many relationship, a record in one table is associated with one or more records in another table. However, each record in the second table is associated with only one record in the first table. This relationship is represented by a foreign key in the "many" side table that references the primary key in the "one" side table.

Example:
Consider two tables: Department and Employee. Each department can have multiple employees, but each employee belongs to only one department.

3. Many-to-Many (N:N) Relationship:
In a many-to-many relationship, multiple records in one table are associated with multiple records in another table. This relationship requires a third table, known as a junction or associative table, to connect the two tables. The junction table typically consists of foreign keys referencing the primary keys of the two related tables.

Example:
Consider two tables: Student and Course. A student can enroll in multiple courses, and each course can have multiple students. To represent this relationship, a junction table, such as Enrollment, is created with foreign keys referencing the Student and Course tables.

4. Self-Referencing Relationship:
A self-referencing relationship occurs when a table is related to itself. This relationship is often used to represent hierarchical or recursive structures.

Example:
Consider an Employee table where each employee has a manager who is also an employee in the same table. In this case, the table has a self-referencing relationship where the manager column references the employee_id column in the same table.

Understanding these common relationship types is essential for designing and working with databases. It helps establish the appropriate connections between tables and enables efficient data retrieval and maintenance.

### What do you know about database normalization?
Database normalization is a process used in relational database design to minimize data redundancy and maintain data integrity. It involves organizing data into separate tables and establishing relationships between them. The goal is to eliminate data anomalies and improve data consistency.

For example, consider a database with a "Customers" table that contains customer information and an "Orders" table that contains order details. Instead of duplicating customer information for each order, normalization suggests creating separate tables for customer details and orders. The "Customers" table would store unique customer information, such as name, address, and contact details. The "Orders" table would store information specific to each order, such as order ID, date, and customer ID. The customer ID serves as a foreign key to establish a relationship between the two tables.

By normalizing the database, redundancy is reduced, as customer information is stored only once in the "Customers" table. This prevents inconsistencies, such as updating customer details in one place and leaving them unchanged in another. Normalization also facilitates efficient querying and data management, as data is organized logically and can be accessed without unnecessary duplication.

Different levels of normalization, such as first normal form (1NF), second normal form (2NF), and third normal form (3NF), guide the process, ensuring that data is properly structured and relationships are well-defined.

### What is SQL injection?
SQL injection is a security vulnerability that occurs when malicious SQL (Structured Query Language) code is inserted into a database query through user input. It occurs when input from an untrusted source, such as a user's input in a web form, is directly concatenated into a SQL statement without proper sanitization or validation. The injected SQL code can alter the intended behavior of the SQL query and potentially gain unauthorized access to the database or manipulate its data.

Here are the key points to understand about SQL injection:

1. Exploitation:
An attacker can exploit SQL injection by submitting malicious input that alters the structure or logic of a SQL query. The attacker can bypass authentication, retrieve sensitive data, modify or delete data, or perform unauthorized actions on the database.

2. Vulnerable Points:
SQL injection vulnerabilities commonly occur when user input is concatenated directly into SQL statements without proper validation or sanitization. This can happen in dynamic SQL queries, web forms, search fields, login forms, or any input fields that directly interact with the database.

3. Example:
Consider a simple login form where a username and password are collected and used in a SQL query to validate the user:

```sql
SELECT * FROM users WHERE username = '<user_input>' AND password = '<user_input>';
```

If the user enters `' OR '1'='1` as the username and leaves the password field empty, the resulting SQL query would become:

```sql
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
```

The condition `'1'='1'` always evaluates to true, effectively bypassing the authentication mechanism.

4. Impact:
SQL injection attacks can have severe consequences, including unauthorized data disclosure, data manipulation, website defacement, privilege escalation, or even complete compromise of the database server. It can lead to significant financial losses, damage to reputation, legal issues, and compromised customer data.

5. Prevention:
To prevent SQL injection, it is crucial to use prepared statements or parameterized queries with placeholders instead of concatenating user input directly into SQL statements. This ensures that user input is properly escaped or bound to query parameters, preventing the injected SQL code from executing as intended. Additionally, input validation and sanitization should be performed to ensure that user input adheres to expected patterns and formats.

SQL injection is a prevalent and dangerous vulnerability that can be prevented by following secure coding practices, using parameterized queries, and implementing proper input validation and sanitization techniques. It is essential for developers and database administrators to be aware of this vulnerability and take necessary measures to mitigate the risk.