# Lecture 6

## Database Languages

* Data Definition Language (DDL)
  * Define schemas
  * Define integrity constraints
    * Example:  Unique SIDs
   
* Data Manipulation Language (DML)
  * To ask questions - Query
    * Example: Which students have GAP > 3.75
  * To insert, delete, and update data
 
## SQL Datatypes

* Numeric
  * Fixed numbers, approximate numbers, formatted numbers
* Character Strings
  * Fixed & varying length, CLOBS [SQL99[, foreign language
* Bit Strings
  * Fixed & varying length, BLOBS [SQL99]
* Temporal Data
  * Date, time, and timestamp, intervals
* NULL value valid for all types

### Observation on Numeric Types

* They are like datatypes in C or Java
  * BIGINT for a long integer or integer
* Truncation is towards 0
* Rounding is business instead of **Scientific**
  * [0.4] rounds down to 0 | **[0.4] rounds down to 0**
  * [6.9] rounds up to 1   | **[5.9] rounds up to 1**
  * Halg times 5 is 0 and half 1
* Money or currency data types are numeric data with a currency sign: $, £, €, ¥

### Date and Time

* DATE (10 positions) -> YYYY-MM-DD
* TIME -> HH:MM:SS
* TIME(i) (additional decimal fractions of seconds) ->  HH:MM:SS:ddd...d
* TIME WITH TIME ZONE (inclides displacement: +1300 to -12:59) -> HH:MM:SS{+/-}hh:mm
* TIMESTAMP -> complete date and time with 6 fractions of seconds and optinal time zone

#### Functions on Dates

* All systems provide functions under different names
  * For constructing a date from stringsor integers
  * For extracting out the month, day, or year from a date
  * For displaying dates in different ways 
* Examples:
  * ```SQL
    CAST (string AS DATE) --CAST('2002-02-18' AS DATE)
    MAKEDATE (int year, int month, int day) --MAKEDATE(1990, 12, 31)
    EXTRACT (MONTH/DAY/YEAR FROM <date>) --EXTRACT (MONTH FROM DATE(2009, 9, 29))
    YEAR(<date>), MONTH(<date>), DAY(<date>)
    ```

#### Resolving Spec Ambiguity

* ```SQL
  TO_DATE('02182023, 'MMDDYYYY')
  ```
* It parses to the **longest keyword**
* Examples
  ```SQL
  --'DYY' = DY and Y
  TO_DATE('WED7', 'DYY') --= 01-FEB-17 [? 01-SEP-27]

  --'DDDYYYY' = DDD and YYYY
  TO_DATE('3232017', 'DDDYYYY') --= 19-NOV-17

  --'DYYY' = DY and YY
  TO_DATE('WED17', 'DYYY') --= 01FEB-17
  ```

## Basic SQL-DDL Commands

* For database Schemas: ```CREATE SCHEMA, DROP SCHEMA```
* For tables: ```CREATE TABLE, DROP TABLE, ALTER TABLE```
* For Domains: ```CREATE DOMAN, DROP DOMAIN```
* For Views: ```CREATE VIEW, DROP VIEW```
* For Integrity Constraints: ```CREATE IC, DROP IC```

### Create Database Schema

* A schemas is essentially a namespace: It contains named objects
* ```CREATE SCHEMA <sc-name> AUTHORIZATION <user-identifier>```
  * ```CREATE SCEMA micro_db AUTHORIZATION brian; --example```
* ```DROP SCHEMA <sc-name> [RESTRICT | CASCADE];```
  * Restrict: Removes the schema if the schema does not have any objects
  * Cascase: removes everything including data and definitions 
  * ```DROP SCHEMA micro_db RESTRICT --example``` 
    

### Constraints on Attributes

* NOT NULL
* DEFAULT VALUE
  * without the DEFAULT clause, the defaul value is NULL
* PRIMARY KEY (attribute list)
* UNIQUE (attribute list)
  * Allows the specification of alternative key(s)
* Foreign Key (key) REFERENCES table (key)
* CHECK (validity conditions)
  * Specifies the domain constraints
      
