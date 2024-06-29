## 1. What is meant by an entity-relationship (E-R) model? Explain the terms Entity, Entity Type, and Entity Set in DBMS.

An **entity-relationship model** is a diagrammatic approach to a database design where real-world objects are represented as entities and relationships between them are mentioned.

![Entity Modal](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/269/original/E_R_Model.png?1617187943)

**Entity**: An entity is defined as a real-world object having attributes that represent characteristics of that particular object. For example, a student, an employee, or a teacher represents an entity.

**Entity Type**: An entity type is defined as a collection of entities that have the same attributes. One or more related tables in a database represent an entity type. Entity type or attributes can be understood as a characteristic which uniquely identifies the entity.  For example, a student represents an entity that has attributes such as student_id, student_name, etc.

**Entity Set**: An entity set can be defined as a set of all the entities present in a specific entity type in a database. For example, a set of all the students, employees, teachers, etc. represent an entity set.


## 2. What is meant by normalization and denormalization?

**Normalization** is a process of reducing redundancy by organizing the data into multiple tables. Normalization leads to better usage of disk spaces and makes it easier to maintain the integrity of the database. 

**Denormalization** is the reverse process of normalization as it combines the tables which have been normalized into a single table so that data retrieval becomes faster. JOIN operation allows us to create a denormalized form of the data by reversing the normalization.

Normalization and denormalization are key concepts in database design, each with its own purpose and benefits.

Let's learn more about them

### Normalization

Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity. This involves dividing a database into two or more tables and defining relationships between them. The primary goal of normalization is to minimize duplicate data and ensure data dependencies make sense to increase consistency.

#### Example of Normalization

Consider a simple database for a school system, storing student information and the courses they enroll in:

**Unnormalized Table:**

| StudentID | StudentName | CourseID | CourseName | Instructor |
|-----------|-------------|----------|------------|------------|
| 1         | Alice       | C101     | Math       | Prof. Smith|
| 1         | Alice       | C102     | Science    | Prof. Doe  |
| 2         | Bob         | C101     | Math       | Prof. Smith|
| 2         | Bob         | C103     | History    | Prof. White|

**Normalized Tables:**

*Students Table:*
| StudentID | StudentName |
|-----------|-------------|
| 1         | Alice       |
| 2         | Bob         |

*Courses Table:*
| CourseID | CourseName | Instructor   |
|----------|------------|--------------|
| C101     | Math       | Prof. Smith  |
| C102     | Science    | Prof. Doe    |
| C103     | History    | Prof. White  |

*Enrollments Table:*
| StudentID | CourseID |
|-----------|----------|
| 1         | C101     |
| 1         | C102     |
| 2         | C101     |
| 2         | C103     |

In the normalized form, the redundancy is reduced, and data consistency is maintained. For instance, if the name of a student or course changes, it only needs to be updated in one place.

### Denormalization

Denormalization is the process of combining normalized tables to improve read performance. This may introduce redundancy and potential inconsistencies, but it reduces the number of joins needed when querying data, thus speeding up read operations.

#### Example of Denormalization

Using the previously normalized tables, a denormalized version might look like this:

**Denormalized Table:**

| StudentID | StudentName | CourseID | CourseName | Instructor   |
|-----------|-------------|----------|------------|--------------|
| 1         | Alice       | C101     | Math       | Prof. Smith  |
| 1         | Alice       | C102     | Science    | Prof. Doe    |
| 2         | Bob         | C101     | Math       | Prof. Smith  |
| 2         | Bob         | C103     | History    | Prof. White  |

Here, the data redundancy is back, but this structure can be more efficient for read-heavy operations, where frequent joins would otherwise slow down performance. 

### Key Differences

- **Normalization** focuses on reducing redundancy and improving data integrity.
- **Denormalization** focuses on improving read performance at the expense of introducing redundancy.

### Practical Usage

- **Normalization** is beneficial in transactional databases where data integrity is crucial.
- **Denormalization** is useful in read-heavy applications like data warehousing where performance is more critical than data redundancy. 

Both normalization and denormalization have their place in database design, and the choice between them depends on the specific requirements and use cases of the application.



## 3. What is a lock. Explain the major difference between a shared lock and an exclusive lock during a transaction in a database.

A database lock is a mechanism to protect a shared piece of data from getting updated by two or more database users at the same time. When a single database user or session has acquired a lock then no other database user or session can modify that data until the lock is released.

**Shared Lock**: A shared lock is required for reading a data item and many transactions may hold a lock on the same data item in a shared lock. Multiple transactions are allowed to read the data items in a shared lock.

**Example**:

Imagine a library database where users can search for books. If user A is reading the details of a book (e.g., title, author, availability), a shared lock is placed on that book's data. While user A holds the shared lock, user B can also read the same book's details, but neither user A nor user B can update the book's data until the shared locks are released.



**Exclusive lock**: An exclusive lock is a lock on any transaction that is about to perform a write operation. This type of lock doesn’t allow more than one transaction and hence prevents any inconsistency in the database. 

**Example**:

In the same library database, if user C wants to borrow a book, an exclusive lock is placed on the book's data to update its availability status. While user C holds the exclusive lock, no other user can read or update the book's data, ensuring that the borrowing transaction is completed without conflicts.