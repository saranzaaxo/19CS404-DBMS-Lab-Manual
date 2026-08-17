
# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many prescriptions were written by each doctor?

Sample tablePrescriptions Table

<img width="1082" height="154" alt="image (8)" src="https://github.com/user-attachments/assets/847c2cd4-6f98-4861-8fcf-c4b6314b136a" />



```sql
SELECT DoctorID, COUNT(PrescriptionID) AS TotalPrescriptions
FROM Prescriptions
GROUP BY DoctorID;
```

**Output:**

<img width="456" height="526" alt="image" src="https://github.com/user-attachments/assets/1167e070-465f-4a48-8e08-d19587cbed42" />


**Question 2**
---
How many medical records does each doctor have?

Sample table:MedicalRecords Table

<img width="1089" height="164" alt="image (6)" src="https://github.com/user-attachments/assets/eafc4097-884e-4574-8cb9-eba75adc95db" />


```sql
SELECT DoctorID, COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID;
```

**Output:**
<img width="385" height="467" alt="image" src="https://github.com/user-attachments/assets/73ec8555-470d-4010-8915-ed3bf7f7da81" />


**Question 3**
---
What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table

<img width="1082" height="154" alt="image (8)" src="https://github.com/user-attachments/assets/6ae5c6fa-3acd-4517-b033-2fc669a21ac8" />

```sql
SELECT PatientID, COUNT(Medication) AS TotalMedications
FROM Prescriptions
GROUP BY PatientID;

```

**Output:**

<img width="426" height="551" alt="image" src="https://github.com/user-attachments/assets/3ab1e566-5d30-43cc-b83f-a9ff23f9c585" />



**Question 4**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

Sample table: customer

<img width="668" height="138" alt="image (3)" src="https://github.com/user-attachments/assets/9130007b-6309-4753-9e42-0b4c8f1ebe2f" />


```sql
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city != 'Noida';
```

**Output:**

<img width="221" height="235" alt="image" src="https://github.com/user-attachments/assets/bf7fa4e1-27c2-4c78-864c-b0c7e9881d57" />



**Question 5**
---
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER


```sql
SELECT MAX(age)- MIN(age) AS age_difference
FROM employee;
```

**Output:**
<img width="266" height="237" alt="image" src="https://github.com/user-attachments/assets/bed14764-065c-4317-9e7f-76ab14751b8b" />



**Question 6**
---
Write a SQL query to find  how many employees work in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
SELECT COUNT(*) AS employees_in_california
FROM employee
WHERE city ='California';
```

**Output:**
<img width="372" height="240" alt="image" src="https://github.com/user-attachments/assets/ff5dc015-7522-46b4-b4cb-9c462bd1fe79" />



**Question 7**
---
Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee


```sql
SELECT COUNT(*) AS COUNT
FROM employee
WHERE age > 32;
```

**Output:**

<img width="213" height="241" alt="image" src="https://github.com/user-attachments/assets/68fc0dce-4833-4a91-8bda-b09bbef6ea73" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

<img width="992" height="173" alt="unnamed" src="https://github.com/user-attachments/assets/6a26f95d-b1a8-4523-9274-1a85b737aea5" />


```sql
SELECT (age/5)*5 AS age_group, AVG(age)
FROM customer1
GROUP BY (age/5)*5
HAVING AVG(age)<24;
```

**Output:**

<img width="372" height="243" alt="image" src="https://github.com/user-attachments/assets/fbbb4b64-796b-46f7-912a-2e21aba56485" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

Sample table: employee

<img width="1011" height="215" alt="unnamed" src="https://github.com/user-attachments/assets/d260d7f3-fe2a-4559-aaa1-6fdeba608914" />


```sql
SELECT age, MIN(income)
FROM employee
GROUP BY age
HAVING MIN(income) < 400000;
```

**Output:**

<img width="380" height="287" alt="image" src="https://github.com/user-attachments/assets/c3b14df7-46c2-4c15-9d73-3a8530df28a8" />



**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

```sql
SELECT occupation, MIN(workhour)
FROM employee1
GROUP BY occupation
HAVING MIN(workhour)>8;
```

**Output:**


<img width="402" height="357" alt="image" src="https://github.com/user-attachments/assets/699b9f8a-16b0-4bc9-ab27-60c540a8c338" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
