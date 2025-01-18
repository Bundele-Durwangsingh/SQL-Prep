# SQL Datatypes

## 1. Introduction to SQL Datatypes
- SQL datatypes specify the type of data that can be stored in each column of a table.
- Choosing the correct datatype ensures data integrity and optimizes storage.

---

## 2. Commonly Used SQL Datatypes

| Datatype    | Description                                                    |
|-------------|----------------------------------------------------------------|
| **CHAR**    | Fixed-length string. Stores up to 2000 characters.            |
| **VARCHAR** | Variable-length string. Stores up to 4000 characters.         |
| **VARCHAR2**| Enhanced version of VARCHAR. Supports up to 4000 characters.  |
| **NUMBER**  | Numeric data. Supports precision and scale for floating points.|
| **DATE**    | Date and time values. Default format: `DD-MON-YYYY`.           |
| **CLOB**    | Character large object. Stores up to 4GB of text data.         |
| **BLOB**    | Binary large object. Stores up to 4GB of binary data (images, etc.).|

---

## 3. Examples of Using Datatypes

### 3.1 CHAR and VARCHAR
```sql
-- CHAR Example
CREATE TABLE FixedLengthExample (
    Code CHAR(5),
    Description CHAR(50)
);

-- VARCHAR Example
CREATE TABLE VariableLengthExample (
    Name VARCHAR(50),
    Address VARCHAR2(100)
);
```

### 3.2 NUMBER
```sql
-- NUMBER with Precision and Scale
CREATE TABLE SalaryDetails (
    EmployeeID INT,
    Salary NUMBER(8, 2), -- Up to 8 digits, 2 after decimal
    Bonus NUMBER(5, 2)
);
```

### 3.3 DATE
```sql
-- DATE Example
CREATE TABLE ImportantDates (
    EventID INT,
    EventName VARCHAR(100),
    EventDate DATE
);

-- Inserting Date Values
INSERT INTO ImportantDates (EventID, EventName, EventDate)
VALUES (1, 'Project Launch', TO_DATE('22-JUN-2025', 'DD-MON-YYYY'));
```

### 3.4 CLOB and BLOB
```sql
-- CLOB Example
CREATE TABLE TextStorage (
    DocumentID INT,
    DocumentContent CLOB
);

-- BLOB Example
CREATE TABLE MediaStorage (
    MediaID INT,
    MediaFile BLOB
);
```

---

## 4. Notes
- **CHAR vs. VARCHAR**:
  - CHAR is fixed-length, while VARCHAR adjusts to the content size.
  - VARCHAR saves storage space for variable-length strings.
- **NUMBER**:
  - Precision defines the total digits.
  - Scale specifies digits after the decimal point.
- **DATE**:
  - Use `TO_DATE` function to format date values.
- **CLOB/BLOB**:
  - Use for large text or binary data.
  - Avoid storing large files directly in databases when performance is critical.
