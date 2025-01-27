# Lecture 4

## Relational Model

* The most popular implementation model
* Both entity types and relationship types are represented by relations, i.e., tables

### THe Mathematical Concept of Relation

* Let D1, D2,...,Dn be domans. The cartesian product of these n sets (D1 x D2 x ... x Dn) is the set of all possible ordered-n tuples
* D1 = {A, B} D2 = {1, 2, 3}
* D1 x D2 = {(A, 1), (A, 2), (B, 1), (B, 2), (C, 1), (C, 2)}

## SQL Insert

* Implicit (list):
  * ```SQL
    INSERT INTO STUDENT
    VALUES (165, 'SUSAN JONES', 'CS', 0.00);
    ```

* Explicit (set):
  * ```SQL
    INSERT INTO STUDENT (SID, Name)
    VALUES (165, 'Susan Jones');

### Properties of Relations

* A relation is finite
* There are no duplicate tuples in a relation
  * Recall that a relation is a set of tuples
* Order of tuples in a relation is not important
  * Many logical orders can be specified on a relation
* A value may appear multiple times in a column

* Order of attribute values in a tuple is
  * Important in a list of attributes definition
  * Not important in a set of attributes definition
 
## Relation Schema

![image](https://github.com/user-attachments/assets/08377bf8-54d3-4d4d-b774-0553af580bb1)

* A relation schema R specifies:
  * The name of the relation
  * The attribute names A, of R
  * The domain D1 (data type & format) for each attribute A1
  * Uniqueness property
* Data type is a set of atomic data values
  * No attribute is set-valued (1st Normal Form, 1NF)
  * No attribute is composite
 
### Example Table Schema  

* Schema of STUDENT(SID, Name, Major, GPA)
  * ```SQL
    CREATE TABLE STUDENT (
      SID INTEGER,
      Name CHAR(20),
      Major CHAR(4),
      GPA DEC(3, 2), -- 3 numbers, 2 after the decimal (3.44, 2.98, etc.)
      CONSTRAINT STUDENT_PK PRIMARY KEY (SID)
    );
    ```

### Domain Constraints

* Domain (type) of each field is specified and enforced by the DBMS whenever tuples are added or modified
* Example of IC Violation
* ```SQL
  UPDATE STUDENTS
  SET Age = 'Eighteen'
  WHERE Name = Jones; -- ERROR: The domain of Age is integer but it is set to the string. Same is true for Name 
     
### Loading / Populating a Database

![image](https://github.com/user-attachments/assets/6170b6f4-f2d3-4593-bb2f-c62463e1df50)


* When a schema is created, the database is at an empty state!
* Initial state when the database is populated (loaded) after creation

## Useful Terms

* Cardinality of a relation r(R): Number of tuples in r(R) (denoted by |r(R)|)
* Arity or Degree of a relation r(R): Number of attributes in R (denoted by |R|)
  * ![image](https://github.com/user-attachments/assets/8e7b48f5-4e84-43dd-941a-48d0913e17e7)
  * Arity, |R| = 4
  * Cardinality, |r(R)| = 3
* |R| > 0 and |r(R)| >= 0
* Cardinality is a property of a relation
* Arity is a property of a relation schema or a relation

## Basic SQL Select Statement

* Retrieving / Querying the state of a database
  ```SQL
  SELECT [DISTINCT | ALL] attribute-list
  FROM table-list
  [WHERE selection-condition]
  ```
• Example:
  ```SQL
  SELECT SID, Name, Age, GPA
  FROM Students
  WHERE Name = Pat;
  Basic SQL Select Statement
  ```
### Relational Datbase Schema

* A database schema is a set of relation shcemas and a set of integrity constraints
  * Integrity constraints
    * Structural integrity Constraints
      * Key constraints: Uniqueness of keys
      * Entity integrity constraints: No primary key value can be NULL
      * Refernetial Integrity constraint
    * Semantic integrity constraints

### Integrity Constraints (ICs)

* IC: Condition that must be true for any instance of the database
  * E.G., domain constraints
* A lgal instance of a relation is one that satisfies all specified ICs
* ICs are specified when the schema is defined
* ICs are enforced when tables are modified

#### Primary Key Constraint

* A set of fields is a key for a relation if:
  * No two distinct tuples can have the same values in all key fields
* If there is more than one key for a relation
  * Each key is called a candidate key
  * Once candidate key is designated as the **primary key**   
