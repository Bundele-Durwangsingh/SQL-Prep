# Database Introduction and CRUD Operations

## 1. Introduction to Databases and DBMS

### What is Data?
- **Data**: Raw facts that describe the attributes of an entity.
  
#### Example:
| Attribute  | Value       |
|------------|-------------|
| Height     | 20 cm       |
| Color      | Blue        |
| Capacity   | 500 ml      |

### What is a Database?
- A **database** is a medium to store data in a systematic and organized manner.

#### Key Concepts:
- **Entity**: Represents a real-world object.
- **Attributes**: Properties of an entity (e.g., brand, RAM, touch).

### Database Management System (DBMS):
- Software that maintains and manages databases.
- Features: Security and authorization.

### Relational Database Management System (RDBMS):
- Stores data in tables (rows and columns).
- Any DBMS following E.F. Codd's rules is considered an RDBMS.

---

## 2. CRUD Operations
CRUD refers to the four basic operations performed on a database:

### 2.1 Create (INSERT)
- Adds new data into a table.

#### Example:
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT,
    Grade CHAR(1)
);

INSERT INTO Students (StudentID, Name, Age, Grade)
VALUES (1, 'John Doe', 20, 'A');
```

### 2.2 Read (SELECT)
- Retrieves data from a table.

#### Example:
```sql
SELECT * FROM Students;
```

### 2.3 Update (UPDATE)
- Modifies existing data in a table.

#### Example:
```sql
UPDATE Students
SET Grade = 'B'
WHERE StudentID = 1;
```

### 2.4 Delete (DELETE)
- Removes data from a table.

#### Example:
```sql
DELETE FROM Students
WHERE StudentID = 1;
```
