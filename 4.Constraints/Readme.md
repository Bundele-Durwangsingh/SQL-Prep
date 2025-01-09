# SQL Constraints

## 1. Introduction to Constraints
- Constraints are rules applied to columns in a table to enforce data integrity.
- They ensure that the data entered into a table meets specific conditions.

---

## 2. Types of Constraints

| Constraint     | Description                                                  |
|----------------|--------------------------------------------------------------|
| **UNIQUE**     | Ensures all values in a column are unique.                   |
| **NOT NULL**   | Ensures a column cannot have NULL values.                    |
| **CHECK**      | Validates that values in a column meet a specific condition. |
| **PRIMARY KEY**| Uniquely identifies each row in a table. Combines UNIQUE and NOT NULL. |
| **FOREIGN KEY**| Establishes a relationship between columns in different tables. |

---

## 3. Detailed Explanation of Constraints

### 3.1 UNIQUE Constraint
- Ensures that all values in a column are distinct.

#### Example:
```sql
CREATE TABLE Employees (
    EmployeeID INT UNIQUE,
    Name VARCHAR(50),
    Department VARCHAR(50)
);
```

### 3.2 NOT NULL Constraint
- Ensures that a column cannot contain NULL values.

#### Example:
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Age INT NOT NULL
);
```

### 3.3 CHECK Constraint
- Ensures that all values in a column satisfy a specific condition.

#### Example:
```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    Price DECIMAL(10, 2) CHECK (Price > 0),
    Quantity INT CHECK (Quantity >= 0)
);
```

### 3.4 PRIMARY KEY Constraint
- Uniquely identifies each record in a table.
- Combines UNIQUE and NOT NULL constraints.

#### Example:
```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT NOT NULL,
    OrderDate DATE NOT NULL
);
```

### 3.5 FOREIGN KEY Constraint
- Creates a relationship between two tables by referencing the primary key of another table.

#### Example:
```sql
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(50)
);

CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

---

## 4. Assignments

### Question 1:
Differentiate between **Primary Key** and **Foreign Key**.

#### Answer:
| Feature              | Primary Key                          | Foreign Key                          |
|----------------------|--------------------------------------|--------------------------------------|
| Uniqueness          | Must be unique for each record.      | Can have duplicate values.          |
| Nullability         | Cannot accept NULL values.           | Can accept NULL values.             |
| Purpose             | Uniquely identifies rows in a table. | Links two tables.                   |
| Number Per Table    | Only one primary key per table.      | Multiple foreign keys are allowed.  |

### Question 2:
Write a query to create a `Customer` and `Order` table with a foreign key relationship.

#### Answer:
```sql
CREATE TABLE Customer (
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL
);

CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customer(CustomerID)
);
