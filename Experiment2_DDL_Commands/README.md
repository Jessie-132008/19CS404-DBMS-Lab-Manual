=k# Experiment 2: DDL Commands

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
Write a SQL Query  to Rename attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date,State as varchar(30) in the table Companies. 

For example:

Test	Result
pragma table_info('Companies');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          int         0                       0
1           first_name  varchar(50  0                       0
2           address     text        0                       0
3           email       varchar(50  0                       0
4           phone       varchar(10  0                       0
5           mobilenumb  number      0                       0
6           DOB         Date        0                       0
7           State       varchar(30  0              


```sql
ALTER TABLE Companies
RENAME COLUMN name TO first_name;

ALTER TABLE Companies
ADD COLUMN mobilenumb number;

ALTER TABLE Companies
ADD COLUMN DOB Date;

ALTER TABLE Companies
ADD COLUMN State varchar(30);
```

**Output:**

<img width="1516" height="766" alt="image" src="https://github.com/user-attachments/assets/e9032319-37af-4bf5-a940-377991f8c06a" />



**Question 2**
---
Create a table named Events with the following columns:

EventID as INTEGER
EventName as TEXT
EventDate as DATE
For example:

Test	Result
pragma table_info('Events');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           EventID     INTEGER     0                       0
1           EventName   TEXT        0                       0
2           EventDate   DATE        0                       0



```sql
CREATE TABLE Events (
      EventID INTEGER,
      EventName TEXT,
      EventDate DATE
      
);
```

**Output:**

<img width="1532" height="753" alt="image" src="https://github.com/user-attachments/assets/56c1dedf-cba5-475c-8a54-551d294601c2" />



**Question 3**
---
Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
For example:

Test	Result
select * from student_details;
RollNo      Name           Gender      Subject     MARKS
----------  -------------  ----------  ----------  ----------
1           Alice Johnson  Female      Math        85
2           Bob Smith      Male        Science     90
3           Charlie Brown  Male        English     78


```sql
INSERT INTO Student_Details
SELECT * FROM Archived_students;
```

**Output:**

<img width="1561" height="743" alt="image" src="https://github.com/user-attachments/assets/0bd74557-5f72-4792-8c95-07eb0956eb10" />



**Question 4**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.
For example:

Test	Result
INSERT INTO Bonuses (BonusID, EmployeeID, BonusAmount, BonusDate, Reason) VALUES (1, 6, 1000.0, '2024-08-01', 'Outstanding performance');
SELECT * FROM Bonuses;


```sql
CREATE TABLE Bonuses (
    BonusID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    BonusAmount REAL CHECK
(BonusAmount > 0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EmployeeID)
References Employees(EmployeeID)
);
```

**Output:**

<img width="1521" height="711" alt="image" src="https://github.com/user-attachments/assets/4e2c98b4-203e-4c95-84d1-f56d506c4352" />



**Question 5**
---
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
 

For example:

Test	Result
pragma table_info('customer');
cid         name         type                               notnull     dflt_value  pk
----------  -----------  ---------------------------------  ----------  ----------  ----------
0           customer_id  integer primarykey auto increment  0                       0
1           cust_name    varchar2(30)                       0                       0
2           city         varchar(30)                        0                       0
3           grade        number                             0                       0
4           salesman_id  number                             0                       0
5           birth_date   timestamp            

```sql
ALTER TABLE customer ADD birth_date timestamp;
```

**Output:**

<img width="1472" height="817" alt="image" src="https://github.com/user-attachments/assets/a536642a-a5b5-48a1-a8e3-c9d2d2013a1d" />



**Question 6**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
For example:

Test	Result
INSERT INTO Orders (OrderID, OrderDate, CustomerID) VALUES (1, '2024-08-01', 1);
INSERT INTO Invoices (InvoiceID, InvoiceDate, Amount, DueDate, OrderID) VALUES (1, '2024-08-01', 100.0, '2024-09-01', 1);
SELECT * FROM Invoices;
InvoiceID   InvoiceDate  Amount      DueDate     OrderID
----------  -----------  ----------  ----------  ----------
1           2024-08-01   100.0       2024-09-01  1


```sql
CREATE TABLE Invoices(
  InvoiceID INTEGER PRIMARY KEY,
  InvoiceDate DATE,
  Amount REAL CHECK (Amount>0),
  DueDate DATE CHECK (DueDate > InvoiceDate),
  OrderID INTEGER,
  FOREIGN KEY (OrderID) REFERENCES Orders
);
```

**Output:**

<img width="1493" height="682" alt="image" src="https://github.com/user-attachments/assets/cbcf9ab7-affb-409f-9ccc-1e3d0d50fa00" />



**Question 7**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).
For example:

Test	Result
INSERT INTO Customers (CustomerID, FirstName, LastName, Email) VALUES (1, 'Alice', 'Johnson', 'alice.johnson@example.com');
INSERT INTO Orders (OrderID, OrderDate, CustomerID) VALUES (1, '2024-08-01', 1);
select * from orders;


```sql
CREATE TABLE Orders (
  OrderID INTEGER PRIMARY KEY,
  OrderDate DATE NOT NULL,
  CustomerID INTEGER,
  FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1467" height="673" alt="image" src="https://github.com/user-attachments/assets/564b752a-2876-4181-91fa-7f3e4ae2353f" />



**Question 8**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
For example:

Test	Result
INSERT INTO Invoices (InvoiceID, InvoiceDate)
VALUES (1, '2024-08-08'),(1,'2024-09-08');
Error: UNIQUE constraint failed: Invoices.InvoiceID


```sql
CREATE TABLE Invoices (
  InvoiceID INTEGER PRIMARY KEY,
  InvoiceDate DATE,
  DueDate DATE,
  Amount REAL,
  CHECK (DueDate > InvoiceDate),
  CHECK (Amount > 0)
);
```

**Output:**

<img width="1482" height="657" alt="image" src="https://github.com/user-attachments/assets/192d5af0-2817-48cf-9acb-cacb5747bcdc" />



**Question 9**
---
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

For example:

Test	Result
SELECT * FROM Books;
ISBN            Title                    Author      Publisher   Year
--------------  -----------------------  ----------  ----------  ----------
978-1234567890  Data Science Essentials  Jane Doe    TechBooks   2024

```sql
INSERT INTO Books (ISBN,Title,Author,Publisher,Year) VALUES ('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**

<img width="1481" height="617" alt="image" src="https://github.com/user-attachments/assets/6ebc9f5f-4f49-4130-a517-c3e190a01572" />



**Question 10**
---
Write a SQL Query for inserting the below values in the table Customers

ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000
 

For example:

Test	Result
SELECT * FROM Customers;
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Ramesh      32          Ahmedabad   2000
2           Khilan      25          Delhi       1500
3           Kaushik     23          Kota        2000

```sql
INSERT INTO Customers(ID,NAME,AGE,ADDRESS,SALARY) VALUES (1,'Ramesh',32,'Ahmedabad',2000);
INSERT INTO Customers(ID,NAME,AGE,ADDRESS,SALARY) VALUES (2,'Khilan',25,'Delhi',1500);
INSERT INTO Customers(ID,NAME,AGE,ADDRESS,SALARY) VALUES (3,'Kaushik',23,'Kota',2000);


```

**Output:**

<img width="1467" height="736" alt="image" src="https://github.com/user-attachments/assets/6fd05602-e027-4588-ad6f-245657f7d4fa" />



**Grade Page:**

<img width="1847" height="862" alt="image" src="https://github.com/user-attachments/assets/6f07f4f3-7a6d-4c32-9996-3a547fe586b8" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
