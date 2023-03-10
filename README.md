# PostgresSQL Syntax

## CREATE Table
```sql
Syntax: CREATE TABLE table_name(
      Column_name data_type constraint,
      Column_name data_type constraint,
      Column_name data_type constraint,
      .
      .
      .
      Column_name data_type constraint
);
```
---
## Cascade in SQL

**Cascade in SQL** is used to simultaneously delete or update an entry from both the child and parent table.

---
## Insert Query
It is used to insert the values into the table. 
```sql
      a. For single row data insert
      INSERT INTO tableName (col1, col2, ..., coln) 
      VALUES 
      ('value1', 'value2', ... , 'valuen');
```
---

```sql
    b. For multiple row data
      INSERT INTO tableName (col1, col2, ..., coln) 
      VALUES 
      ('value1', 'value2', ... , 'valuen'),
      ('value1', 'value2', ... , 'valuen'),
      ('value1', 'value2', ... , 'valuen'),
      .
      .
      .
      ('value1', 'value2', ... , 'valuen');
```
---      

## ALTER TABLE

Alter table is used to add/modify/drop/ rename the cloumn from existing table. It is also used to add/drop the constraint from your existing table.

- **ADD COLUMN**
  ```sql
        ALTER TABLE table_name ADD Column Column_name Column_Definition;
  ```
- **REMOVE the Column**
  ```sql
        ALTER TABLE table_name DROP Column Column_name; 
  ```
- **Modify the COLUMN** 
  ```sql
      ALTER TABLE table_name ALTER Column Column_name TYPE Column_definiton;
  ```
- **ADD Constraint**
  ```sql
      ALTER TABLE table_name ADD Constraint Constraint_name Constraint_Definition;
  
      Eg.: ALTER TABLE table_name ADD Constraint age_constraint CHECK (age>18);
  ```
- **Drop Constraint**
  ```sql
      ALTER TABLE table_name DROP Constraint Constraint_name;
  ```
- **Rename COLUMN name**
  ```sql
      ALTER TABLE table_name RENAME Column old_name to new_name;
  ```
---
## UPDATE QUERY
* is used/modify existing record in a table.
  ```sql
      Syntax:
            UPDATE table_name SET column_name1 = 'new value', Column_name2 = 'new value', ..., Column_namen = 'new value' WHERE Condition;
      
      Example:
            UPDATE offices SET Oname = 'XYZ' WHERE Onumber = '1';
  ```
---
## DELETE QUERY
* is used to remove records from table
  ```sql
      Syntax:
            DELETE FROM table_name WHERE Condition;
      Example:
            DELETE FROM Offices WHERE Onumber = '2';
  ```
---
## DROP QUERY
* Drop is used to remove table or whole database 
  ```sql
        a) TO REMOVE table
              DROP TABLE IF EXISTS table_name;
        b) TO REMOVE Database optional
              DROP DATABASE IF EXISTS db_name;
  ```
---
## SELECT QUERY
* Query is used to retreive the desire records from table
```sql
      Syntax:
            SELECT Col1, Col2, ..., Coln FROM table_name;
```
---

### **Table: Student**
|  ID   | Name  | Email       | Contact    |
| :---: | :---: | ----------- | ---------- |
|   1   |   A   | a@gmail.com | 9841457895 |
|   2   |   B   | b@gmail.com | 9846283576 |

```sql
      Example:
            Select name, email FROM Student;
                -- It will retreive the name, email of student
      
      - To retreive all columns 
          -- this is wildcard, which represents all column
             ^
      SELECT * FROM Student;

      - To filter the record (use WHERE Clause)
            Syntax:
                  SELECT * FROM table_name WHERE Condition;
      
      - To SORT the records
            Syntax:
                  SELECT * FROM table_name WHERE condition ASC/DESC;
                        -- ASC = Ascending, DESC = Descending
```
---

## SQL Clauses

-  **Group By**
     - is used to group the records 
     - Always use with SELECT Query
     - must use with some 
       ```c++
            aggregate_function(avg, sum, count, min, max )
       ```
     - It is always followed by WHERE Clauses and preceeds the order by Clause.
    
       ```sql
       Example: SELECT aggregate_function(col_name) FROM table_name GROUP by col_name;
---
-  **Having Clause**
   -  Behave like a WHERE Clause but only used with group by clause.
   -  to alter the group related to group by clause

      ```sql
      Syntax: SELECT col_name, aggregate_function(col_name) FROM table_name Group by column_name having condition;
---
- **Order by Clause**
  - is used to sort the records in ascending/decsending order.
  - by default it sort the records in ascending order
  
      ```sql
      Syntax: SELECT * FROM table_name WHERE condition ORDER BY column_name ASC/DESC;
---
- **Limit**
  - Limit is used to Limit the number of results of the SELECT Query
  
      ```sql
      Syntax: SELECT * FROM table_name WHERE condition limit 10; 
                  (It only displays the 10 results)
---

## WildCard
- It is a special character used to substitute the one or more character in string 
- % is used to represent zero or more character
- _ is used to represent exactly one character

Wildcard character are always used with **Like operator**.
```sql
For Example: SELECT * FROM Employee WHERE Ename Like 'R%'
--This returns records of employee whose name start with R

SELECT * FROM Employee WHERE Ename Like 'R__';
--returns the employee records whose name start with R and have exactly 3 characters
```
---
## Join 
```sql
      Syntax: For table JOIN
      a) Cross Join
            SELECT Col1, Col2, ... FROM table1 CROSS JOIN table2;
      b) Inner Join/ Right Join/ Left Join/ Outer Join/ Full Join
            SELECT Col1, Col2, ... FROM tabe1
            INNER JOIN -- (Repacable by Right, Left, Outer & Full Join)
            table2 ON
                  table1.column_field = table2.column_field; 
```
---
## Sub Query
A sub query or inner query or nested query is a query within a another SQL Query and embedded within the `WHERE` clause. A sub query is used to return a data that will be used in the main query (outer query) as a condition to further restrict the data to be retrieved. Sub Query can be used with `SELECT, INSERT, UPDATE and DELETE` statement along with the operators like `=, <, >, <=, >=, IN, between` etc. There are few rules that Sub Query must follow:

- Sub query must be enclosed within parenthesis '( )'
- A Sub query can have only one column in the `SELECT` caluse unless multiple columns are in the main query for the sub query to compare its selected columns
- An `order by` caluse cannot be used in sub query although the main query can use an `order by` clause
- Sub queries that return more than one row can only be used with multiple value operators such as the `IN` operator 

```sql
Syntax: SELECT * FROM table_name WHERE column_name (SELECT name FROM table2)
```
---

## Question
### Consider the following database, where primary key are underlined 
teacher(tid, tname, qualification) </br>
teaches(tid, cid) </br>
course(cid, cname, ccode) </br>
Write the RA and SQL Query query for the following 
1. Find the names of all teachers who have Phd Qualification.
2. Find the name of all course taught by Ram Prasad.
3. Find the total number of course taught bt Ram Prasad. 
