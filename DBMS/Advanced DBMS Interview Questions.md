## 1. Explain the difference between a 2-tier and 3-tier architecture in a DBMS.

The 2-tier architecture refers to the client-server architecture in which applications at the client end directly communicate with the database at the server end without any middleware involved.

![2-tier](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/283/original/2_tier.png?1617188844)


### 2-Tier Architecture

- **Structure:** 
  - **Client:** Directly communicates with the database server.
  - **Server:** Contains the database and handles client requests.
  
- **Features:**
  - No intermediate layer; the client connects directly to the database.
  - Simpler and easier to set up.
  - Less secure since clients have direct access to the database.

- **Example:** 
  - A contact management system using MS Access where users connect directly to the database.


The **3-tier architecture** contains another layer between the client and the server to provide GUI to the users and make the system much more secure and accessible. In this type of architecture, the application present on the client end interacts with an application on the server end which further communicates with the database system.

![3-tier](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/284/original/3_tier.png?1617188871)


### 3-Tier Architecture

- **Structure:**
  - **Client (Presentation Layer):** Provides the user interface (e.g., web browser or application).
  - **Application Server (Business Logic Layer):** Acts as a middle layer handling business logic and processing.
  - **Database Server (Data Layer):** Stores and manages the database.

- **Features:**
  - More secure, as the database is not directly accessible to the client.
  - Better scalability and maintainability.
  - Separates user interface, business logic, and data management.

- **Example:**
  - A large website where users interact with a web interface, which communicates with a server-side application, and then accesses the database.

### Key Differences:

- **Security:** 3-tier is more secure due to the separation of layers.
- **Scalability:** 3-tier can handle more users and more complex applications.
- **Maintenance:** 3-tier allows for easier updates and changes to specific layers without affecting others.

### Summary:

- **2-Tier:** Direct client-to-database connection, simpler but less secure.
- **3-Tier:** Uses an intermediate application server, providing better security and scalability.


## 2. Explain different types of keys in a database.

There are mainly 7 types of keys in a database:

**Candidate Key**: The candidate key represents a set of properties that can uniquely identify a table. Each table may have multiple candidate keys. One key amongst all candidate keys can be chosen as a primary key. In the below example since studentId and firstName can be considered as a Candidate Key since they can uniquely identify every tuple.

**Super Key**: The super key defines a set of attributes that can uniquely identify a tuple. Candidate key and primary key are subsets of the super key, in other words, the super key is their superset.

**Primary Key**: The primary key defines a set of attributes that are used to uniquely identify every tuple. In the below example studentId and firstName are candidate keys and any one of them can be chosen as a Primary Key. In the given example studentId is chosen as the primary key for the student table.

![keys](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/282/original/db_keys.png?1617188783)


**Unique Key**: The unique key is very similar to the primary key except that primary keys don’t allow NULL values in the column but unique keys allow them. So essentially unique keys are primary keys with NULL values.

**Alternate Key**: All the candidate keys which are not chosen as primary keys are considered as alternate Keys. In the below example, firstname and lastname are alternate keys in the database.

**Foreign Key**:  The foreign key defines an attribute that can only take the values present in one table common to the attribute present in another table. In the below example courseId from the Student table is a foreign key to the Course table, as both, the tables contain courseId as one of their attributes.

**Composite Key**:  A composite key refers to a combination of two or more columns that can uniquely identify each tuple in a table. In the below example the studentId and firstname can be grouped to uniquely identify every tuple in the table.

![different keys](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/240/original/relationship_between_keys.png?1616078153)


## 3. Explain different types of Normalization forms in a DBMS.

Following are the major normalization forms in a DBMS:

![normalization](https://d3n0h9tb65y8q.cloudfront.net/public_assets/assets/000/002/819/original/normalization_forms.png?1645074158)

![table](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/275/original/normalization_ex.png?1617188308)


**1NF**: It is known as the first normal form and is the simplest type of normalization that you can implement in a database. A table to be in its first normal form should satisfy the following conditions:

- Every column must have a single value and should be atomic.
- Duplicate columns from the same table should be removed.
- Separate tables should be created for each group of related data and each row should be identified with a unique column.

![1nf](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/276/original/1NF.png?1617188352)

**Example**:

Before 1NF:
Student
| studentId | name  | subjects        |
|-----------|-------|------------------|
| 1         | John  | Math, Science    |

After 1NF:
Student
| studentId | name  | subject  |
|-----------|-------|----------|
| 1         | John  | Math     |
| 1         | John  | Science  |



**2NF**: It is known as the second normal form. A table to be in its second normal form should satisfy the following conditions:

- The table should be in its 1NF i.e. satisfy all the conditions of 1NF.
- Every non-prime attribute of the table should be fully functionally dependent on the primary key i.e. every non-key attribute should be dependent on the primary key in such a way that if any key element is deleted then even the non_key element will be saved in the database.
- Must be in 1NF.
- No partial dependency (no non-key attribute depends only on a part of a composite key).

![2nf](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/277/original/2NF.png?1617188407)

![2nf](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/278/original/2NF-02.png?1617188442)


**Example**:

Before 2NF:
Order
| orderId | productId | productName | orderDate |
|---------|-----------|-------------|-----------|
| 1       | 101       | Widget      | 2023-01-01|

After 2NF:
Order
| orderId | orderDate |
|---------|-----------|
| 1       | 2023-01-01|

Product
| productId | productName |
|-----------|-------------|
| 101       | Widget      |


**3NF**: It is known as the third normal form. A table to be in its third normal form should satisfy the following conditions:
- The table should be in its 2NF i.e. satisfy all the conditions of 2NF.
- There is no transitive functional dependency of one attribute on any attribute in the same table.
- Must be in 2NF.
- No transitive dependency (no non-key attribute depends on another non-key attribute).

![3nf](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/279/original/3NF.png?1617188565)


![enf](https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/280/original/3NF-01.png?1617188616)

**Example**:

Before 3NF:
Employee
| empId | empName | deptId | deptName  |
|-------|---------|--------|-----------|
| 1     | Alice   | D01    | Sales     |

After 3NF:
Employee
| empId | empName | deptId |
|-------|---------|--------|
| 1     | Alice   | D01    |

Department
| deptId | deptName |
|--------|----------|
| D01    | Sales    |

**BCNF**: BCNF stands for Boyce-Codd Normal Form and is an advanced form of 3NF. It is also referred to as 3.5NF for the same reason. A table to be in its BCNF normal form should satisfy the following conditions:
- The table should be in its 3NF i.e. satisfy all the conditions of 3NF.
- For every functional dependency of any attribute A on B
(A->B), A should be the super key of the table. It simply implies that A can’t be a non-prime attribute if B is a prime attribute.
- Must be in 3NF.
- Every determinant must be a candidate key.

Before BCNF:
Project
| projId | projName | managerId | managerName |
|--------|----------|-----------|-------------|
| 1      | Alpha    | 101       | Bob         |

After BCNF:
Project
| projId | projName | managerId |
|--------|----------|-----------|
| 1      | Alpha    | 101       |

Manager
| managerId | managerName |
|-----------|-------------|
| 101       | Bob         |


### 5. Fourth Normal Form (4NF)

- **Definition:** Ensures no multi-valued dependencies other than a candidate key.
- **Requirements:**
  - Must be in BCNF.
  - No multi-valued dependencies.

**Example:**
```plaintext
Before 4NF:
StudentCourseHobby
| studentId | course   | hobby   |
|-----------|----------|---------|
| 1         | Math     | Music   |
| 1         | Science  | Art     |

After 4NF:
StudentCourse
| studentId | course   |
|-----------|----------|
| 1         | Math     |
| 1         | Science  |

StudentHobby
| studentId | hobby    |
|-----------|----------|
| 1         | Music    |
| 1         | Art      |
```

### 6. Fifth Normal Form (5NF)

- **Definition:** Ensures no join dependencies exist other than candidate keys.
- **Requirements:**
  - Must be in 4NF.
  - Decomposed in such a way that no loss of information occurs through joins.

**Example:** Generally involves complex relationships and is less commonly used in practice.

### 7. Sixth Normal Form (6NF)

- **Definition:** Ensures no non-trivial join dependencies exist.
- **Requirements:**
  - Must be in 5NF.
  - Typically used in specialized database systems.

### Summary

- **1NF:** Atomic values, no repeating groups.
- **2NF:** No partial dependencies on a composite key.
- **3NF:** No transitive dependencies.
- **BCNF:** Stronger version of 3NF, every determinant is a candidate key.
- **4NF:** No multi-valued dependencies.
- **5NF:** No join dependencies.
- **6NF:** No non-trivial join dependencies.

Normalization helps maintain data integrity and reduces redundancy in relational databases.