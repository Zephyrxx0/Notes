
# Data Abstraction

Physical level- 
- Logical level-
- View level -

The overall design of the database is known as the database schema
- Physical-
- Logical- 

# Data Independence 
Capacity to change the schema at one level of a database system without having to change the schema at the next highest level

- Physical Data Independence -
- Logical Data Independence -

---

# Entity-Relationship(ER) Modeling

### Key Terms:

- An entity can be person, object, place, event or a concept in the user environment about which the organization wishes to maintain data
- Real World Object distinguishable from other objects
- Ex: a student, car, job etc.

## Entity type 

- Collection of Entities that share common properties or characteristics





# Constraints in ER Model

## Cardinality Constraints

![[CardinalityConstraint.excalidraw]]

## Participation Constraints
Defines how the entities set is participating in the relationship. This participation of entities set in a relationship might be total or partial.

---
# Attributes
Properties that distinguish one entity set from another one

## Key Attributes
Unique Identity 
Set of attributes that uniquely identify an entity in the entity set



| Cid  | Cname | Street | City   | MNo   | EmailID       |
| :--- | ----- | ------ | ------ | ----- | ------------- |
| c101 | A     | S      | Nagpur | xxxxx | test@mail.com |
| -    | -     | -      | -      | -     | -             |


- Super Key:- Set of attributes that can identify all attributes that can identify the entities in a row or a column in a table
- A set of all those attributes which can be used to uniquely Identify an entity in an entity set
	- ER MODEL 
		- Entity
		- Entity Set
`{Cid}, {Cid,Cname}, {EmailID}, {MNo}, {MNo, EmailID}`
*Composite key if it is a combination of 2 or more attributes*

- Candidate key : Super key's combination who's subset is not a super key itself
	- Those minimal super keys for which no proper subset is a super key
	- All candidate keys are Super Keys
`{Cid}, {EmailID}, {MNo}`

- Primary key: - The key attribute selected by the database designer to uniquely identify and entity in the entity set from the options available
`{Cid}`

- Foreign Key: 


# Strong vs Weak Entities and Identifying Relationships

## Strong Entities

- Exists independently of other types of entities
- has its own unique identifier
- Identifier underlined with single-line

### Weak Entities

- Dependent on strong entities(Identifying owner), cant exists on its own
- does not have a unique identifier(only a partial identifier)
- Partial identifier underlined with double line
- Entity box has double line

###  Identifying Relationships

Links Weak Entities to Strong Entities.

---

# Unit 5 
# Transaction Management

### Properties

- #### ACID Properties
	
	- Atomicity
		- Entire transaction takes place at once or doesn't happen at all.
	- Consistency 
		- Data is in a constant state when a transaction starts and after it ends.
	- Isolation
		- Immediate state of transaction is invisible to other transaction. As a result, transactions that run concurrently appear to be serialized
	- Durability
		- The changes of a successful transaction occurs even if the system failures occurs
		- Changes to data persist and are not undone.

### Concurrency Control

- Deals with preventing concurrently running processes form improperly inserting, deleting or updating the same data

- Ensures that correct results for concurrent operations are generated, while getting those results as quickly as possible.

- In DBMS, Ensures that database transactions are performed concurrently without violating the database properties 

####  Uncommitted Dependency Problems
 
#### Inconsistent Analysis Problem
- Occurs when transaction reads several  

### Serializability

- Objective of a concurrency control protocol [...]

