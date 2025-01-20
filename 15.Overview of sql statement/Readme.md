# **SQL Statements Overview**

## **Classification of SQL Statements**
SQL statements are classified into five types:

1. **Data Definition Language (DDL)**
2. **Data Manipulation Language (DML)**
3. **Transaction Control Language (TCL)**
4. **Data Control Language (DCL)**

---

## **1. Data Definition Language (DDL)**
DDL is used to define and manage database objects. It deals with the structure of database objects.

### **Key DDL Statements**

1. **CREATE**: Used to construct an object in the database.
   - Objects can include tables or views (virtual tables).

#### **How to Create a Table**
- Ensure tables have unique names.
- Define the number of columns.
- Assign names, data types, and optional constraints to columns.

#### **Example 1: CUSTOMER Table**

| Column Name | Data Type     | Constraints          |
|-------------|---------------|----------------------|
| CID         | Number(2)     | NOT NULL, PRIMARY KEY |
| CNAME       | Varchar(10)   | NOT NULL            |
| CNO         | Number(10)    | NOT NULL, UNIQUE, CHECK (length(CNO) = 10) |
| ADDRESS     | Varchar(15)   | NULL                |

**Syntax to create a table:**
```sql
CREATE TABLE Table_Name (
    Column_Name1 DataType Constraint_Type,
    Column_Name2 DataType Constraint_Type,
    Column_Name3 DataType Constraint_Type
    ...
);
```
**Example:**
```sql
CREATE TABLE CUSTOMER (
    CID Number(2) PRIMARY KEY,
    CNAME Varchar(10),
    CNO Number(10) NOT NULL CHECK (length(CNO) = 10),
    ADDRESS Varchar(15)
);
```

#### **Example 2: PRODUCT Table**

| Column Name | Data Type      | Constraints          |
|-------------|----------------|----------------------|
| PID         | Number(2)      | NOT NULL, PRIMARY KEY |
| PNAME       | Varchar(10)    | NOT NULL            |
| PRICE       | Number(7,2)    | CHECK (PRICE > 0)   |
| CID         | Number(2)      | FOREIGN KEY REFERENCES CUSTOMER(CID) |

**Example:**
```sql
CREATE TABLE PRODUCT (
    PID Number(2) PRIMARY KEY,
    PNAME Varchar(10),
    PRICE Number(7,2) CHECK (PRICE > 0),
    CID Number(2),
    CONSTRAINT CID_FK FOREIGN KEY (CID) REFERENCES CUSTOMER(CID)
);
```

2. **RENAME**: Used to rename a database object.
   - Syntax: `RENAME Table_Name TO New_Name;`
   - Example:
     ```sql
     RENAME Customer TO Cust;
     ```

3. **ALTER**: Used to modify the structure of a table.
   - **Add a column:**
     ```sql
     ALTER TABLE Table_Name
     ADD Column_Name DataType Constraint_Type;
     ```
   - **Drop a column:**
     ```sql
     ALTER TABLE Table_Name
     DROP COLUMN Column_Name;
     ```
   - **Rename a column:**
     ```sql
     ALTER TABLE Table_Name
     RENAME COLUMN Old_Column_Name TO New_Column_Name;
     ```
   - **Modify a column's data type:**
     ```sql
     ALTER TABLE Table_Name
     MODIFY Column_Name New_DataType;
     ```

4. **TRUNCATE**: Removes all records from a table permanently.
   - Syntax: `TRUNCATE TABLE Table_Name;`
   - Example:
     ```sql
     TRUNCATE TABLE Cust;
     ```

5. **DROP**: Deletes a table from the database permanently.
   - Syntax: `DROP TABLE Table_Name;`
   - Example:
     ```sql
     DROP TABLE Cust;
     ```
   - **To recover a dropped table:**
     ```sql
     FLASHBACK TABLE Table_Name TO BEFORE DROP;
     ```
   - **To delete the table from the recycle bin:**
     ```sql
     PURGE TABLE Table_Name;
     ```

**Note:** DDL statements are auto-commit statements.

---

## **2. Data Manipulation Language (DML)**
Used to manipulate database objects by performing insertion, updating, and deletion.

### **Key DML Statements**

1. **INSERT**: Used to insert records into a table.
   - Syntax:
     ```sql
     INSERT INTO Table_Name VALUES (Value1, Value2, Value3, ...);
     ```
   - Example:
     ```sql
     INSERT INTO CUSTOMER VALUES (1, 'DINGA', 9876543210, 'BANGALORE');
     ```

2. **UPDATE**: Used to modify existing records in a table.
   - Syntax:
     ```sql
     UPDATE Table_Name
     SET Column1 = Value1, Column2 = Value2, ...
     WHERE Condition;
     ```
   - Example:
     ```sql
     UPDATE CUSTOMER
     SET ADDRESS = 'MYSORE'
     WHERE CID = 1;
     ```

3. **DELETE**: Used to remove specific records from a table.
   - Syntax:
     ```sql
     DELETE FROM Table_Name
     WHERE Condition;
     ```
   - Example:
     ```sql
     DELETE FROM CUSTOMER
     WHERE CNAME = 'ABDUL';
     ```

---

## **3. Transaction Control Language (TCL)**
Used to control transactions performed on the database.

### **Key TCL Statements**

1. **COMMIT**: Saves all transactions to the database.
   - Syntax: `COMMIT;`
   - Example:
     ```sql
     INSERT INTO T1 VALUES ('A', 100);
     COMMIT;
     ```

2. **ROLLBACK**: Reverts the database to the last committed state.
   - Syntax: `ROLLBACK;`

3. **SAVEPOINT**: Marks a transaction point for restoration.
   - Syntax: `SAVEPOINT Savepoint_Name;`
   - Example:
     ```sql
     SAVEPOINT S1;
     ```

   - **Rollback to a savepoint:**
     ```sql
     ROLLBACK TO S1;
     ```

---

## **4. Data Control Language (DCL)**
Controls the access and permissions for users.

### **Key DCL Statements**

1. **GRANT**: Gives permission to a user.
   - Syntax:
     ```sql
     GRANT Permission_Type ON Table_Name TO User_Name;
     ```

2. **REVOKE**: Revokes permission from a user.
   - Syntax:
     ```sql
     REVOKE Permission_Type ON Table_Name FROM User_Name;
     ```

**Example:**
```sql
GRANT SELECT ON EMP TO HR;
REVOKE SELECT ON EMP FROM HR;
```

---

**Try It Out:**
- Differentiate between TRUNCATE and DELETE:

| **Aspect**    | **TRUNCATE**            | **DELETE**              |
|---------------|-------------------------|-------------------------|
| **Type**      | DDL                    | DML                     |
| **Scope**     | Removes all records    | Removes specific records |
| **Commit**    | Auto-commit            | Not auto-commit         |
