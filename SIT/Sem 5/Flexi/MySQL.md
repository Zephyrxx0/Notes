`mysql2.createConnection()`: Connect to the SQL server

# INTRODUTION

SQL is a standard language for accessing and manipulating databases

SQL stands for Structured Query Language.

SQL lets you access and manipulate databases.

`CRUD` operations

SQL can set permissions on tables, procedures, and views

## Functions

## `Alter`

The ALTER TABLE statement is used to: 
- add, delete, or modify columns in an existing table.
- add or drop constraints of a column

```mysql
ALTER TABLE table_name ADD column_name datatype; #add a column in a table

ALTER TABLE table_name DROP COLUMN column_name; #delete a column in a table

ALTER TABLE table_name MODIFY COLUMN column_name datatype; #change the data type of a column
```

## `Logical Operators`

he `WHERE` clause can be combined with `AND`, `OR`, and `NOT` operators.

The AND and OR operators are used to filter records based on more than one condition:

- The `AND` operator displays a record if all the conditions separated by `AND` are TRUE.

- The `OR` operator displays a record if any of the conditions separated by `OR` is TRUE.

- The `NOT` operator displays a record if the condition(s) is NOT TRUE.

> [!Example] Examples
> 
> > [!example] `AND`
> > ```sql
> > SELECT * FROM Customers WHERE Country='Germany' AND City='Berlin'; 
> > ```
> > 
> 
> > [!example] `OR`
> > ```sql
> > SELECT * FROM Customers WHERE City='Berlin' OR City='München'; 
> > ```
> > 
> 
> > [!example] `NOT`
> > 
> > ```sql
> > SELECT * FROM Customers WHERE NOT Country='Germany'; 
> > ```
> >
> > [!example] Combined
> >```sql
> >SELECT * FROM Customers
> >WHERE Country='Germany' AND (City='Berlin' OR City='München'); #selects all fields from "Customers" where country is NOT "Germany" and NOT "USA":
> >```

## `AUTO_INCREMENT`

By default, the starting value for AUTO_INCREMENT is 1


```mysql
CREATE TABLE Persons (
    Personid int NOT NULL AUTO_INCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (Personid)
);

ALTER TABLE Persons AUTO_INCREMENT=100;
#To insert a new record into the "Persons" table, we will NOT have to specify a value for the "Personid" column (a unique value will be added automatically):
```

## `Between`

The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.
The BETWEEN operator is inclusive: begin and end values are included.

```mysql
SELECT column_name(s)
FROM table_name    
WHERE column_name BETWEEN value1 AND value2;
```

## Constraints

SQL constraints are used to specify rules for the data in a table.

Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted.

Constraints can be column level or table level. Column level constraints apply to a column, and table level constraints apply to the whole table.

The following constraints are commonly used in SQL:

- `NOT NULL `- Ensures that a column cannot have a NULL value.

- `UNIQUE` - Ensures that all values in a column are different.

- `PRIMARY KEY` - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table

- `FOREIGN KEY` - Uniquely identifies a row/record in another table.

- `DEFAULT` - Sets a default value for a column when no value is specified.

- `INDEX` - Used to create and retrieve data from the database very quickly.

- `Auto_Increment` - Auto-increment allows a unique number to be generated automatically when a new record is inserted into a table.

## `Count()`

Returns the number of rows that matches a specified criteria.

```mysql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

## `AVG()`

Returns the average value of a numeric column.

```mysql
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```

## `SUM()`

The SUM() function returns the total sum of a numeric column.

```mysql
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```

## `CREATE DATABASE`

CREATE DATABASE statement is used to create a new SQL database

```mysql
CREATE DATABASE databasename;
```

## `CREATE TABLE`

The CREATE TABLE statement is used to create a new table in a database.

Syntax:
  
```mysql
CREATE TABLE table_name (                                                              
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```

The column parameters specify the names and datatypes `(e.g. varchar, integer, date, etc.)` of the columns of the table.

## `DELETE`

The `DELETE` statement is used to delete existing records in a table.

```mysql
DELETE FROM table_name WHERE condition;
```

It is possible to delete all rows in a table without deleting the table. This means that the table structure, attributes, and indexes will be intact:

```mysql
DELETE FROM table_name;
```

## `DROP` and `TRUNCATE`

The DROP TABLE statement is used to drop an existing table in a database.

```mysql
DROP TABLE table_name;
```

The TRUNCATE TABLE statement is used to delete the data inside a table, but not the table itself.
```mysql
TRUNCATE TABLE table_name;
```

## `FOREIGN`
A FOREIGN KEY is a key used to link two tables together.

A FOREIGN KEY is a field (or collection of fields) in one table that refers to the PRIMARY KEY in another table.

The table containing the foreign key is called the child table, and the table containing the candidate key is called the referenced or parent table.

Notice that the "PersonID" column in the "Orders" table points to the "PersonID" column in the "Persons" table.

The "PersonID" column in the "Persons" table is the PRIMARY KEY in the "Persons" table.

The "PersonID" column in the "Orders" table is a FOREIGN KEY in the "Orders" table.

The FOREIGN KEY constraint is used to prevent actions that would destroy links between tables.

The FOREIGN KEY constraint also prevents invalid data from being inserted into the foreign key column, because it has to be one of the values contained in the table it points to.

```mysql
CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    Foreign KEY (OrderID) REFERENCES table2 (key),
  
);
```


