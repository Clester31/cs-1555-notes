# Lecture 3

## Question

* Can an attribute be composite and have a single value?
  * Answer: Yes - you can store extra attributes about something inside of one value
 
### Example of a composite Attribute

![image](https://github.com/user-attachments/assets/d3af5d39-6e7f-46e7-9415-c304318fc996)

## Entity Types

* All similar (same attributes) entities are grouped into sets, an entity type

* Entity type schema specifies the common structure:
  * Type nae
  * Entity attributes *Doman, Value Set)
  * Constraints on entities k
* Faculty: Name(FN, LN, MI), DoB SSN, {Degree}, Rank
  * FN:String(15) LN:String(15), SSN:String(9), etc.
  * DOB DD/MM/YYYY
  * Degree: {BS, MS, PhD}
  * Rank: {Lecturer, Associate, Full}
 
### Uniqueness or Key Contraint

* Entities are distinguish various keys
* A key is a uniqueness contraint on attributes
* A key is defined over one or more attributes
  * SSN, StudentID, Car License Plate: State and Number
 
## Key Constraints

* **Superkeys**: Any combination of attributes that uniquely identifies an entity
* **Candidate Keys** is a minimal superkey
  * E.g., SSN and StudentID
* **Primary Key** is one of the candidate keys (StudentID)
* **Alternative Keys** are the remaining candidate keys (not chosen as the primary key)
  * The primary key is underlined while the alternative key is overlines
  ![image](https://github.com/user-attachments/assets/4379781e-d061-4ffe-90ed-3db25893a9e0) ![image](https://github.com/user-attachments/assets/f9edd551-8497-4e6e-aa78-7740427631f3)

## Relationship Types

* Relationship Types: Sets of relationships that are homogenous in participating entities
  * BELONGS: <FACULTY, DEPARTMENT>
  * ENROLLS: <STUDENT, SECTION>

  ![image](https://github.com/user-attachments/assets/246d4c4e-bf43-4c11-92fd-676bc88924d4)

### Degree of a Relationship

* Degree of a relationship is the number of participating entity types
  * 2-entities -> binary relationship
  * 3-entities -> ternary relationship
    * TAKES: <STUDENT, CLASS, FACULTY>
  * ...
  * N-entities -> N-ary relationships
 
### Recursive Relationship

* Recursive relationships involve the same entity type more that once with different roles
  * SUPERVISES <supervisor-faculty, supervisee-faculty>
 
  ![image](https://github.com/user-attachments/assets/a666e97d-0289-4b2d-aa10-79a6a5dd40d5)

### Constraints on Relationship Costs - Cardinality

* Cardinality Ration: Specifies the number of relationship instances that an entity can participate in
  * 1:1 - A Department has a single Chairperson and a Chairperson only chairs _one_ department
  * N:1 - A child has _one_ mother, but a mother can have _many_ children
  * 1:N - A mother can have _many_ children but a child can only have _one_ mother
  * M:N - A student enrolls in _many_ class sections and a class section has _many_ students enrolled
 
### Constraints on Relationship Types - Participation

* Participation
  * **Total** -> Existence of entity depends on the existence of a related entity
    * E.g., Classes have total participation to OFFER_BY department, since a class will not exist if it is not offered by the department
  * **Partial** -> Some entites are not related to other entites and their existance does NOT depend on a related entity
    * E.g., Faculty have partial participation to being the chair of a department, since faculty can exist in a department without being the chair
   
### Strong and Weak Entities

* Strong or ordinary entities:
  * Most common
  * Have independent existence in the mini-world
  * They are part of the core of the application
  * Have a key attribute making instances distinguishable
 
* Weak Entities:
  * They are independent on another entity, known as the _identifying owner_
  * No key attribute; Instances are distinguishable through an **identifying relationship** and a **discriminator** or **partial key**
    * Identifying relationsihp is always total participation
    * Discriminator and partial key are underlined using a dotted or dashed line 
 
