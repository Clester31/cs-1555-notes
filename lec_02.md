# Lecture 2

## Execution Abstraction

* A transaction is a logical unit of work in DBMSs
  * It is the execution of a program segment that performs some function or task by accessing shared data
  * Logcal grouping of query and update requests needed to perform a task
* Exmaples:
  * Deposit, Withdrawl, transfer money
  * Reserve a seat on a flight
  * Print monthly payment checks
  * Update inventory
 
## ACID Properties

* **A**tomicity
  * Either all of the operations associated with a transaction happen or _none_ of them happen
* **C**onsistency
  * A transaction is a correct program segment. It satisfies the integrity constraints on the database at the transaction's boundaries 
* **I**solation
  * Transactions are independent, the result of the execution of the concurrent transaction is the same as if transactions were executed serially, one after the other
* **D**urability
  * The effects of completed transactions become permanent surviving any subsequent failures
 
## BaSE in NoSQL Databases

* ACID to BaSE: No immediate consistency, data freshness & accuracy
  * Basic Availability: The database appears to work most of the time
  * Soft-state: Stores don't have to be write-consistent, nor do differentreplicas have to be mutually ocnsistent all of the time
  * Eventual Consistency: Stores exhibit consistency at some later point
 
## Reliability

* Enforcing _integrity constraints_
  * E.g. data type, relationships between values
  * Data in DB must satisfy integrity constraints
  * Transactions are committed if they do not violate any integrity constraints
  * Integrity constraints are stored in the catalog
* Ensuring _data integrity_ despite failures
  * Data are not lost when the system or a transaction fails for whatever reason
* Security
  * Encryptionl & Private information Retrieval
  * Authentication
  * Data Domains, Compartmentalization
* Access Control
  * Who (user/role), what (data), how (operations)
  * Views and access permissions in the catalog
 
## Performance Problems with Files

* Redundancy
  * Waste of Space
* Waste of Effort
  * Some change in multiple places
* Need for coordination
  * Inconsistent data
  * Independent updates
  * E.g., Jan-19-2017 vs Jan-29-2017
 
## Efficiency and Performance

* Space Efficiency
  * Minimizes data redundancy by storing data only one
* Time efficiency (response time)
  * Eliminates the need for multiple updates to keep the replicas consistent and up-to-date
  * Enchances query performance by means of optimizations and access methods
  * Allows many users (transactions) to access and share the database concurrently
 
## When is an SQL-DBMS Inappropriate

* Disadvantages
  * Price to buy (DBMS & Hardware)
  * Additional experties (SQL/DBA)
* Hence, it is overkill when:
  * The database has a simple structure or its overall design is small
  * The application is simple, special purpose, and is not expected to change
  * Concurrent, multiple-user access is not required
  * Can tolerate failures
  * Monitor applications, high volume of updates
 
## When is a DBMS important?

* To integrate efficiently and correctly large volumes of related data
  * Central control, tuning for better performance, security
* Building of large applications
  * New applications using a DBMS is estimated 1/6 to 1/4 of the time of applications using a file system
  * Economy of scale
* Expandability / Flexibility
  * Supports evolution without affecting existing applications
* Supports sharing and discovering of information
  * Data minig, deductive databases, active databases
* DBMS ensures true QOS

# Conceptual Database Design & ER-Model

## Database Goal / Data Modeling

* What is the full, real-world problem?
* Which components are we focused on/need to store
  * Wchich objects will we need to store
    * What characteristics define and distinguish these obejcts
  * Are there interactions between these objects 
* **Goal: How can we model this mini-world Database System**

## Functional Design

* High-level specification of Transactions
  * DBMS-Independent
  * Event Diagrams
* Application program design
  * DBMS-specific (DB Schema together with Data Manipulation Language [DML])
  * Language and environment-specific
 
## Database Desing

* Database design is the activity of specifying the schema of a database in a given data model
* Three categories:
  * Conceptual database design
  * Logical database design
  * Physical database design
 
* Conceptual Database Design
  * An abstract but complete description of the DB
  * Implementation independent
  * E.g., conceptual model: E-R model
 
* Logical Database Design
  * The conceptual database schema
  * Formal Schema in an implementation data model
  * E.g., Relational, O-O, O-R, Network, heirarchical, graph, XML/JSON
 
* Physical Database Design
  * Internal Schema: Internal storage organization of objects, implementing the conceptual object
 
## Entity Relationship Model

* Two semantic primitives
* **Entities**
  * Objects with physical existence
    * Alex, Pat, Alex's house
  * Objects with conceptual existence
    * University, Course, Account
* **Relationships**
  * Associations / Interactions between two or more entities
    * e.g., Alex married Pat, Pat studies Physics, etc.
   
### Attributes

* Entities are characterized by their attributes
  * Alex has an age
  * Pat's care has a color
  * The CS 1520 project has a deadline
* Relationships may also have attributes
  * Alex _married_ Pat on Jan 7
  * Pat worked on the CS 1520 project for 6 hours
    
![image](https://github.com/user-attachments/assets/b781259e-ff86-4b0a-b75e-a7808886e109)
   
