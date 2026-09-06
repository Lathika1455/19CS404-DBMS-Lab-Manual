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
Write a SQL query to calculate the total number of working hours of all employees

```sql
select sum(workhour) as 'Total working hours'
from employee1;
```

**Output:**

<img width="802" height="398" alt="image" src="https://github.com/user-attachments/assets/93ab9df9-a790-4cf3-bc23-2b914baa4ae9" />


**Question 2**
---
Write a SQL query to find the maximum purchase amount.

```sql
select max(purch_amt) as MAXIMUM
from orders;
```

**Output:**

<img width="470" height="375" alt="image" src="https://github.com/user-attachments/assets/38f27bc3-0662-4545-b4b9-0bd59762aabd" />


**Question 3**
---
Write a SQL query to find the minimum purchase amount.


```sql
SELECT 
    MIN(purch_amt) AS MINIMUM
FROM 
    orders;
```

**Output:**

<img width="446" height="380" alt="image" src="https://github.com/user-attachments/assets/c3fa4d68-f4f1-4e72-9ccd-9cbcbd6d2c2b" />

**Question 4**
---
How many patients are covered by each insurance company?

```sql
select InsuranceCompany,count(*) as TotalPatients
from Insurance
group by InsuranceCompany;
```

**Output:**

<img width="847" height="757" alt="image" src="https://github.com/user-attachments/assets/3c88a6df-0f31-42fb-bffa-19a751698f42" />


**Question 5**
---
What is the count of male and female patients?

```sql
select gender,count(*) as TotalPatients
from patients
group by gender;
```

**Output:**

<img width="752" height="427" alt="image" src="https://github.com/user-attachments/assets/a4cd837f-fa6b-4ecb-af0f-3444dd2637ac" />

**Question 6**
---
How many patients have insurance coverage valid in each year?


```sql
select strftime('%Y',Validityperiod) as ValidityYear,count(*) as TotalPatients
from insurance
group by ValidityYear
```

**Output:**

<img width="773" height="452" alt="image" src="https://github.com/user-attachments/assets/e65f313b-2c35-4abe-93d4-cd67d6755458" />

**Question 7**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.

```sql
SELECT 
  age,
  SUM(income) AS "SUM(income)"
FROM employee
GROUP BY age
HAVING SUM(income) > 1000000;
```

**Output:**

<img width="728" height="471" alt="image" src="https://github.com/user-attachments/assets/a36b01dc-bddb-437f-acf8-505f8784e4e9" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

```sql
select age,min(income) as Income
from employee
group by age
having min(income) < 1000000;
```

**Output:**

<img width="707" height="501" alt="image" src="https://github.com/user-attachments/assets/1b555d55-3518-44ed-8d32-313fac1e7580" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by age groups, displays the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

```sql
SELECT (age/5) * 5 AS age_group, MIN(salary)
FROM customer1
GROUP BY age_group
HAVING MIN(salary) < 2000
ORDER BY age_group;
```

**Output:**

<img width="703" height="408" alt="image" src="https://github.com/user-attachments/assets/e9c46b24-dc8c-48d5-99bc-65a13d260538" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

```sql
select occupation,min(workhour) as 'MIN(workhour)'
from employee1
group by occupation
having min(workhour) > 8;
```

**Output:**

<img width="857" height="552" alt="image" src="https://github.com/user-attachments/assets/4acbb7d0-a22f-4841-a7b6-2eb47fe68c35" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
