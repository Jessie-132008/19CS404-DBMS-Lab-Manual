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
What is the average duration of insurance coverage for patients covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
StartDate          DATE
EndDate            DATE
For example:

Result
InsuranceCompany  AvgCoverageDurationDays
----------------  -----------------------
ABC Insurance     7.0
DEF Insurance     3.0
JKL Insurance     3.0
STU Insurance     3.0
VWX Insurance     3.0
XYZ Insurance     3.0
YZA Insurance     3.0

```sql
SELECT InsuranceCompany,ROUND(AVG(julianday(EndDate)-julianday(StartDate))/365.0,1) AS AvgCoverageDurationDays
FROM Insurance GROUP BY InsuranceCompany;
```

**Output:**

<img width="1442" height="752" alt="image" src="https://github.com/user-attachments/assets/dd1f3d34-cd80-42ae-9606-de6375d9fbd8" />



**Question 2**
---
How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table



For example:

Result
Specialty          Gender    TotalDoctors
-----------------  --------  --------------
Cardiology         Male      1
Dermatology        Male      1
Gastroenterology   Female    4
Gastroenterology   Male      1
Pediatrics         Female    1
Pediatrics         Male      2

```sql
SELECT Specialty,Gender,COUNT(*) AS TotalDoctors FROM Doctors GROUP BY Specialty,Gender;
```

**Output:**
<img width="1441" height="800" alt="image" src="https://github.com/user-attachments/assets/e0f396ae-3324-4862-86f0-6800b1dda904" />



**Question 3**
---
What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table



For example:

Result
PatientID   TotalMedications
----------  ----------------
1           1
2           1
3           1
4           1
5           1
6           1
7           1
8           1
9           1
10          1


```sql
SELECT PatientID,COUNT(*) AS TotalMedications FROM Prescriptions GROUP BY PatientID;
```

**Output:**
<img width="1331" height="847" alt="image" src="https://github.com/user-attachments/assets/5606604c-b698-414c-84b7-883af59b5fae" />



**Question 4**
---
Write a SQL query to  find the average salary of all employees?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 

For example:

Result
Average_Salary
--------------
1568750.0


```sql
SELECT AVG(income) AS Average_Salary FROM employee;
```

**Output:**
<img width="1446" height="742" alt="image" src="https://github.com/user-attachments/assets/27681dff-e83c-4fdb-b154-a78bfeb4265d" />



**Question 5**
---
Write a SQL query to find the customer with longest name?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
name          length
------------  ----------
Preeti Patel  12


```sql
SELECT name,LENGTH(name) AS length FROM customer ORDER BY Length(name) DESC LIMIT 1;
```

**Output:**
<img width="1447" height="742" alt="image" src="https://github.com/user-attachments/assets/b74de775-ddac-4556-9461-041b9fe1f21c" />



**Question 6**
---
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

Sample table: employee

id

name

age

address

salary

1

Paul

32

California

20000

4

Mark

25

Richtown

65000

5

David

27

Texas

85000

 

For example:

Result
COUNT
----------
4


```sql
SELECT COUNT(DISTINCT age) AS COUNT FROM employee;
```

**Output:**
<img width="1397" height="727" alt="image" src="https://github.com/user-attachments/assets/abaf05f0-11a0-481f-8678-47e3d59104ac" />



**Question 7**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

For example:

Result
TOTAL
----------
17541.18

```sql
SELECT SUM(purch_amt) AS TOTAL FROM orders;
```

**Output:**
<img width="1347" height="730" alt="image" src="https://github.com/user-attachments/assets/f4a43e85-5834-4e17-8bc4-a5242d2caae7" />



**Question 8**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

Sample table: customer1



For example:

Result
address     SUM(salary)
----------  -----------
Bhopal      8500
Hyderabad   4500
Indore      10000
Mumbai      6500


```sql
SELECT address,SUM(salary) FROM customer1 GROUP BY address HAVING SUM(salary) > 2000;
```

**Output:**
<img width="1476" height="832" alt="image" src="https://github.com/user-attachments/assets/c42aca5d-b445-4714-ae5d-0fd3be3f3fa5" />



**Question 9**
---
Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3.

Sample table: products



For example:

Result
category_id  count(product_name)
-----------  -------------------
1            4
2            3

```sql
SELECT category_id,count(product_name) FROM products GROUP BY category_id HAVING MIN(category_id)<3;
```

**Output:**


<img width="1452" height="757" alt="image" src="https://github.com/user-attachments/assets/13695d31-514d-44f1-86fd-f5398647dc1b" />

**Question 10**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.

Sample table: customer1



For example:

Result
age_group   AVG(age)
----------  ----------
20          23.0


```sql
SELECT (age/5)*5 AS age_group,AVG(age) AS "AVG(age)" FROM customer1 GROUP BY age_group HAVING AVG(age)<24;
```

**Output:**

<img width="1500" height="705" alt="image" src="https://github.com/user-attachments/assets/fecd3047-a7c0-4250-8a55-aad63b7206f1" />


## SEB MODULE:

<img width="1485" height="741" alt="image" src="https://github.com/user-attachments/assets/0c390b50-cee0-40a0-9fc3-317e51024e5f" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
