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

1.Each member has a unique Member ID (M_ID).
2.A member can enroll in multiple programs, but each enrollment is recorded separately.
3.Each program is assigned to one trainer at a time.
4.A trainer can conduct multiple sessions.
5.A session is conducted by only one trainer.
6.A member can book multiple sessions.
7.Every payment is made by only one member.
8.Each payment has a unique Payment ID (P_ID).
9.Every member has one address, which consists of Street, City, and Pincode.
10.Attendance is recorded for members attending sessions.
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
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/73a55eb4-ca4e-44a7-9664-87a0d1eac87b" />


### Entities and Attributes

| **Entity**      | **Attributes (PK, FK)**                                                                             | **Notes**                                                          |
| --------------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Customer**    | **Customer_ID (PK)**, Name, Phone, Email                                                            | Stores customer details.                                           |
| **Reservation** | **Reservation_ID (PK)**, **Customer_ID (FK)**, Table_No, Date, Time, No_of_Guests, Reservation_Type | Stores reservation or walk-in details.                             |
| **Waiter**      | **Waiter_ID (PK)**, Name, Phone                                                                     | Stores waiter information.                                         |
| **Order**       | **Order_ID (PK)**, **Reservation_ID (FK)**, Order_Time, Order_Status                                | Stores orders placed under a reservation.                          |
| **Order_Item**  | **Order_ID (FK)**, **Dish_ID (FK)** *(Composite PK)*, Quantity, Unit_Price, Subtotal                | Stores individual dishes in an order.                              |
| **Dish**        | **Dish_ID (PK)**, Dish_Name, Price, **Category_ID (FK)**                                            | Stores menu items offered by the restaurant.                       |
| **Category**    | **Category_ID (PK)**, Category_Name                                                                 | Stores dish categories such as Starter, Main Course, Dessert, etc. |
| **Bill**        | **Bill_ID (PK)**, **Reservation_ID (FK)**, Bill_Date, Food_Total, Service_Charge, Total_Amount      | Stores billing information for each reservation.                   |


### Relationships and Constraints

| **Relationship** | **Entities Involved**  | **Description**                              |
| ---------------- | ---------------------- | -------------------------------------------- |
| **Makes**        | Customer ↔ Reservation | A customer makes one or more reservations.   |
| **Assigned_To**  | Reservation ↔ Waiter   | A waiter is assigned to serve a reservation. |
| **Places**       | Reservation ↔ Order    | A reservation can place one or more orders.  |
| **Contains**     | Order ↔ Order_Item     | An order contains multiple ordered dishes.   |
| **Belongs_To**   | Dish ↔ Order_Item      | Each order item refers to one dish.          |
| **Has**          | Category ↔ Dish        | A category contains multiple dishes.         |
| **Generates**    | Reservation ↔ Bill     | Each reservation generates one bill.         |


### Assumptions
Each customer has a unique Customer_ID.
A customer can make multiple reservations, but each reservation belongs to only one customer.
Reservations may be Reserved or Walk-in.
Each reservation is assigned to one waiter, while a waiter can handle multiple reservations.
A reservation can place one or more orders.
Each order contains one or more dishes through the Order_Item entity.
A dish belongs to only one category, but a category can contain many dishes.
Each reservation generates only one bill after all orders are completed.
The bill total is calculated as Food Total + Service Charge.
The Order_Item entity uses a composite primary key (Order_ID, Dish_ID) to uniquely identify each dish within an order.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
