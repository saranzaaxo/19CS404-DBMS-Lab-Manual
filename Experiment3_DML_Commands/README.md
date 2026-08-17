# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to Update the grade of all customers in Chennai city as  5. 

Customer table (customer_id,cust_name,city,grade,salesman_id)

```sql
VUPDATE customer 
SET grade = 5
WHERE city = 'Chennai';
```

**Output:**

<img width="1112" height="335" alt="image" src="https://github.com/user-attachments/assets/045cde5d-00c5-45fa-b337-918d2bd12b5e" />


**Question 2**
---
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE Products
SET quantity=quantity*1.10;
```

**Output:**

<img width="1071" height="330" alt="image" src="https://github.com/user-attachments/assets/1dc3c0bd-765e-49cd-9251-33e54d721ed9" />


**Question 3**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
For example:

```sql
UPDATE suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**

<img width="1326" height="217" alt="image" src="https://github.com/user-attachments/assets/717f6d83-997a-49d3-9ff8-2af96f813917" />


**Question 4**
---
Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE Employees
SET salary = 8000
WHERE employee_id = 105 AND salary < 5000;
```

**Output:**

<img width="937" height="137" alt="image" src="https://github.com/user-attachments/assets/446fd90b-57ba-45db-b552-fd51d7eecf7d" />



**Question 5**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**


<img width="505" height="106" alt="image" src="https://github.com/user-attachments/assets/81742a02-b9ee-4b74-8be5-5fb87e32f9b7" />


**Question 6**
---

Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
-- DELETE FROM customer
WHERE WORKING_AREA ='New York';
```

**Output:**


<img width="1212" height="332" alt="image" src="https://github.com/user-attachments/assets/82d4d0a1-dd6a-4aeb-9b4a-a30deebaa7fb" />


**Question 7**
---
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN ('UK','USA','Canada')
 AND GRADE >= 3;
```

**Output:**


<img width="1218" height="186" alt="image" src="https://github.com/user-attachments/assets/44766142-5e20-46e9-95a4-aac8975f6288" />


**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

Sample table: Customer

```sql
DELETE FROM customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;
```

**Output:**


<img width="1096" height="225" alt="image" src="https://github.com/user-attachments/assets/5ba06740-f609-4adf-bf2f-fea161b54a85" />

**Question 9**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```sql
DELETE FROM Surgeries
WHERE surgery_id = 3;
```

**Output:**


<img width="835" height="280" alt="image" src="https://github.com/user-attachments/assets/2b516e7b-6909-43b9-8924-b3c0c8521052" />


**Question 10**
---
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

Sample table: Customer

```sql
DELETE FROM Customer
WHERE GRADE = 2
AND CUST_NAME LIKE 'M%'
AND PAYMENT_AMT <3000;
```

**Output:**


<img width="1037" height="153" alt="image" src="https://github.com/user-attachments/assets/86c94241-2cee-4d29-b10d-41b2a6fdba57" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
