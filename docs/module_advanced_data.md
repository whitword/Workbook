# Advanced Data module

## General SQL

### What are relational databases? Explain the theory behind them!
Relational databases are a type of database management system (DBMS) based on the relational model. The theory behind relational databases was developed by E.F. Codd in the 1970s. According to this theory, data is organized into tables or relations, consisting of rows (tuples) and columns (attributes). The key principles of relational databases include the concept of primary keys to uniquely identify rows, foreign keys to establish relationships between tables, and the use of SQL (Structured Query Language) for querying and manipulating data. The relational model provides a logical and structured approach to storing and retrieving data, ensuring data integrity and enabling powerful data manipulation capabilities.
### Why SQL is important these days?
SQL (Structured Query Language) is important these days for several reasons. Firstly, SQL is the standard language for relational databases, which are widely used to store and manage structured data in various applications and industries. SQL provides a powerful and efficient way to retrieve, manipulate, and analyze data, enabling businesses to make informed decisions based on data insights. Additionally, SQL's declarative nature allows users to focus on the what rather than the how of data operations, making it accessible to both technical and non-technical users. With the rise of data-driven decision making and the increasing volume of data, SQL remains a vital skill for working with relational databases and harnessing the power of data.
### All the new GUI tools enable me to click a button to write SQL. Why should I spend time learning to write SQL manually?
While GUI tools provide convenience and ease of use for executing SQL queries, learning to write SQL manually offers several advantages. Firstly, manual SQL writing allows for greater control and flexibility in crafting complex queries and performing advanced data manipulations. It enables understanding and optimizing query performance, as well as troubleshooting and debugging issues. Additionally, manual SQL proficiency allows for working with databases directly, without relying solely on specific GUI tools. It also enhances the ability to collaborate with other developers, as SQL remains a widely used and understood language in the database realm. Overall, investing time in learning manual SQL empowers users with a versatile and valuable skill set for working with relational databases.
### If SQL is standardized, should you be able to program with SQL on any databases?
While SQL is a standardized language, the implementation and specific features of SQL can vary across different database management systems (DBMS). Although the core syntax and basic functionalities remain consistent, there may be variations and extensions in SQL dialects and vendor-specific implementations. This means that while you can write portable SQL code that works across multiple databases, certain advanced or specialized features may not be universally supported. It is essential to be familiar with the specific SQL capabilities and syntax of the database you are working with to ensure compatibility and optimal usage of its features.
### What makes SQL a nonprocedural language?
SQL is considered a nonprocedural or declarative language because it focuses on describing what data is needed, rather than specifying how to retrieve it. In SQL, you define the desired result set or data manipulation operations, and the database management system determines the most efficient way to execute the query. The developer does not need to explicitly define the steps or sequence of operations to retrieve the data. This declarative approach allows for a more abstract and concise representation of the data requirements, promoting ease of use and enabling the database system to optimize query execution based on its internal algorithms and structures.
### What can you do with SQL?
SQL (Structured Query Language) allows you to perform various operations on relational databases. With SQL, you can create and modify database schemas, define tables and relationships, insert, update, and delete data, retrieve data using complex queries, filter and sort data, aggregate and summarize data, and perform calculations. SQL also supports joining multiple tables, grouping data, creating views, and implementing constraints to ensure data integrity. Additionally, SQL provides capabilities for indexing, transaction management, and user access control. Overall, SQL empowers you to manage and manipulate data effectively, extract meaningful insights, and interact with relational databases efficiently.

---

## DQL

### Do the following statements return the same or different output? Why?

```sql
SELECT * FROM CHECKS;
select * from checks;
```

The two SQL statements `SELECT * FROM CHECKS;` and `select * from checks;` are likely to return the same output, assuming the database has a table named "CHECKS" and the table exists with the same structure and data. 

SQL is not case-sensitive for most database systems, so the uppercase and lowercase variations of the same keywords and identifiers are treated as the same. However, the actual behavior may depend on the database system or specific configuration settings. It is generally a good practice to use consistent casing for readability and to avoid potential confusion or errors.
### The following queries do not work when entered into the command line psql console. Why not?

```sql
Select *
Select * from checks
Select amount name payee FROM checks;
```
The queries you provided are not working because they contain syntax errors. Here are the corrected versions of each query:

1. ``` Select * ```: This query is incomplete. In SQL, you need to specify the table from which you want to select data. For example, if you have a table called "employees," the correct query would be:
```sql 
SELECT * FROM employees;
```

2. ```Select * from checks``` : This query is correct, assuming you have a table named "checks" in your database. However, when executing the query in the psql console, you need to terminate the statement with a semicolon (;) to indicate the end of the command. Here's the corrected version:
```sql
SELECT * FROM checks;
```

3. ```Select amount name payee FROM checks``` : This query has a syntax error. In the SELECT clause, you need to separate column names with commas. Additionally, you should use the keyword "AS" to provide aliases for the selected columns. Here's the corrected version:
```sql
SELECT amount, name, payee FROM checks;
```

### What shorthand could you use instead of `WHERE a >= 10 AND a <=30`?
Instead of `WHERE a >= 10 AND a <= 30`, you can use the shorthand `WHERE a BETWEEN 10 AND 30` to achieve the same result. The `BETWEEN` operator simplifies the condition by specifying a range of values for the column "a." It includes both the lower and upper bounds, making the query more concise and readable. The `BETWEEN` operator is inclusive, meaning that it considers values equal to the lower and upper bounds as part of the result set.
### Which function capitalizes the first letter of a character string and makes the rest lowercase?
The function that capitalizes the first letter of a character string and converts the rest of the characters to lowercase is typically called `INITCAP()` or `Capitalize()`. This function is commonly available in many relational database management systems, such as Oracle, MySQL, and PostgreSQL. It is useful for standardizing the capitalization of strings, such as names or titles, and providing consistent formatting. Using this function ensures that the first letter of the string is uppercase, while the remaining characters are lowercase.
### Will this query work? Why?

```sql
SELECT COUNT(LASTNAME) FROM CHARACTERS;
```
The query `SELECT COUNT(LASTNAME) FROM CHARACTERS;` may or may not work, depending on the structure of the "CHARACTERS" table. 

If the "LASTNAME" column exists in the "CHARACTERS" table, the query should work and return the count of non-null values in the "LASTNAME" column. However, if the "LASTNAME" column does not exist, the query will result in an error. It is crucial to ensure that the column names and table names are accurate and exist in the database schema to execute a successful query.
### Assuming that they are separate columns, which function(s) would splice together FIRSTNAME and LASTNAME?
To concatenate the values of the "FIRSTNAME" and "LASTNAME" columns together, you can use the concatenation operator `||` or the `CONCAT()` function, depending on the database system you are using.

Using the concatenation operator:

```sql
SELECT FIRSTNAME || ' ' || LASTNAME AS FULLNAME FROM CHARACTERS;
```

Using the `CONCAT()` function:

```sql
SELECT CONCAT(FIRSTNAME, ' ', LASTNAME) AS FULLNAME FROM CHARACTERS;
```

Both approaches will concatenate the values of "FIRSTNAME" and "LASTNAME" with a space in between to create a full name. The resulting column alias "FULLNAME" will contain the concatenated values.
### Why are so few functions defined in the ANSI standard and so many defined by the individual implementations?
The ANSI SQL standard defines a core set of functions that are commonly supported across different database management systems. However, individual implementations of SQL databases often provide additional functions and extensions specific to their system.

The reason for this is that different databases have unique features, optimizations, and requirements that go beyond the standard. Database vendors aim to differentiate their products and cater to specific needs of their users. As a result, they introduce additional functions and capabilities that may be tailored for their platform or designed to address common use cases.

Furthermore, the SQL standard evolves over time, and new features and functions are added in subsequent versions. The standardization process takes time, and the adoption of new features varies across different database systems.

Therefore, while the ANSI standard provides a baseline of common functionality, the rich variety of functions offered by individual implementations reflects the diversity and innovation in the database market.
### What is the function of the GROUP BY clause?
The GROUP BY clause in SQL is used to group rows based on one or more columns and perform aggregate calculations on each group. It allows you to create subsets of data based on common values in a column and then apply aggregate functions such as COUNT, SUM, AVG, MAX, or MIN to calculate summary values for each group. The GROUP BY clause is essential for generating summarized reports and performing analysis by grouping and aggregating data based on specific criteria. It helps to organize and summarize data in a meaningful way for analysis and reporting purposes.
### When using the HAVING clause, do you always have to use a GROUP BY also?
No, it is not necessary to use a GROUP BY clause when using the HAVING clause in SQL. The HAVING clause is used to filter the results of a GROUP BY query based on a specified condition that involves aggregate functions. While the GROUP BY clause is typically used in conjunction with the HAVING clause to define the groups, it is also possible to use the HAVING clause without a GROUP BY clause. In such cases, the HAVING clause operates on the entire result set, allowing you to filter the aggregated data based on specific conditions.
### Can you use ORDER BY on a column that is not one of the columns in the SELECT statement?
No, you cannot use the ORDER BY clause on a column that is not included in the SELECT statement. The ORDER BY clause is used to sort the result set based on the specified column(s) in the SELECT statement. The columns used in the ORDER BY clause must be part of the SELECT statement or derived from the selected columns. Attempting to order by a column not present in the SELECT statement would result in an error, as the database wouldn't have access to that column's values for sorting.

---

## Joins

### Explain the different kind of joins! (outer, inner, left, right, natural, etc.)
In SQL, different types of joins allow you to combine data from multiple tables based on specified conditions. 

- Inner join returns only the matching rows from both tables.
- Left join returns all the rows from the left table and the matching rows from the right table.
- Right join returns all the rows from the right table and the matching rows from the left table.
- Full outer join returns all the rows from both tables, including unmatched rows.
- Cross join returns the Cartesian product of both tables.
- Natural join matches rows based on columns with the same name, eliminating duplicate columns.

These join types provide flexibility in combining data and retrieving the desired result set based on the relationship between tables and the data you need.
### How many tables can you join on?
In most database systems, you can join multiple tables together in a single query. The number of tables you can join is typically limited by the database system's capacity and performance constraints, but it can typically handle joining several tables in a single query.
### Would it be fair to say that when tables are joined, they actually become one table?
No, it would not be fair to say that joined tables become one table. When tables are joined, they are combined based on common columns or specified conditions to produce a result set. The result set may include columns from multiple tables, but the original tables remain separate entities in the database. The join operation allows for the retrieval of related data from different tables, but it does not physically merge or alter the original tables' structure or storage. Each table retains its own data and can be accessed and modified independently.
### How many rows would a two-table join produce if one table had 50,000 rows and the other had 100,000?
The number of rows produced by a join between two tables depends on the relationship between the tables and the join conditions. In general, if there is no common column or condition to match rows between the tables, a Cartesian product would be formed, resulting in the multiplication of rows from both tables. In this case, the join would produce 50,000 multiplied by 100,000, which is 5 billion rows. However, if there are matching conditions or columns used in the join, the resulting row count would depend on the number of matches between the tables.
### What type of join appears in the following SELECT statement?

```sql
select e.name, e.employee_id, ep.salary  
from employee_tbl e, employee_pay_tbl ep  
where e.employee_id = ep.employee_id;
```
The SELECT statement in the given example represents an implicit or old-style inner join. The join is performed by specifying the common column "employee_id" in the WHERE clause to match the corresponding rows between the "employee_tbl" and "employee_pay_tbl" tables. The result will include the columns "name" and "employee_id" from the "employee_tbl" table and the column "salary" from the "employee_pay_tbl" table for the matched rows.
### In joining tables are you limited to one-column joins, or can you join on more than one column?
In SQL, you are not limited to joining tables on a single column. You can join tables based on multiple columns by specifying multiple conditions in the JOIN or WHERE clause. This allows for more precise matching and combining of data from different tables. By using multiple columns in the join conditions, you can establish more complex relationships between the tables, such as joining based on a combination of primary and foreign keys or other related attributes. This flexibility enables you to join tables on multiple criteria to retrieve the desired result set.

---

## DML

### Does SQL have a statement for file import/export operations?
SQL itself does not have a specific statement for file import/export operations. However, many database management systems provide additional tools or extensions that allow importing and exporting data from files. For example, SQL Server has the BULK INSERT and BCP utilities, PostgreSQL has the COPY command, and MySQL has the LOAD DATA INFILE statement. These tools or extensions enable you to import data from files into database tables or export data from tables to files in various formats, such as CSV, JSON, or XML. The specific method and syntax may vary depending on the database system you are using.
### Can you copy data from a table into itself using the INSERT command? You would like to make duplicate copies of all the existing records and change the value of one field.
No, you cannot directly copy data from a table into itself using the INSERT command in SQL. When you attempt to insert into the same table from which you are selecting, it creates a conflict and may result in an error. However, you can achieve the desired result by using a combination of the INSERT INTO and SELECT statements, where you select the data from the table and insert it into a new or temporary table. Then, you can update the desired field in the new table and insert the modified records back into the original table.
### What would happen if you issued the following statement?

```sql
DELETE * FROM COLLECTION;
```
This statement contains an error because the asterisk (*) is not valid syntax in the DELETE statement. The correct syntax for the DELETE statement in SQL is:

```sql
DELETE FROM COLLECTION;
```
Without the asterisk, the statement would delete all records from the specified "COLLECTION" table in the database, similar to the previous response. However, including the asterisk would result in a syntax error, and the statement would fail to execute.
### Can you remove columns with the ALTER TABLE statement?
Yes, you can remove columns from a table using the ALTER TABLE statement in SQL. The specific syntax for removing columns may vary slightly depending on the database system you are using, but the general structure is as follows:

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

By executing this statement, the specified column will be removed from the table. It is important to note that removing a column will permanently delete the data stored in that column. Therefore, exercise caution when using the ALTER TABLE statement to remove columns, ensuring that you have appropriate backups and consider the impact on dependent objects or applications.
### Is the DROP TABLE command functionally equivalent to the DELETE FROM <table_name> command?
No, the DROP TABLE command and the DELETE FROM <table_name> command are not functionally equivalent. 

The DROP TABLE command is used to completely remove a table from the database. It deletes the entire table structure along with all the data stored in it. Once a table is dropped, it no longer exists in the database and cannot be accessed or referenced.

On the other hand, the DELETE FROM <table_name> command is used to remove specific rows or records from a table while keeping the table structure intact. It allows you to selectively delete data based on specific conditions or criteria.

In summary, DROP TABLE removes the entire table, while DELETE FROM removes specific rows within a table.
### What is the difference between the functionality of the DELETE FROM <table_name> and the TRUNCATE TABLE command?
The DELETE FROM <table_name> command and the TRUNCATE TABLE command have similar goals of removing data from a table, but they differ in functionality and behavior:

1. DELETE FROM <table_name>:
   - Removes specific rows from the table based on specified conditions using the WHERE clause.
   - Provides more flexibility as you can selectively delete specific rows based on criteria.
   - The operation is logged and can be rolled back using the transaction mechanism.
   - Deletes rows one by one, which can be resource-intensive for large tables.

2. TRUNCATE TABLE:
   - Removes all rows from the table, effectively resetting it to an empty state.
   - Does not require specifying conditions or using the WHERE clause.
   - Performs the operation as a whole, not row by row, which makes it faster for large tables.
   - The operation is not logged, meaning it cannot be rolled back using the transaction mechanism.
   - Resets auto-increment values and resets storage space, resulting in better performance.

In summary, DELETE FROM allows selective row deletion, while TRUNCATE TABLE quickly removes all rows from a table without logging each deletion, providing a faster and more efficient way to empty a table.
### When a table is created, who is the owner?
When a table is created in a database, the owner of the table is typically the user or role who executed the CREATE TABLE statement. The owner is the entity that has certain privileges and control over the table. The owner can be thought of as the entity responsible for managing and administering the table, including performing operations such as altering the table structure, inserting, updating, or deleting data, and granting permissions to other users or roles.

The concept of ownership in a database system helps in organizing and managing access rights, permissions, and responsibilities for different database objects. The owner has certain privileges and control over the table, but those privileges can be granted or revoked by database administrators or users with appropriate permissions.
### If data in a character column has varying lengths, what is the best choice for the data type?
If the data in a character column has varying lengths, the best choice for the data type would typically be a variable-length character data type, such as VARCHAR or NVARCHAR (for Unicode characters). 

The VARCHAR data type allows you to store character strings with varying lengths, up to a maximum specified length. It optimizes storage by using only the necessary space for each value, reducing storage overhead.

When choosing the appropriate length for the VARCHAR data type, it's essential to consider the maximum expected length of the values to avoid truncation. By setting an appropriate maximum length, you can ensure efficient storage utilization while accommodating varying lengths of data in the column.

It's worth noting that different database systems might have variations in the specific data types and their naming conventions, but the general concept of using a variable-length character data type for columns with varying lengths applies across most databases.