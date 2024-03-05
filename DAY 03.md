## Deleting Existing Tables
```
DROP TABLE Customers;
DROP TABLE Department;
DROP TABLE Employee;
DROP TABLE Shippings;
DROP TABLE Orders;
```

## Creating Table and Inserting Data
```
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
```
SELECT e.name AS employee, m.name AS manager
FROM employees e
LEFT OUTER JOIN employees m ON e.manager_id = m.employee_id;
```

## Using Clause
```
SELECT d.name, e.name AS manager
FROM departments d
JOIN employees e USING(manager_id);
```

## Cross Join
```
SELECT e.name AS employee, d.name AS department
FROM employees e
CROSS JOIN departments d;
```

## UNION Operation
```
SELECT employee_id, name FROM employees
UNION
SELECT department_id, name FROM departments;
```

## Natural Join
```
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