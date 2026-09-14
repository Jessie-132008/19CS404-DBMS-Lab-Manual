# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.

```sql
SELECT p.first_name AS patient_name, d.first_name AS doctor_name 
FROM PATIENTS p 
INNER JOIN DOCTORS d
ON p.doctor_id = d.doctor_id 
WHERE p.discharge_date > '1990-01-01';
```

**Output:**

<img width="745" height="347" alt="image" src="https://github.com/user-attachments/assets/b2592f91-7724-47de-9865-06532e40844d" />


**Question 2**
---

-- Write the SQL query that achieves the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column. Include conditions to filter for patients discharged between '2024-03-01' and '2024-03-31' but not admitted during the same period.

```sql
select p.first_name, s.surgery_id, p.patient_id, s.surgeon_id, s.surgery_date 
FROM PATIENTS p
INNER JOIN SURGERIES s 
ON p.patient_id = s.patient_id 
WHERE p.discharge_date BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**

<img width="1254" height="433" alt="image" src="https://github.com/user-attachments/assets/7c15d347-950a-43f6-987e-5789ad57365e" />


**Question 3**
---
-- From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```sql
SELECT c.cust_name AS "Customer Name", c.city, s.name as Salesman, s.commission 
FROM customer c 
JOIN salesman s 
ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1262" height="802" alt="image" src="https://github.com/user-attachments/assets/c7b18e99-6340-4246-a368-def9018806f3" />


**Question 4**
---
-- Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.

```sql
SELECT c.cust_name, o.ord_no, o.ord_date, o.purch_amt 
FROM CUSTOMER c
LEFT JOIN ORDERS o
ON c.customer_id = o.customer_id;
```

**Output:**

<img width="1254" height="785" alt="image" src="https://github.com/user-attachments/assets/3db6204e-f000-4454-912f-e79c004be476" />


**Question 5**
---
-- write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

```sql
SELECT s.name AS "Salesman", c.cust_name, s.city 
FROM salesman s, customer c
WHERE s.city = c.city;
```

**Output:**

<img width="1061" height="645" alt="image" src="https://github.com/user-attachments/assets/ce6d8714-31f4-48af-ab9f-abbecdb1658a" />


**Question 6**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```sql
SELECT p.first_name AS "patient_name", d.specialization AS "Doctor_specialization" 
FROM PATIENTS p 
INNER JOIN DOCTORS d 
ON p.doctor_id = d.doctor_id 
WHERE p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="729" height="350" alt="image" src="https://github.com/user-attachments/assets/6e3af8fd-7d47-43b3-8989-8f498541486b" />


**Question 7**
---
-- Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned.

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, c.cust_name, c.city AS "customer_city", c.grade, s.name AS "salesman_name", s.city AS "salesman_city", s.commission
FROM orders o 
INNER JOIN customer c
ON o.customer_id = c.customer_id 
INNER JOIN salesman s
ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1255" height="780" alt="image" src="https://github.com/user-attachments/assets/dcc7543c-18e2-4cd3-b711-1e216ff45444" />


**Question 8**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

```sql
-- SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount",
    s.name AS "name",
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1247" height="784" alt="image" src="https://github.com/user-attachments/assets/0a30ff4c-dbe1-4b28-b7f1-08f214e4fa0f" />


**Question 9**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.

```sql
SELECT 
    s.name, 
    c.cust_name, 
    c.city, 
    c.grade, 
    c.salesman_id
FROM 
    customer c
LEFT JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.salesman_id IN (
        SELECT 
            salesman_id 
        FROM 
            customer 
        GROUP BY 
            salesman_id 
        HAVING 
            COUNT(customer_id) > 1
    )
ORDER BY 
    c.salesman_id, c.customer_id;

```

**Output:**
<img width="1255" height="639" alt="image" src="https://github.com/user-attachments/assets/6922fa3f-4fb0-4015-b0d7-6d1b4defe720" />



**Question 10**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

```sql
-- SELECT o.ord_no, o.purch_amt, c.cust_name, c.city 
FROM orders o
INNER JOIN customer c
ON o.customer_id = c.customer_id 
WHERE o.purch_amt BETWEEN 500 AND 2000
ORDER BY o.ord_no;
```

**Output:**

<img width="1254" height="510" alt="image" src="https://github.com/user-attachments/assets/d90dae65-e35d-4988-8149-b565f65720cc" />


## SEB MODULE:

<img width="1485" height="741" alt="image" src="https://github.com/user-attachments/assets/88a8d40d-5771-4d2d-b8b5-97f499178233" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
