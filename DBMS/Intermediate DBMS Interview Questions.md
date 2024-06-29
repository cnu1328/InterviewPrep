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

## 4. Explain the difference between the DELETE and TRUNCATE command in a DBMS.

**DELETE** command: this command is needed to delete rows from a table based on the condition provided by the WHERE clause.

1. It deletes only the rows which are specified by the WHERE clause.
2. It can be rolled back if required.
3. It maintains a log to lock the row of the table before deleting it and hence it’s slow.

**TRUNCATE** command: this command is needed to remove complete data from a table in a database. It is like a DELETE command which has no WHERE clause.

1. It removes complete data from a table in a database.
2. It can't be rolled back even if required. ( truncate can be rolled back in some databases depending on their version but it can be tricky and can lead to data loss). Check this link for more details
3. It doesn’t maintain a log and deletes the whole table at once and hence it’s fast.


## 5. Explain the difference between intension and extension in a database

Following is the major difference between intension and extension in a database:

**Intension**: Intension or popularly known as database schema is used to define the description of the database and is specified during the design of the database and mostly remains unchanged.

**Extension**: Extension on the other hand is the measure of the number of tuples present in the database at any given point in time. The extension of a database is also referred to as the snapshot of the database and its value keeps changing as and when the tuples are created, updated, or destroyed in a database.

## 6. Explain different types of relationships amongst tables in a DBMS.

Following are different types of relationship amongst tables in a DBMS system:

### 1. One-to-One Relationship

In a one-to-one relationship, each row in table X is linked to exactly one row in table Y, and vice versa. This is used when each entity in both tables corresponds uniquely to one another.

![One to one](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/270/original/1_to_1.png?1617188060)

**Example:**
- **Tables:** `Person` and `Passport`
- **Relationship:** Each person has one passport.


**Tables:**
- `Person`:
  - `person_id` (Primary Key)
  - `name`
- `Passport`:
  - `passport_id` (Primary Key)
  - `person_id` (Foreign Key)

**SQL:**
```sql
CREATE TABLE Person (
    person_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE Passport (
    passport_id INT PRIMARY KEY,
    person_id INT,
    FOREIGN KEY (person_id) REFERENCES Person(person_id)
);
```

### 2. One-to-Many Relationship

In a one-to-many relationship, a single row in table X is related to multiple rows in table Y. This is common in situations where one entity can have multiple associated entities.

![one to Many](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/271/original/1_to_n.png?1617188084)


**Example:**
- **Tables:** `Author` and `Book`
- **Relationship:** One author can write many books.

**Tables:**
- `Author`:
  - `author_id` (Primary Key)
  - `name`
- `Book`:
  - `book_id` (Primary Key)
  - `title`
  - `author_id` (Foreign Key)

**SQL:**
```sql
CREATE TABLE Author (
    author_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE Book (
    book_id INT PRIMARY KEY,
    title VARCHAR(100),
    author_id INT,
    FOREIGN KEY (author_id) REFERENCES Author(author_id)
);
```

### 3. Many-to-Many Relationship

In a many-to-many relationship, multiple rows in table X can be related to multiple rows in table Y. This requires a junction table to manage the associations.

![many to many](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/272/original/m_to_m.png?1617188110)

**Example:**
- **Tables:** `Student` and `Course`
- **Relationship:** Students can enroll in many courses, and each course can have many students.

**Tables:**
- `Student`:
  - `student_id` (Primary Key)
  - `name`
- `Course`:
  - `course_id` (Primary Key)
  - `course_name`
- `Enrollment` (Junction Table):
  - `student_id` (Foreign Key)
  - `course_id` (Foreign Key)

**SQL:**
```sql
CREATE TABLE Student (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE Course (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100)
);

CREATE TABLE Enrollment (
    student_id INT,
    course_id INT,
    PRIMARY KEY (student_id, course_id),
    FOREIGN KEY (student_id) REFERENCES Student(student_id),
    FOREIGN KEY (course_id) REFERENCES Course(course_id)
);
```

### 4. Self-Referencing Relationship

In a self-referencing relationship, rows in a table are related to other rows within the same table. This is often used for hierarchical data.

![self - referencing](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/273/original/self_referencing.png?1617188132)



**Example:**
- **Table:** `Employee`
- **Relationship:** An employee can report to another employee (a manager).

**Table:**
- `Employee`:
  - `employee_id` (Primary Key)
  - `name`
  - `manager_id` (Foreign Key referencing `employee_id`)

**SQL:**
```sql
CREATE TABLE Employee (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100),
    manager_id INT,
    FOREIGN KEY (manager_id) REFERENCES Employee(employee_id)
);
```

### Summary

- **One-to-One:** Each row in one table is linked to one row in another table.
- **One-to-Many:** One row in one table is linked to multiple rows in another.
- **Many-to-Many:** Multiple rows in one table are linked to multiple rows in another, using a junction table.
- **Self-Referencing:** Rows in a table are linked to other rows in the same table.


## 7. Explain different levels of data abstraction in a DBMS.

The process of hiding irrelevant details from users is known as data abstraction. Data abstraction can be divided into 3 levels:

![levels](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/223/original/levels_of_abstraction.png?1616075395)


### 1. Physical Level

- **What it is:** This is the lowest level of abstraction and deals with how data is physically stored in the database.
- **Who uses it:** Database administrators but not usually developers or users.
- **Details:** Includes data storage details like file formats, indices, and data compression.

**Example:** Think of the data stored on disks or in specific file structures. You don’t need to know how the data is physically organized or stored.

### 2. Conceptual (Logical) Level

- **What it is:** This level defines what data is stored and the relationships between those data points.
- **Who uses it:** Database developers and administrators.
- **Details:** Includes tables, columns, data types, and relationships (like foreign keys).

**Example:** 
- Tables like `Customer` and `Order` with fields such as `customer_id`, `name`, `order_id`, and `order_date`.
- Defines how these tables are related (e.g., one customer can have many orders).

### 3. External (View) Level

- **What it is:** This level describes how users see the data, hiding the complexity of the underlying tables.
- **Who uses it:** End users or applications.
- **Details:** Users interact with views that present data in a specific way without showing the entire database schema.

**Example:**
- A **view** might show only the `customer_name` and `order_date` from the `Customer` and `Order` tables, providing a simplified interface.

### Real-World Example

Imagine a library database:

1. **Physical Level:**
   - Data stored on a disk in binary format, with file structures for books, authors, and borrow records.
   - Details like indexing methods and file paths are hidden.

2. **Conceptual (Logical) Level:**
   - **Tables:**
     - `Book` (with columns like `book_id`, `title`, `author_id`)
     - `Author` (with columns like `author_id`, `name`)
     - `Borrow` (with columns like `borrow_id`, `book_id`, `member_id`)
   - Relationships between tables (e.g., each book has one author).

3. **External (View) Level:**
   - **View:** `AvailableBooksView` might show only available books to users with fields like `title` and `author_name`, derived from the `Book` and `Author` tables.
   - Users run queries to see available books without seeing all the underlying data.

### Summary

- **Physical Level:** How data is physically stored.
- **Conceptual Level:** Structure of the database (tables, relationships).
- **External Level:** What users interact with (simplified views of the data).


## 8. What is Data Warehousing?

The process of collecting, extracting, transforming, and loading data from multiple sources and storing them in one database is known as data warehousing. A data warehouse can be considered as a central repository where data flows from transactional systems and other relational databases and is used for data analytics. A data warehouse comprises a wide variety of an organization’s historical data that supports the decision-making process in an organization.

![Data WareHousing](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/268/original/data_warehousing.png?1617187867)


### Key Components:

1. **Data Collection:**
   - Data is collected from multiple sources, such as transactional systems, relational databases, and external sources.

2. **ETL Process (Extract, Transform, Load):**
   - **Extract:** Data is pulled from different source systems.
   - **Transform:** Data is cleaned and formatted to ensure consistency.
   - **Load:** Data is stored in the data warehouse.

3. **Central Repository:**
   - A single database where all the integrated data is stored, often optimized for query performance.

4. **Data Analytics:**
   - The data warehouse supports various analytical processes, such as reporting, data mining, and machine learning, helping organizations make informed decisions.

### Example:

**Scenario:** An online retail company wants to analyze customer behavior and sales performance.

1. **Data Sources:**
   - **Transactional Systems:** Orders, customer interactions.
   - **CRM:** Customer information.
   - **ERP:** Inventory and supply chain data.

2. **ETL Process:**
   - **Extract:** Data from orders, customer info, inventory levels.
   - **Transform:** Clean data (e.g., correct formatting, remove duplicates).
   - **Load:** Store in the data warehouse.

3. **Data Warehouse Structure:**
   - **Tables:** 
     - `Customers` (customer_id, name, demographics)
     - `Sales` (order_id, customer_id, amount, date)
     - `Products` (product_id, name, category)

4. **Analytics:**
   - **Example Queries:**
     - Analyze sales trends over time.
     - Identify top-selling products.
     - Understand customer demographics.

### Benefits:

- **Centralized Data:** All data is in one place, making it easier to access and analyze.
- **Historical Analysis:** Stores historical data, enabling trend analysis.
- **Improved Decision-Making:** Supports data-driven decisions with comprehensive reports and insights.

### Real-World Example:

A **bank** might use a data warehouse to consolidate customer transaction data from various branches and online services. By analyzing this data, the bank can identify spending patterns, optimize marketing strategies, and improve customer service.
