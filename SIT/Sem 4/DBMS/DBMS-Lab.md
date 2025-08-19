#Question: Find the details of such customers whose name starts with an 'A'

`Like` predicate is used to do the pattern matching in SQL on a particular Column

```Sql
SELECT col1, col2, col3 from t_name where col_name like 'a%';
```

`'%<varchar>'`: checks the last character of a string
`'<varchar>%'`: checks the first character of a string

*does NOT work for `char`, only for `varchar`*

---

#Question: Find the details of such customers whose name has exactly 4 characters
```Sql
SELECT col1, col2, col3 from t_name where col_name like '____'; 
```
*four underscores will match a string of 4 length

---


#Question Find the name of such customers whose name's 3rd char is 'h'

```Sql
SELECT col1, col2, col3 from t_name where col_name like '__h%'; 
```

---

Truncate : `where` clause not usable, all columns and rows are deleted , but the structure of table remains
```sql
TRUNCATE table t_name;
```

Drop: Deletes everything along with the structure
```sql
DROP table table_name;
```


Delete : delete a particular row , usable with `where` clause
```sql
DELETE from t_name where col_name = '   ';
```


Dual: A dummy table of 1 * 1 dimension

```sql
SELECT sysdate from dual;
```

# Alter and Update

```SQL
alter table Customer modify(street varchar2(20));
```
Modifies Existing variable storage
%%Comes under DDL - Data Definition Language%%
 
#Question Create a table `EMPLOYEE` with attributes `Emp_ID(Primary key)`, `E_Name`, `Department_Name`, `Salary`, `MNo`, `Dependents_Count`
Make use of alter table Query to add a new column in the table: Date of joining of the employee, modify the datatype of one column, delete the column `dependents_count` from the table. After Creation of the structure, insert 10 records in the table.

```syntax
alter table <table_name> column <col_name>`
```

```SQL
alter table Employee modify(EMP_NAME varchar2(25)); ' modify datatype size '
alter table Employee drop column dep_count; 'delete a column'
alter table Employee add(dateJoined date); 'add a column'
alter table Employee rename Column DATEJOINED TO DoJ; 'rename a column name'
```


```sql
update Employee set city = 'Ngp'; 'updates city column for value ngp for all entry'
update Employee set city = 'Goa' where emp_id = 'c101'; 'updates for select record'
```

Update the salary of all employees who are working in technical department as 90,000 

---

#Question Find:
	- Sum of all prices
	- Least price
	- Highest price
	- Average price
	- Sum of price in each category

```SQL
Select sum(price) from Products;   'sum of column'
Select avg(price) as "Average Price" from Products;  'avg of column'
Select min(price) as "MIN Price" from Products;  'min of column'
Select max(price) as "MAX Price" from Products;  'max of column'
Select Count(price) as "Count" from Products;    'number of entities in a row'
Select Count(category) as "Count" from Products;    
/*Select distinct Count(category) as "Count" from Products;*/
Select Count(distinct category) as "Count" from Products; 'unique entities in a col'
```

```SQL
Select sum(Price) as "Sum of Stationary" from Products where category = 'Stationary'; --Sum of a specific category
Select sum(Price) as "Sum of Categories" from Products group by category; 'Displays sum of all categories seperately'
```

#Question Find the average of prices of products from the category "Groceries" in the `Products`

```sql
Select avg(Price) as "Average of Groceries" from Products where category = 'Groceries';
```

#Question Find the summation of prices whose prices is greater than 100rs.

```SQL
 Select Sum(Price) as "Sum" from Products where price > 100 group by category;
```

#Question Find the count of the product IDs whose price is greater than 60

```sql
Select Count(category) as "Count" from Products;
/* OR */
Select Count(category) as "Count" from Products where price > 60 group by category;
'seperate the count by category'
```

> [!NOTE]
> `Where` vs `Having`
> `Having` is applied on chunk of rows, `where` clause is only applied on a single row

---

#Question Create a table `Employee` with attributes `emp_name`, `emp_id`, `dept_name`, `date_of_joining` and  `salary`.


```SQL
select upper(Emp_name) from employee; 'uppercases all string in column'
select lower(Emp_name) from employee; 'lowercases all string in column'
 
select trim('e' from 'eeee189e6ee') from dual; 'trims from both sides'
select ltrim('aaaa189e69287e01', 'a') from dual; 'trims 'a' from left side'
select rtrim('aaaa189e6ee', 'e') from dual;      'trims 'e' from right side'
select rtrim('aaaa189e69287e01eef', 'e') from dual;  'doesnt trim anything cuz e isnt there in right side'

select Length('Shreya') from dual; 'returns the length of string'
select INSTR('Shreya', 'y') from dual;  'first instance of letter in string'

select months_between('2-JUL-2004' , '23-DEC-2004') as "Age difference" from dual; 'Bigger month in 1st parameter for positve answer'
```

---
## Math Functions

```SQL
SELECT ABS(-46) AS AbsoluteValue from dual;  'returns absolute value of a number'
SELECT CEIL(4.4) AS CeilValue from dual;
SELECT FLOOR(4.5) AS FloorValue from dual;
SELECT ROUND(87.5) AS RoundValue from dual;
SELECT DECIMAL(5,2) AS DecimalValue from dual; 'number with 5 lenght with 2 decimal places'
SELECT POWER(4, 2) AS CeilValue from dual;
SELECT MOD(53,17) AS Mod FROM DUAL;
SELECT EXP(3) FROM dual;         'e^3'
SELECT SQRT(121) AS "square root" FROM dual; 'return square root'

```

---
## Date Functions

```SQL
SELECT SYSDATE FROM DUAL; 
SELECT ADD_MONTHS(SYSDATE,5) AS NewDate FROM dual;
SELECT MONTHS_BETWEEN(SYSDATE, TO_DATE('2024-12-1','YYYY-MM-DD')) AS monthDifference FROM DUAL; 'Difference Between months'
SELECT TRUNC(SYSDATE, 'MM') AS FirstOfMonth FROM DUAL; 
SELECT SYSDATE + 5 AS NewDate FROM DUAL; 'adds 5 days to the date'
SELECT TO_DATE('2025-06-2','YYYY-MM-DD') AS ConvertedDate FROM dual; 'converted date'
SELECT TO_CHAR(SYSDATE,'YYYY-MM-DD HH24:MI:SS') AS DateFormated FROM dual; 'formatted date'
SELECT EXTRACT(YEAR FROM SYSDATE) AS CurrentYear FROM DUAL; 'extracts the part of the date'
SELECT Next_day(SYSDATE,'Monday') AS NextDay FROM DUAL; 'returns the date of the upcoming day'
SELECT Last_day(SYSDATE) AS LastMonthDay FROM DUAL; 'returns the last date of the month'
SELECT Current_Date AS CurrentDate FROM DUAL;
SELECT Current_TimeStamp AS CurrentDate FROM DUAL;

```

----
Write a procedure which will take 2 numbers as parameters and perform addition of these two numbers and print the result.

```SQL
CREATE PROCEDURE add_numbers(a IN NUMBER,b IN NUMBER) IS

BEGIN
    DBMS_OUTPUT.PUT_LINE(a+b);
END add_numbers;

/
```

---
## Experiment 5
University Database Management Systems creates, manages and performs all the activities related to the database of the given university. The database consists of information about the various departments of university, students, faculties, various courses, instructors. student's sections and various time slots and the class rooms available in the university. the main aim of this project is to manage the database in such a way that any academic information can be retrieved easily, efficiently and accurately.
Draw an ER diagram with all the possible following constraints and Enhanced Entity Relationship diagram. Also draw schema diagram:
- A university has many departments
- Each department has multiple instructors(one is HOD). HOD = Head of Department
- An instructor belongs to only one department.
- Each department offers multiple courses, each subject is taught by a single instructor.
- A student may enroll for many courses offered  by different departments.


---
<!--18-02-2025-->
#Question Draw the detailed ER diagram for: 
- Banking Database
- Hospital Management system
- Online bookstore Management system
- A company database handling vehicle accident insurance
- Database Handling the operations of a cricket league



---
# Experiment 6

Aim:  To study PL/SQL Procedure and write procedures for:
- Swapping of two numbers without using third variable
- Largest amongst three number
- Area of circle by radius as an argument.

---
#Question Write a PL/SQL block to create a procedure to calculate total marks of the student and percentage of the student.

#Question Write a PL/SQL block to create a procedure to calculate area of circle, triangle and rectangle

#Question Write a PL/SQL block to create a procedure to sum of first 10 numbers using while loop.

#Question Write a PL/SQL block to create a procedure to sum of first 10 odd numbers using FOR loop.

#Question Consider an examination system. It will accept the marks of 4 subjects,. Write procedure which will find the total and average of 4 subjects and display the grade

### Experiment  7 

[SQL](SQL\exceptionHandling.sql)


### Experiment 9_a:

**Aim** Use airline reservation system. Design a database containing tables/fields as route_id. origin, destination, fare, distance, capacity
Write a procedure to satisfy the following conditions accepting the route as the user_input.
- If the distance is less than 500 then update the fare to be 190.98
- If the distance is between 501-1000 then update fare to 876
- IF distance is greater than 1000 then display a message.

### Experiment 9_b:
**Aim** Use airline reservation database system designed in Practical 9. Write a trigger
- Which will compel the insertion of values or origin and destination fields 