# Interview question on SQL

### Difference between DELETE and TRUNCATE and DROP
- 1. Delete - To delete 1 or multiple rows at a time. Data deleted can be roll back(undo) . DML Command
- 2. Truncate - All the data is deleted  but the structure is there. Data cant be roll back. DDL command.
- 3. DROP - All the data as well as the structure is deleted. Data CANT be roll back. DDL command.

In SQL, "DELETE," "TRUNCATE," and "DROP" are three distinct commands used to manage data and database objects, but they have different purposes and implications:

1. **DELETE:**
   - **Purpose:** The DELETE statement is used to remove specific rows or records from a table based on a specified condition.
   - **Usage:** `DELETE FROM table_name WHERE condition;`
   - **Effect:** DELETE is a DML (Data Manipulation Language) statement that removes specific rows that meet the condition, leaving the table structure intact.
   - **Transaction Log:** DELETE generates individual entries in the transaction log for each row deleted. It's suitable for removing specific data while keeping the table structure.

2. **TRUNCATE:**
   - **Purpose:** The TRUNCATE statement is used to remove all the rows from a table quickly. It is essentially a way to remove all data from a table without deleting the table itself.
   - **Usage:** `TRUNCATE TABLE table_name;`
   - **Effect:** TRUNCATE is a DDL (Data Definition Language) statement that deallocates the data pages used by the table, effectively removing all rows in the table.
   - **Transaction Log:** TRUNCATE generates minimal transaction log entries and is generally faster than DELETE for removing all data. However, it cannot be used with a WHERE clause and does not log individual row deletions.

3. **DROP:**
   - **Purpose:** The DROP statement is used to delete database objects entirely, including tables, indexes, views, or even the entire database.
   - **Usage:** `DROP TABLE table_name;` or `DROP DATABASE database_name;` (for database deletion)
   - **Effect:** DROP is a DDL statement that permanently removes the specified object from the database. Once an object is dropped, it cannot be recovered, and all associated data and structures are lost.
   - **Transaction Log:** DROP operations do not generate transaction log entries for individual rows but affect the database schema and structure.

In summary:

- **DELETE:** Used for removing specific rows while keeping the table structure. Generates transaction log entries for each deleted row.
- **TRUNCATE:** Used for removing all rows in a table while deallocating data pages. Faster than DELETE for bulk removal and generates minimal transaction log entries.
- **DROP:** Used for permanently deleting database objects, including tables and databases. Does not log individual data deletions but impacts the database schema.

The choice of which operation to use depends on the specific requirements and goals of your data management tasks.


## Difference between WHERE and HAVING
- Where apply the command on the single record and check the condition.
- Having apply the command on a group of records.

### Group BY and Order BY
- Group by is used to group similar data and show in o/p.
- Oder by is used to make an order asc/dsc for the  data.

### Unions and Joins
UNION and JOIN are two distinct operations in SQL, used for different purposes:

- Union - column wise adding of data
- Join - row wise data add

1. **UNION:**
   - **Purpose:** The UNION operator is used to combine the result sets of two or more SELECT queries into a single result set. It combines rows from different tables or queries into a single result set, removing duplicates by default.
   - **Usage:** `SELECT column1, column2 FROM table1 UNION SELECT column1, column2 FROM table2;`
   - **Effect:** UNION is used to stack rows vertically, combining the results of multiple SELECT statements into one result set with the same structure.
   - **Duplicates:** By default, UNION removes duplicate rows from the combined result set unless you use UNION ALL, which includes duplicates.

   Example:
   ```sql
   SELECT employee_name FROM employees_in_department_1
   UNION
   SELECT employee_name FROM employees_in_department_2;
   ```

2. **JOIN:**
   - **Purpose:** JOIN operations are used to retrieve data from multiple tables based on a related column between them. It combines rows from two or more tables to create a new result set, allowing you to establish relationships between tables.
   - **Usage:** `SELECT column1, column2 FROM table1 INNER JOIN table2 ON table1.columnX = table2.columnY;`
   - **Effect:** JOIN combines rows horizontally by matching values in specified columns, creating a result set that includes columns from multiple tables.
   - **Types:** Common types of joins include INNER JOIN (returns only matching rows), LEFT JOIN (returns all rows from the left table and matching rows from the right table), RIGHT JOIN (returns all rows from the right table and matching rows from the left table), and FULL JOIN (returns all rows when there is a match in either table).

   Example:
   ```sql
   SELECT orders.order_id, customers.customer_name
   FROM orders
   INNER JOIN customers ON orders.customer_id = customers.customer_id;
   ```

In summary:

- **UNION:** Combines rows from multiple SELECT queries into a single result set, stacking them vertically, and optionally removing duplicates.
- **JOIN:** Retrieves data from multiple tables based on related columns, combining rows horizontally, and establishing relationships between tables.

UNION and JOIN serve different purposes: UNION combines data from different sources into a single result set, while JOIN retrieves data from multiple tables based on relationships between them.

## VIEW
In SQL, a view is a virtual table that represents the result of a SELECT query. Unlike physical tables, views do not store data themselves; instead, they are defined by a query that retrieves data from one or more underlying tables. Views are used to simplify data access, enhance security, and provide a convenient way to work with complex or frequently used SQL queries. Here are some key points about SQL views:

1. **Definition:** A view is defined using a SELECT statement that specifies which columns and rows from one or more tables should be included in the view.

2. **Structure:** Views have a structure that resembles a table, with named columns and rows of data. The column names and data types are determined by the SELECT statement used to create the view.

3. **Data Integrity:** Views can enforce data security and data integrity by restricting access to specific rows or columns in the underlying tables. This allows you to define fine-grained access control.

4. **Abstraction:** Views provide a level of abstraction, allowing users and applications to interact with data without needing to understand the underlying table structure or complex SQL queries.

5. **Convenience:** Views are often used to simplify complex joins or aggregations. They can also be used to create custom "virtual" tables tailored to specific reporting or analysis needs.

6. **Modifiability:** In some cases, you can update data through a view (if certain conditions are met), making it appear as if you're modifying the underlying tables directly.

7. **No Data Storage:** As mentioned earlier, views do not store data themselves. Instead, they retrieve data dynamically from the underlying tables whenever the view is queried.


Creating a view is straightforward. Here's an example of creating a simple view:

```sql
CREATE VIEW EmployeeView AS
SELECT employee_id, first_name, last_name, department
FROM Employees
WHERE department = 'Sales';
```

In this example, `EmployeeView` is a view that retrieves employee data from the `Employees` table but only includes employees from the 'Sales' department.

After creating a view, you can query it like a regular table:

```sql
SELECT * FROM EmployeeView;
```

Views are a powerful feature in SQL databases because they enable you to manage and present data in a way that suits your specific needs, while also providing a level of abstraction and data security.

  
