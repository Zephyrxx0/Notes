
Is a procedural Query Language used for querying and manipulating relational databases. It provides a foundation for SQL and is essential for understanding how relational database management systems (RDBMS) process queries.

### Key Concepts

- **Relation:** A table in relational Database (sets of tuples)
- **Tuple:** A single row in a table
- **Attribute:** A single column in a table
- **Domain:** A set of allowable values for an attribute

Relational Algebra consists of a set of operations that work on relations to 

```SQL
Select * FROM TABLE a,TABLE b WHERE a.col = b.col;
```

---


## Difference Between SQL Queries and Relational Algebra

SQL (Structured Query Language) and Relational Algebra are both used for querying relational databases, but they differ in purpose and representation.

Examples

1. Selection (σ) - Filtering Rows

```SQL
SELECT * FROM Students WHERE age > 18;
```

```RelationalAlgebra
σ age > 18 (Students)
```

2. Projection (π) - Selecting Columns
```SQL
SELECT name, age FROM Students;
```

```
π name, age (Students)
```

3. Join (⨝) - Combining Tables

```SQL
SELECT Students.name, Courses.course_name 
FROM Students 
JOIN Enrollments ON Students.id = Enrollments.student_id 
JOIN Courses ON Enrollments.course_id = Courses.id;
```


```
π Students.name, Courses.course_name (Students ⨝ Enrollments ⨝ Courses)
```

4. Union (∪) - Combines Tuples From two relations

```SQL
R1 ∪ R2  -- R1 and R2 must have same schema
```

5. Set Difference (-) - Returns Tuples in 1 relation but not in another
```SQL
R1 - R2 --stuff in R1 but not in R2 --R1 , R2 have same schema
```

6. Rename (ρ) - Rename a Relation
```SQL
ρ <og_name> (newName)
```

Sample Questions to Solve

#Question 1. Basic Selection & Projection

Given a Customers table with attributes (id, name, city, age), write:
an SQL query to get names of customers from "New York".
the equivalent relational algebra expression.

***Solution**
```SQL
SELECT name FROM CUSTOMERS WHERE city = 'New York';
```

```
π(σ city = 'New York'(Customers))
```

2. Join & Filtering

#Question Consider two tables:
Employees(eid, name, dept_id, salary)
Departments(dept_id, dept_name)

Write an SQL query to get names of employees working in the "HR" department.
```SQL
SELECT name FROM Employees e, Departments d WHERE e.dept_id = d.dept_id AND dept_name = 'HR'; 
```

Write the equivalent relational algebra.
```
π names(σ dept_name = 'HR'(Employees ⨝ Departments ))
```




3. Aggregate Functions

For a Sales table with (sale_id, product_id, amount), write an SQL query to find the total sales amount.

4. **Retrieve Employee and Department Names**

- Given the tables:
- `Employees(eid, name, dept_id, salary)`  
- `Departments(dept_id, dept_name, location)`   
- Write:

- An SQL query to get employee names along with their department names.
- The corresponding relational algebra expression using a **natural join**

***Solution
```SQL
SELECT e.name,d.dept_name FROM Employees,Departments WHERE e.dept_id = d.dept_id;
```

```
π name,dept_name(σ (Employee ⨝ Departments))
```

5. **Find Students Enrolled in Courses**
-  `Students(student_id, student_name, age)`
-  `Enrollments(student_id, course_id)`         
-  `Courses(course_id, course_name, instructor)`  
- Write:
- An SQL query to find student names along with the courses they are enrolled in.
 - The equivalent relational algebra.

***Solution 
```SQL
SELECT student_name, course_name FROM Students s, Enrollments e WHERE sdept  
```