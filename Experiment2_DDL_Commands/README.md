# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
CREATE TABLE Employees (
EmployeeID INT PRIMARY KEY,
FirstName VARCHAR(50) NOT NULL,
LastName  VARCHAR(50) NOT NULL,
Email VARCHAR(100) UNIQUE,
Salary INT CHECK (Salary>0),
DepartmentID INT REFERENCES Departments(departmentID)
);
```

**Output:**

<img width="1290" height="307" alt="image" src="https://github.com/user-attachments/assets/5c4c02c8-2fcb-4938-8a1a-ebc54a9dff5a" />



**Question 2**
---
Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies. 

```sql
ALTER TABLE Companies RENAME COLUMN name TO first_name;
ALTER TABLE Companies ADD mobilenumb number;
ALTER TABLE Companies ADD DOB Date;
```

**Output:**

<img width="1172" height="302" alt="image" src="https://github.com/user-attachments/assets/b36bd8df-5fbd-4ded-b345-2810f0bf86e6" />


**Question 3**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values.    

```sql
INSERT INTO Employee (EmployeeID, Name, Position)
VALUES (4, 'Emily White', 'Analyst');
```

**Output:**

<img width="747" height="265" alt="image" src="https://github.com/user-attachments/assets/9d11281d-6b93-4df7-861e-a46a73b118af" />
 

**Question 4**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
CREATE TABLE Products (
ProductID INTEGER PRIMARY KEY,
ProductName TEXT UNIQUE NOT NULL,
Price REAL CHECK (Price>0),
StockQuantity INTEGER CHECK (StockQuantity >= 0)
);
```

**Output:**

<img width="1150" height="167" alt="image" src="https://github.com/user-attachments/assets/1063cb46-4e71-46ac-bc2d-2ee3e54a3f61" />


**Question 5**
---
Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.

```sql
ALTER TABLE Student_details ADD ParentsNumber number;
ALTER TABLE Student_details ADD Adhar_Number number;
```

**Output:**

<img width="1185" height="292" alt="image" src="https://github.com/user-attachments/assets/98c2ceda-43ee-48df-9d76-33917019ac65" />

**Question 6**
---
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300

```sql
INSERT INTO Products (Name, Category, Price, Stock) VALUES
('Smartphone', 'Electronics', 800, 150),
('Headphones', 'Accessories', 200,300);
```

**Output:**

<img width="987" height="267" alt="image" src="https://github.com/user-attachments/assets/c723c32d-67bb-4755-9926-0f80dc331551" />


**Question 7**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.

```sql
CREATE TABLE Invoices (
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
DueDate DATE CHECK(DueDate > InvoiceDate),
Amount REAL CHECK(Amount > 0)
);
```

**Output:**

<img width="1010" height="220" alt="image" src="https://github.com/user-attachments/assets/a249ce4b-9510-40b5-8340-792708b320be" />


**Question 8**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders (
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1290" height="217" alt="image" src="https://github.com/user-attachments/assets/52a1dc60-c6d9-4729-9be8-c5ceda1b6ba8" />


**Question 9**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```sql
INSERT INTO Products SELECT * FROM Discontinued_products;
```

**Output:**

<img width="863" height="217" alt="image" src="https://github.com/user-attachments/assets/f348af5c-162a-438c-b9f4-f4c523fdd0f6" />


**Question 10**
---
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE

```sql
CREATE TABLE Employees 
(EmployeeID  INTEGER,
FirstName  TEXT,
LastName  TEXT,
HireDate  DATE
);
```

**Output:**

<img width="1072" height="233" alt="image" src="https://github.com/user-attachments/assets/214309e7-ecb7-43ee-ba83-e3035f4b3973" />




## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
