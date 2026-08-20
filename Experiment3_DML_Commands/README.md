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
Write a SQL query to Select all patients who were admitted for one day.

Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT

```sql
select patient_id,first_name,admission_date,discharge_date
from patients
where admission_date=discharge_date;
```

**Output:**

<img width="1196" height="377" alt="image" src="https://github.com/user-attachments/assets/b03c9e9d-8f9c-4a2d-9483-06e2d28b267d" />

**Question 2**
---
For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE Products
SET sell_price = CAST(cost_price * 1.35 AS INTEGER)
WHERE ((sell_price - cost_price) / sell_price) < 0.30;
```

**Output:**

<img width="1205" height="571" alt="image" src="https://github.com/user-attachments/assets/0dd8b686-37bc-42de-8a6f-9247e96ca2d2" />

**Question 3**
---
Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
delete from doctors
where doctor_id between 2 and 4;
```

**Output:**

<img width="1205" height="924" alt="image" src="https://github.com/user-attachments/assets/4b299051-5548-4fd8-a545-4cc8583d8ee8" />


**Question 4**
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization

```sql
delete from doctors
where specialization = 'Pediatrics' and first_name like 'Michael';
```

**Output:**

<img width="1218" height="462" alt="image" src="https://github.com/user-attachments/assets/a61dfb82-60ab-40df-b4f3-24408489b698" />

**Question 5**
---
Show the categoryName and description from the categories table sorted by categoryName.

name                     type
---------------       ---------------
CategoryID           INTEGER
CategoryName     VARCHAR(25)
Description          VARCHAR(255)

```sql
SELECT CategoryName, description
FROM categories
ORDER BY categoryName;
```

**Output:**

<img width="1203" height="598" alt="image" src="https://github.com/user-attachments/assets/66eacd3f-e696-4bb0-89c4-c06a46cbf993" />

**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

Sample table: Customer

```sql
DELETE FROM Customer
WHERE CUST_NAME LIKE '%Holmes%';
```

**Output:**

<img width="1211" height="603" alt="image" src="https://github.com/user-attachments/assets/683a1526-842e-4eb5-b59a-5c86a6a24f49" />

**Question 7**
---
Write a SQL statement to show all the contact_name, address, city of all customers who are from 'Germany', 'Mexico' and 'Spain' countries.

customers table

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           CustomerID    INTEGER      0                       1
1           CustomerName  VARCHAR(50)  0                       0
2           ContactName   VARCHAR(50)  0                       0
3           Address       VARCHAR(50)  0                       0
4           City          VARCHAR(20)  0                       0
5           PostalCode    VARCHAR(10)  0                       0
6           Country       VARCHAR(15)  0                       0

```sql
SELECT ContactName, Address, City
FROM customers
WHERE Country IN ('Germany','Mexico','Spain');
```

**Output:**

<img width="924" height="901" alt="image" src="https://github.com/user-attachments/assets/0313ac75-8dec-4fd1-8b14-08133b4c891f" />


**Question 8**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

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
update products
set sell_price=sell_price*1.1
where category='Bakery';
```

**Output:**

<img width="1209" height="578" alt="image" src="https://github.com/user-attachments/assets/58247348-984f-45ca-af89-0cbdd9744f6a" />


**Question 9**
---
Write a SQL query to categorize value1 in the Calculations table as 'High' if it is greater than 50, otherwise 'Low'.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```sql
select id,value1,
   case
   when value1 > 50 then 'High'
   else 'Low'
   end as value_category
from calculations;
```

**Output:**

<img width="894" height="358" alt="image" src="https://github.com/user-attachments/assets/2c143dc5-f832-4133-9d9c-5adafff738f8" />

**Question 10**
---
Write a SQL query to calculate the discounted price for products where the discount percentage is greater than 0, and order the results by discounted_price in ascending order. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage 

------------+----------------+--------------------- 

101 | 50.00 | 0.10 

102 | 75.00 | 0.00 

103 | 100.00 | 0.20

```sql
SELECT product_id,
       original_price,
       discount_percentage,
       original_price * (1 - discount_percentage) AS discounted_price
FROM Products
WHERE discount_percentage > 0
ORDER BY discounted_price ASC;
```

**Output:**

<img width="1213" height="356" alt="image" src="https://github.com/user-attachments/assets/be181616-cc58-4421-8e0e-86ef182acc41" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
