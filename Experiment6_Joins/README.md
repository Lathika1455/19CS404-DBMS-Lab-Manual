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
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.


```sql
SELECT 
    customer.cust_name, 
    customer.city, 
    orders.ord_no, 
    orders.ord_date, 
    orders.purch_amt AS "Order Amount"
FROM 
    customer
LEFT JOIN 
    orders ON customer.customer_id = orders.customer_id
ORDER BY 
    orders.ord_date ASC;
```

**Output:**
<img width="1288" height="956" alt="image" src="https://github.com/user-attachments/assets/02dd383a-cee9-41a8-bb56-5bedd7e46f6a" />

**Question 2**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "salesman_name") and the "cust_name" column from the "customer" table (aliased as "customer_name"), with a left join on the "salesman_id" column.


```sql
SELECT s.name AS salesman_name, c.cust_name AS customer_name
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id;
```

**Output:**

<img width="702" height="880" alt="image" src="https://github.com/user-attachments/assets/3e4c3bad-2c3d-4f57-9c9b-d7acce6b9764" />


**Question 3**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.


```sql
select c.cust_name as 'Customer Name' , c.city, s.name  as Salesman, s.commission
from customer c
join salesman s on c.salesman_id=s.salesman_id;
```

**Output:**

<img width="1227" height="872" alt="image" src="https://github.com/user-attachments/assets/d017c145-e4fa-441c-8f9e-5452f875f36d" />


**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.


```sql
SELECT 
    p.first_name AS patient_name, 
    t.result_id,
    t.patient_id,
    t.test_name,
    t.result,
    t.test_date
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id
WHERE
    t.test_name = 'Blood Pressure';
```

**Output:**

<img width="1242" height="452" alt="image" src="https://github.com/user-attachments/assets/e75c593a-4d94-4592-a96c-132b48a4709a" />


**Question 5**
---
Write the SQL query that accomplishes the selection of the first name and last name from the "patients" table, with an inner join on the "patient_id" column and a condition filtering for surgeries with a surgery date between '2024-01-01' and '2024-01-31'.


```sql
select p.first_name, p.last_name
from patients p
join surgeries s on p.patient_id=s.patient_id
where s.surgery_date between '2024-01-01' and '2024-01-31';
```

**Output:**

<img width="787" height="415" alt="image" src="https://github.com/user-attachments/assets/90b75dd2-85ae-4c36-882b-2d0d324b83aa" />


**Question 6**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'New York'.


```sql
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c ON s.salesman_id = c.salesman_id
WHERE 
    c.city = 'New York';
```

**Output:**

<img width="425" height="405" alt="image" src="https://github.com/user-attachments/assets/1c9b144a-5c63-49d5-99fe-7ad0fff59f91" />


**Question 7**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.


```sql
select p.first_name as patient_name, t.result_id, p.patient_id, t.test_name, t.result, t.test_date
from patients p
inner join test_results t on p.patient_id=t.patient_id
where p.admission_date  between '2024-01-01' and '2024-01-31';
```

**Output:**

<img width="1233" height="435" alt="image" src="https://github.com/user-attachments/assets/5a7e26bb-4c44-4b7a-99dc-dc0562396412" />


**Question 8**
---
Write the SQL query that achieves the selection of the "nurse_id" from the "nurses" table (aliased as "n") and the "department_name" from the "departments" table, with an inner join on the "department_id" column and conditions filtering for a nurse with the first name 'David' and last name 'Moore'.


```sql
SELECT n.nurse_id, d.department_name
FROM nurses AS n
INNER JOIN departments AS d ON n.department_id = d.department_id
WHERE n.first_name = 'David' AND n.last_name = 'Moore';
```

**Output:**

<img width="720" height="423" alt="image" src="https://github.com/user-attachments/assets/f9f6a0fa-ef96-4dd5-8bf4-55ac36013ed1" />


**Question 9**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date between '2012-07-01' and '2012-07-30'.


```sql
SELECT 
    c.*
FROM 
    customer AS c
LEFT JOIN 
    orders AS o ON c.customer_id = o.customer_id
WHERE 
    o.ord_date BETWEEN '2012-07-01' AND '2012-07-30';
```

**Output:**
<img width="1245" height="436" alt="image" src="https://github.com/user-attachments/assets/0c6289d2-ac9e-410e-9ca9-9fe76ccddfe5" />


**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.


```sql
select p.patient_id, p.first_name, p.last_name, p.date_of_birth, p.admission_date, p.discharge_date, d.doctor_id, d.specialization as doctor_specialization
from patients p 
inner join doctors d on p.doctor_id=d.doctor_id;
```

**Output:**

<img width="1252" height="572" alt="image" src="https://github.com/user-attachments/assets/cfa7c232-d9a9-4dd1-b2d2-487756aec1a5" />





## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
