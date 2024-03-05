## Deleting Existing Tables
```sql
DROP TABLE Customers;
DROP TABLE Shippings;
DROP TABLE Orders;
```

## Creating Table and Inserting Data
```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50),
    manager_id INT
);

INSERT INTO employees (employee_id, name, manager_id) VALUES
(1, 'John', NULL),
(2, 'Alice', 1),
(3, 'Bob', 1),
(4, 'Carol', 2),
(5, 'David', 3);

CREATE TABLE departments (
    department_id INT PRIMARY KEY,
    name VARCHAR(50),
    manager_id INT
);

INSERT INTO departments (department_id, name, manager_id) VALUES
(1, 'HR', 2),
(2, 'Finance', 4),
(3, 'IT', 5);
```

## Self Join
```sql
SELECT e.name AS employee, m.name AS manager
FROM employees e
LEFT OUTER JOIN employees m ON e.manager_id = m.employee_id;
```

## Using Clause
```sql
SELECT d.name, e.name AS manager
FROM departments d
JOIN employees e USING(manager_id);
```

## Cross Join
```sql
SELECT e.name AS employee, d.name AS department
FROM employees e
CROSS JOIN departments d;
```

## UNION Operation
```sql
SELECT employee_id, name FROM employees
UNION
SELECT department_id, name FROM departments;
```

## Natural Join
```sql
Create Table department
(
   DEPT_NAME Varchar(20),
   MANAGER_NAME Varchar(255)
);
Create Table employee
(
   EMP_ID int,
   EMP_NAME Varchar(20),
   DEPT_NAME Varchar(255)
);
INSERT INTO department(DEPT_NAME,MANAGER_NAME) VALUES ( "IT", "ROHAN");
INSERT INTO department(DEPT_NAME,MANAGER_NAME) VALUES ( "SALES", "RAHUL");
INSERT INTO department(DEPT_NAME,MANAGER_NAME) VALUES ( "HR", "TANMAY");
INSERT INTO department(DEPT_NAME,MANAGER_NAME) VALUES ( "FINANCE", "ASHISH");
INSERT INTO department(DEPT_NAME,MANAGER_NAME) VALUES ("MARKETING", "SAMAY");
INSERT INTO employee(EMP_ID, EMP_NAME, DEPT_NAME) VALUES (1, "SUMIT", "HR");
INSERT INTO employee(EMP_ID, EMP_NAME, DEPT_NAME) VALUES (2, "JOEL", "IT");
INSERT INTO employee(EMP_ID, EMP_NAME, DEPT_NAME) VALUES (3, "BISWA", "MARKETING");
INSERT INTO employee(EMP_ID, EMP_NAME, DEPT_NAME) VALUES (4, "VAIBHAV", "IT");
INSERT INTO employee(EMP_ID, EMP_NAME, DEPT_NAME) VALUES (5, "SAGAR", "SALES");


--Natural Join
SELECT *
FROM employee
NATURAL JOIN department; 
```

## Column Attributes

In SQL, column attributes are properties that define the characteristics of a column in a table. These attributes include data type, constraints, and other properties that determine how data is stored and managed within the column. Here's a summary of common column attributes in SQL:

**1. Data Type:** Specifies the type of data that can be stored in the column, such as INTEGER, VARCHAR, DATE, etc. Each data type has specific storage requirements and rules for data manipulation.

2. Length/Size: For character data types like VARCHAR, CHAR, TEXT, etc., the length or size attribute specifies the maximum number of characters that can be stored in the column.

3. Primary Key: A column or combination of columns that uniquely identifies each row in the table. It ensures that each row has a unique identifier and helps enforce entity integrity.

4. Foreign Key: A column or combination of columns that establishes a link between two tables by referencing the primary key or a unique key in another table. It enforces referential integrity by ensuring that values in the foreign key column exist in the referenced table.

5. NOT NULL Constraint: Specifies that the column cannot contain NULL values, ensuring that every row must have a value for that column.

6. UNIQUE Constraint: Ensures that all values in the column are unique across the table, except for NULL values. It prevents duplicate values from being inserted into the column.

7. DEFAULT Constraint: Specifies a default value for the column if no value is provided during INSERT operations. It assigns the default value to the column when a new row is added to the table.

8. CHECK Constraint: Defines a condition that must be satisfied for the data in the column. It restricts the range of allowed values based on the specified condition.

9. Auto Increment/Identity: Automatically generates a unique value for the column when a new row is inserted into the table. It is commonly used for primary key columns to ensure unique identifiers for each row.

Here's an example of creating a table with some of these column attributes:

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    department_id INT,
    salary DECIMAL(10, 2) DEFAULT 0,
    hire_date DATE,
    CONSTRAINT fk_department FOREIGN KEY (department_id) REFERENCES departments(department_id)
);
```

In this example, the `employees` table has columns with various attributes:
- `employee_id` is the primary key column.
- `name` is a VARCHAR column with a NOT NULL constraint.
- `department_id` is an INT column that serves as a foreign key referencing the `department_id` column in the `departments` table.
- `salary` is a DECIMAL column with a DEFAULT constraint, which assigns a default value of 0 if no value is provided during INSERT.
- `hire_date` is a DATE column without any additional constraints.

These attributes help define the structure and behavior of columns in SQL tables, ensuring data integrity and consistency.