- **What’s the difference between DELETE, TRUNCATE, and DROP?**
    
    **DELETE removes specific rows from a table, supports WHERE clauses, and can be rolled back, while TRUNCATE quickly removes all rows from a table, preserving its structure and indexes but typically cannot be rolled back**
    
    **DROP is a**
    
    [**Data Definition Language (DDL) command**](https://www.google.com/search?sca_esv=913ae395eea29b77&sxsrf=AE3TifPEjsojrAImw-WSwAArJpoq7XOIMA%3A1759330085672&q=Data+Definition+Language+%28DDL%29+command&sa=X&ved=2ahUKEwjJiLKmn4OQAxWGUGwGHXihNzAQxccNegQIIxAB&mstk=AUtExfCnU326KMfr1CMZuP-b6RYUsntniSlRB2P3hMxrBJx2GmhkZ9fLks8QTk3W0U-ZL4S5tDxmmpNMxCKtrMSyvTT1M3xd8yeW2HnIlYBjte20sOvi8uXCtfzsTgm0__TBZSKILyOT-9v8Sj4-stBmGFkZIGtymLbk7TF1RUvNqF8Yl7E-dj5aCUnkAptXzx0yy6BYmW7R6jk_Ft-zhHGTki7ntt6olv64KvReD-U1wx3qavGYLBUEE7oLrpJuqeRHO-V-ZINeUO-yv7yK1WR7ourM&csui=3)
    
    **that completely removes the entire table, including its structure, data, and all associated objects.**
    
    | **Parameter** | **DELETE** | **DROP** | **TRUNCATE** |
    | --- | --- | --- | --- |
    | **Type** | DML | DDL | DDL |
    | **Purpose** | Deletes specific rows based on condition | Deletes the entire table or database | Deletes all rows but retains table structure |
    | **Syntax** | `DELETE FROM table_name WHERE condition;` | `DROP TABLE table_name;` | `TRUNCATE TABLE table_name;` |
    | **Rollback Support** | Can be Rollback | Cannot be Rollback | Cannot be Rollback |
    | **Data Removal** | Removes selected rows | Removes table and data completely | Removes all rows |
    | **Efficiency** | Slower, as each row is processed individually | Instant removal, affecting schema | Faster than DELETE but slower than DROP |
    | **Triggers** | Fires triggers | Does not fire triggers | Does not fire triggers |
    
    **DELETE**
    
    **Purpose:** Removes one or more specific rows from a table.
    
    - **Purpose:** Removes one or more specific rows from a table.
    
    **Data Removal:** You can specify conditions using a `WHERE` clause to delete only certain rows.
    
    - **Data Removal:** You can specify conditions using a `WHERE` clause to delete only certain rows.
    
    **Rollback:** Because it's a DML (Data Manipulation Language) command, `DELETE` operations can be rolled back.
    
    - **Rollback:** Because it's a DML (Data Manipulation Language) command, `DELETE` operations can be rolled back.
    
    **Performance:** It's slower than `TRUNCATE` because it processes and logs individual row deletions.
    
    - **Performance:** It's slower than `TRUNCATE` because it processes and logs individual row deletions.
    
    **Table Structure:** The table's structure (columns, indexes, etc.) remains intact.
    
    - **Table Structure:** The table's structure (columns, indexes, etc.) remains intact.
    
    **TRUNCATE**
    
    **Purpose:** Deletes all records from a table quickly.
    
    - **Purpose:** Deletes all records from a table quickly.
    
    **Data Removal:** Removes all rows from the table at once.
    
    - **Data Removal:** Removes all rows from the table at once.
    
    **Rollback:** `TRUNCATE` cannot be rolled back like `DELETE`.
    
    - **Rollback:** `TRUNCATE` cannot be rolled back like `DELETE`.
    
    **Performance:** It is much faster than `DELETE` because it removes all data at once without individual row processing.
    
    - **Performance:** It is much faster than `DELETE` because it removes all data at once without individual row processing.
    
    **Table Structure:** The table structure and its indexes are preserved.
    
    - **Table Structure:** The table structure and its indexes are preserved.
    
    **DML vs. DDL:** `TRUNCATE` is often considered a DDL command in some systems, or a hybrid DML/DDL command, as it deallocates space and cannot be used with a `WHERE` clause.
    
    - **DML vs. DDL:** `TRUNCATE` is often considered a DDL command in some systems, or a hybrid DML/DDL command, as it deallocates space and cannot be used with a `WHERE` clause.
    
    **DROP**
    
    **Purpose:** Removes the entire table from the database.
    
    - **Purpose:** Removes the entire table from the database.
    
    **Data Removal:** Deletes all data, the table structure, and any associated indexes or constraints.
    
    - **Data Removal:** Deletes all data, the table structure, and any associated indexes or constraints.
    
    **Rollback:** `DROP` is a DDL command and cannot be rolled back.
    
    - **Rollback:** `DROP` is a DDL command and cannot be rolled back.
    
    **Performance:** It's a quick command because it removes the entire object from the database system.
    
    - **Performance:** It's a quick command because it removes the entire object from the database system.
    
    **Table Structure:** The table itself, along with its definition and all contents, is completely deleted.
    
    - **Table Structure:** The table itself, along with its definition and all contents, is completely deleted.
    
    **When to Use Which Command**
    
    Use DELETE when you need to remove specific rows conditionally or if you need to be able to roll back the operation.
    
    - Use DELETE when you need to remove specific rows conditionally or if you need to be able to roll back the operation.
    
    Use TRUNCATE to quickly delete all rows from a table, for example, to empty a temporary or staging table while keeping its structure.
    
    - Use TRUNCATE to quickly delete all rows from a table, for example, to empty a temporary or staging table while keeping its structure.
    
    Use DROP when you want to completely remove a table and all its associated objects from the database permanently.
    
    - Use DROP when you want to completely remove a table and all its associated objects from the database permanently.
    
- Union vs Union All
    
    The UNION and UNION ALL operators in SQL are used to combine the result sets of two or more SELECT statements into a single result set. The primary difference lies in how they handle duplicate rows: 
    
    **1. UNION:**
    
    - **Removes Duplicates:** The UNION operator combines the results of multiple SELECT statements and automatically removes duplicate rows from the final result set. Only unique rows are returned.
    - **Performance:** The process of identifying and removing duplicates adds overhead, making UNION generally slower than UNION ALL, especially with large datasets.
    - **Use Case:** Ideal when you need a distinct list of values from multiple sources and want to eliminate any redundant entries.
    
    Example:
    
    ```sql
    SELECT column1, column2 FROM table_a 
    UNION
    SELECT column1, column2 FROM table_b;
    ```
    
    ---
    
    **2. UNION ALL:**
    
    - **Includes Duplicates:** The UNION ALL operator combines the results of multiple SELECT statements and includes all rows from each statement, including any duplicate rows that may exist across the combined result sets.
    - **Performance:** Since no duplicate removal process is involved, UNION ALL is generally faster and more efficient than UNION.
    - **Use Case:** Preferred when you need to combine all records from different sources, regardless of whether they are duplicates, or when performance is a critical factor and duplicate removal is not required.
    
    Example:
    
    ```sql
    SELECT column1, column2 FROM table_a
    UNION ALL
    SELECT column1, column2 FROM table_b;
    ```
    
    ---
    
    **Key Considerations for both operators:**
    
    - **Number of Columns:** The SELECT statements being combined must have the same number of columns.
    - **Data Types:** The corresponding columns in each SELECT statement should have compatible data types.
    - **Order of Columns:** The order of columns in each SELECT statement should match to ensure meaningful results.
    
- Where vs Having in SQL
    
    In SQL, the WHERE clause filters individual rows based on specified conditions before any data grouping occurs, while the HAVING clause filters groups of rows based on conditions applied to aggregate functions (like COUNT or SUM) after the GROUP BY clause has been executed. Therefore, use WHERE to filter single data points and HAVING to filter groups of data. 
    
    Here's a breakdown of the key differences:
    
    **WHERE Clause**
    
    - **Purpose**: Filters individual rows from a table.
    - **Timing**: Applied before the GROUP BY clause.
    - **Conditions**: Works with conditions on single column values.
    - **Aggregate Functions**: Cannot be used with aggregate functions (e.g., COUNT(), SUM(), AVG()).
    - **Use Cases**: Selects rows that meet certain criteria, like WHERE City = 'California'.
    
    **HAVING Clause**
    
    - **Purpose**: Filters the result of a GROUP BY clause.
    - **Timing**: Applied after the GROUP BY clause.
    - **Conditions**: Works with conditions on aggregated data or aggregate functions.
    - **Aggregate Functions**: Designed specifically to work with aggregate functions.
    - **Use Cases**: Filters groups based on an aggregate condition, such as `HAVING AVG(Price) > 10`.
    
    **Imagine you have a list of all customers and their orders.**
    
    - **WHERE**
        
        is like looking at each individual customer and filtering out those from a specific city before you count their orders.
        
    - **HAVING**
        
        is like looking at the groups of orders for each customer (after you've counted them) and only keeping the customers whose total orders exceed a certain number.
        
    
    **When to Use Each**
    
    - Use WHERE when you want to filter based on conditions that apply to individual rows.
    - Use HAVING when you want to filter based on conditions that apply to aggregated results after a GROUP BY operation.
    - You can use both clauses in the same query; the WHERE clause filters rows first, and then the HAVING clause filters the resulting groups.
    
    Before going into examples, it’s important to understand the distinctions between the WHERE and HAVING clauses. The table below outlines their key differences for a clear comparison.
    
    | **WHERE Clause** | **HAVING Clause** |
    | --- | --- |
    | Filters rows before groups are aggregated. | Filters groups after the aggregation process.. |
    | WHERE Clause can be used without GROUP BY Clause | HAVING Clause can be used with GROUP BY Clause |
    | WHERE Clause implements in row operations | HAVING Clause implements in column operation |
    | WHERE Clause cannot contain aggregate function | HAVING Clause can contain aggregate function |
    | WHERE Clause can be used with SELECT, UPDATE, DELETE statement. | HAVING Clause can only be used with SELECT statement. |
    | WHERE Clause is used before GROUP BY Clause | HAVING Clause is used after GROUP BY Clause |
    | WHERE Clause is used with single row function like UPPER, LOWER etc. | HAVING Clause is used with multiple row function like SUM, COUNT etc. |
- What is a Primary Key vs Unique Key?
    
    **Primary Key:** Uniquely identity the table with providing identity with combination of unique values + not null values
    
    **Unique Key:** It is unique values with can have only one null value  in column. Multi unique key can exists in table.
    
    A primary key uniquely identifies each row in a table, cannot contain NULL values, and there can be only one per table, often creating a clustered index. A unique key also ensures unique values in a column or set of columns, but it allows a single NULL value and multiple unique keys can exist in a table, typically creating a non-clustered index. The main difference is that **a primary key enforces entity integrity by preventing NULLs and is the single designated identifier, while a unique key enforces uniqueness on other columns and can accommodate a single missing value**.  
    
    **Key Differences at a Glance**
    
    | Feature | Primary Key | Unique Key |
    | --- | --- | --- |
    | NULL Values | Not allowed | One NULL value allowed |
    | Number | Only one per table | Multiple per table |
    | Purpose | Primary identifier for all records | Guarantees uniqueness of other columns |
    | Index Type | Clustered index by default | Non-clustered index by default |
    | Auto-Increment | Often supported | Not supported |
- Difference between INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN?
    - INNER JOIN → common in both.
    - LEFT JOIN → all left + matches from right.
    - RIGHT JOIN → all right + matches from left.
    - FULL JOIN → all records from both (with NULLs).
- Difference between EXISTS and IN?
    
    
- What is the difference between Clustered and Non-Clustered Index?
- What is a Stored Procedure vs Function?
- How do you find the second highest salary?
- What are Common Performance Tuning Techniques?
