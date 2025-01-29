# Lecture 5

### Create Table Schema - Example (addenendum)

```SQL
CREATE TABLE STUDENT (
  SID INTEGER NOT NULL, --Required by DB2 only
  -- ...
  CONSTRAINT STUDENT_UN UNIQUE (Login) --Unique can take NULL values
);
```

## Foreign Keys

* Foreign Key (FK) in relation to R2, is a set of attributes of R2 that forms a primary key (PK) of another relation R1
  * Attributes in FK and PK have the same domain

  ![image](https://github.com/user-attachments/assets/4d6cd20c-1b0f-451f-886a-1a2e903eb7e7)

### Foreign Key Constraints

* If foreign key constraints are enforced, **referential integrity** is achieved
  * E.g., only students can enroll in a class
* Like a "logical pointer 

### Any Attribute Can be a Foreign Key

* **Foreign Key**: set of fields in one relation that is used to "refer" to a tuple in another relation
  * Must correspond to primary key of the referred relation
  * If not part of a key, it could be NULL
 
### Foreign Keys in SQL

![image](https://github.com/user-attachments/assets/082525a3-2314-4106-9956-b984b1771d80)

```SQL
CREATE TABLE Enrolled (
  SID CHAR(20),
  CID CHAR(20),
  Grade CHAR(2),
  CONSTRAINT ENROLLED_PK PRIMARY KEY (SID, CID),
  CONSTRAINT STUDENT_FK_sid FOREIGN KEY (SID) REFERENCES STUDENT (SID)
  CONSTRAINT STUDENT_FK_cid FOREIGN KEY (CID) REFERENCES COURSE (CID)
    ON UPDATE CASCADE ON DELETE NO ACTION --see referential integrity
);
```

### Referential Integrity Enforcement

* WHat are the alternatives when a "STUDENT" tuple is deleted?
  * Delete all enrolled tuples that refer to it
  * Disalllow deletion of a STUDENT tuple that is referred to
  * Set SID in Enrolled tuples that refer to some "default" SID
  * If SID was not part of the primary key, set SID to a special value "NULL" denoting "unkown" or "inapplicable"
 
* SQL/92 and SQL/99 support all 4 options on delete and upadte
  * NO ACTION (default)
    * Delete/update is rejected
  * CASCADE
    * Also delete all tuples that refer to the deleted tuple
  * SET NULL / SET DEFAULT
    * Sets foreign key value of referencing type      

## Relational Database

 * A database schema is a set of relation shcemas and a set of integrity constraints

### Database Languages

* Data Definition Language (DDL)
  * Define schemas
  * Define Integrity Constraints
 
* Sata Manipulation Language (DML)
  * To ask questions = Query
  * To insert delete, and update data
 
### SQL Datatypes

* Numberic
  * Fixed numbers, approximate nubers, formatted numbers
* Character Strings
  * Fixed & varying length, CLOBS [SQL99], foreign language
* Bit Strings
  * Fixed & varying length, BLOBS[SQL99]
  * B'011010'       
