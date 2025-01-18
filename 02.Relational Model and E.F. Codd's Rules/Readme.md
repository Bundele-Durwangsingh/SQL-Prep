# Relational Model and E.F. Codd's Rules

## 1. Introduction to the Relational Model
- The relational model was introduced by **E.F. Codd**.
- In this model, data is stored in tables consisting of **rows** (records) and **columns** (attributes).

### Example Table:
| EID | ENAME  | SALARY |
|-----|--------|--------|
| 1   | SMITH  | 1000   |
| 2   | ALLEN  | 1500   |
| 3   | CLARK  | 2000   |

- Any database management system following the relational model is termed as **RDBMS**.

---

## 2. Rules of E.F. Codd
### Key Rules:
1. **Single-Valued Entries**:
   - Each cell in a table must contain a single value.

   #### Example:
   Invalid:
   | EID | PHONE_NO   |
   |-----|------------|
   | 1   | 101, 102   |

   Valid:
   | EID | PHONE_NO |
   |-----|----------|
   | 1   | 101      |
   | 2   | 102      |

2. **Data Stored in Tables**:
   - Data, including metadata, is stored in tables.

3. **Relationships via Keys**:
   - Tables can be connected using **key attributes** (e.g., primary keys, foreign keys).

4. **Data Validation**:
   - Data entered into tables must be validated using datatypes and constraints.

---

## 3. Metadata and Validation
- **Metadata**: Data about data, such as details of attributes, formats, and constraints.

#### Example:
| Image Name | Size | Format | Resolution  |
|------------|------|--------|-------------|
| MyPic      | 127kB| JPEG   | 400x600     |

- **Data Validation**:
  1. **Datatypes**: Define the type of data stored in a column.
  2. **Constraints**: Optional rules for ensuring data integrity.
