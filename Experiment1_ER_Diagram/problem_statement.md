# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="1892" height="907" alt="image" src="https://github.com/user-attachments/assets/7d00a257-1d57-46a9-b7a8-eba3dbae7e77" />


### Entities and Attributes

| **Entity**  | **Attributes (PK, FK)**                                                                | **Notes**                                                        |
| ----------- | -------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **Member**  | **M_ID (PK)**, M_name, Phone_no, Mem_type, Start_date, Address (Street, City, Pincode) | Stores details of gym members. Address is a composite attribute. |
| **Session** | **Session_ID (PK)**, Date                                                              | Stores information about gym sessions.                           |
| **Trainer** | **Trainer_ID (PK)**, Name, Experience                                                  | Stores trainer details who conduct sessions.                     |
| **Payment** | **P_ID (PK)**, P_Date, Amount                                                          | Stores member payment details.                                   |
| **Program** | **P_ID (PK)**, P_Name, Duration                                                        | Stores gym program details assigned to trainers and members.     |


### Relationships and Constraints

| **Relationship** | **Entities Involved** | **Description**                    |
| ---------------- | --------------------- | ---------------------------------- |
| **Books**        | Member ↔ Session      | Members book gym sessions.         |
| **Conducts**     | Trainer ↔ Session     | Trainers conduct gym sessions.     |
| **Makes**        | Member ↔ Payment      | Members make payments.             |
| **Enrolls**      | Member ↔ Program      | Members enroll in gym programs.    |
| **Assigns**      | Trainer ↔ Program     | Trainers are assigned to programs. |


### Assumptions
Each member has a unique Member ID (M_ID).
A member can enroll in multiple programs, but each enrollment is recorded separately.
Each program is assigned to one trainer at a time.
A trainer can conduct multiple sessions.
A session is conducted by only one trainer.
A member can book multiple sessions.
Every payment is made by only one member.
Each payment has a unique Payment ID (P_ID).
Every member has one address, which consists of Street, City, and Pincode.
Attendance is recorded for members attending sessions.
---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="1886" height="876" alt="image" src="https://github.com/user-attachments/assets/9f1ffe09-5d57-4ba2-adcb-29984f4a9e30" />


### Entities and Attributes

| **Entity**  | **Attributes (PK, FK)**                          | **Notes**                                                                                       |
| ----------- | ------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| **Member**  | **M_ID (PK)**, M_Name, Name, Ph_no, Join_Date    | Stores details of library members.                                                              |
| **Book**    | **B_ID (PK)**, Title, Attribute                  | Stores information about library books. *(You can rename "Attribute" to Category if required.)* |
| **Loan**    | **Loan_ID (PK)**, Loan_Date                      | Stores details of book loans.                                                                   |
| **Fine**    | **Fine_ID (PK)**, Amount, Fine_Date, Paid_Status | Stores overdue fine details.                                                                    |
| **Event**   | **E_ID (PK)**, E_Name, E_Date, E_Type            | Stores library event details.                                                                   |
| **Speaker** | **S_ID (PK)**, Name, Type                        | Stores speaker/author details for events.                                                       |
| **Room**    | **R_ID (PK)**, R_Name, R_Type, Capacity          | Stores room details for events or study.                                                        |


### Relationships and Constraints

| **Relationship** | **Entities Involved** | **Description**                                               |
| ---------------- | --------------------- | ------------------------------------------------------------- |
| Borrow     | Member ↔ Book         | Members borrow books.                                         |
| **Register**     | Book ↔ Event          | Connects books with related events (as shown in the diagram). |
| **Has**          | Event ↔ Speaker       | An event has one or more speakers.                            |
| **Booked_In**    | Speaker ↔ Room        | Speakers are assigned/booked into rooms.                      |
| **Generates**    | Loan ↔ Fine           | A late loan generates a fine.                                 |



### Assumptions

1.Each member has a unique Member ID (M_ID).
2.Each book has a unique Book ID (B_ID).
3.A member can borrow multiple books, but each loan is recorded separately.
4.Each loan has a unique Loan ID.
5.A fine is generated only if a book is returned late.
6.Each event has a unique Event ID (E_ID).
7.An event can have one or more speakers.
8.A speaker can participate in multiple events.
9.Each room has a unique Room ID (R_ID) and can host events based on its capacity.
10.Members can register for library events.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
