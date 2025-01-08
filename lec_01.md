![image](https://github.com/user-attachments/assets/a6d09289-4b09-40a7-b197-3623afb798db)# Lecture 1 - Introduction

## Overview of Database Management Systems

### What is a database?

* A very large collection of **related** data
  * Data is raw facts on some aspect of the world
* Models a real-world enterprise (e.g. University)
  * Entities (students, courses)
  * Relationships (Bob took CS 1555) 
![image](https://github.com/user-attachments/assets/d2641f3d-e9be-4a96-b1f5-ea18dabfadc2)

### Database Goal / Data Modeling

* What is the full, real world problem?
* Which components are we focused on/need to store?
  * Which objects will we need to store?
    * What characteristics define / distinguish these objects
  * Are there interactions between these objects
* **Goal: How can we model this mini-world in a Database System (DBS)?**

### Integrated Data

* All data are stored and manipulated in a uniform way on a secondary storage
  * Databases stores large amounts of data that cannot fit in main memory
  * Data are stored for a long and indefinite period
  * Data are shared across multiple applications
 
### What is a Database Management System?

* **Database Management System (DBMS)**
  * A general-purpose software package designed to store and manage databases conviniently & efficiently
* **DBMSs**
  * Oracle, IBM, DB2, SQLServer, MySQL, PostgreSQL
* **Usage**
  * Databse system = DB + DBMS + Application Logic
  * Resource Planning Applications
    * PeopleSoft, SAP
  * Web-based Applications
    * amazon.com, ebay, google

### Approaches to management of data

* File system approach
* Database Approach

#### File System Approach

* Write everything to text files
  * Have your applications directly read/write to these files
* Problems
  * Slow
  * Have to constantly enforce layout of data
  * What if multiple instances of your application need to read/write to the file at the same time?
 
### Database vs. File System Approach

* Abstraction
  * Data
  * Execution 
* Reliability
* Efficiency/Performance

### Data Abstraction

* Data are structured in a way meaningful to applications
* **Data Model**
  * A collection of high level data description constructs that hide low-level storage details
  * E.g., Relational, Object-oriented, XML, Graph
* **Relational/Object-Relational Model**
  * Is the most widely used data model today
  * Main construct is a relation: table of records
  * Every relation has a schema
    * Relation name, Names of fields, Types of fields
  ![image](https://github.com/user-attachments/assets/2683b6ae-b681-4efa-a96e-7f9d905d6202)
  * Schema:
    * Students (sid: string, name: string, age: integer, gpa: real)
  * State: Actual data at a given point in time  

### Levels of Data Abstraction in a DBMS

* The data in a DBMS is described at three levels of abstraction
  * Conceptual Schema
    * DDL: Data Definition Language
  * Physical Schema
    * SDL: Storage Definition Language
  * External Schema (views)
    * VDL: View Definition Language
  * Mant external schemas
  * Plus, one conceptual
  * plus, one physical
 
![image](https://github.com/user-attachments/assets/4e7d9c62-9c1c-4348-b54e-12bbd4a78df0)
         
#### External Schema - Views

* Allows data ccess to be customized and authorized at the user-level
  * Defined in terms of data model
  * Consists of a collection of views
  * Example:
    * CourseEnroll(cid: string, enrollment: integer)
* Guided by end-user requirements
* Views are computed as needed
* Multiple views of data allow each user/application to get different perpectives of the database

### 3-Level Architecture

* View Level
  * CSMajors
  * MathMajors
* Logical Level: entire database schema
  * Courses (CourseNo, CourseName, Credits, Dept)
  * Students (StudentID, Lname, Name, Class, Major)
  * GradeReport (StudentID, CourseNo, Grade, Term)
* Physical Level
  * How these tables are stored
  * How many bytes and attributes, ect.
 
### Execution ABstraction

* A transaction is a logical unit of work in DBMSs
  * It is thte execution of a program segment that performs some function or task by accessing shared data
  * Logical grouping of query and update requests needed to perofrm a task 
