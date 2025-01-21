# Normalization

**Normalization** is the process of reducing a large table into smaller tables to remove redundancies and anomalies by identifying their functional dependencies.

- **Alternate Definitions**:
  - The process of decomposing a large table into smaller tables is known as Normalization.
  - Reducing a table to its Normal Form is known as Normalization.

---

## What is Normal Form?

A table without redundancies and anomalies is said to be in **Normal Form**.

---

## Levels of Normal Form

1. **First Normal Form (1NF)**
2. **Second Normal Form (2NF)**
3. **Third Normal Form (3NF)**
4. **Boyce-Codd Normal Form (BCNF)**

> **Note**: If a table/entity is reduced to 3NF, then the table is said to be normalized.

---

### Example Tables

#### Table 1
| QID | NAME | C1      | C2 | C3 |
|-----|------|---------|----|----|
| 1   | A    | JAVA    | MT |    |
| 2   | B    | JAVA    | SQL|    |
| 3   | C    | SQL     | MT |    |

#### Table 2
| EID | ENAME | SAL | DEPTNO | DNAME | LOC |
|-----|-------|-----|--------|-------|-----|
| 1   | A     | 100 | 10     | D1    | L1  |
| 2   | B     | 120 | 20     | D2    | L2  |
| 3   | C     | 320 | 10     | D1    | L1  |
| 4   | D     | 251 | 10     | D1    | L1  |

**Functional Dependencies**:
- `(EID, DEPTNO) -> (ENAME, SAL, DNAME, LOC)`  
  (Composite key attributes result in partial functional dependency).

**Decomposition**:
- **R1**: `(EID, ENAME, SAL)`
- **R2**: `(DEPTNO, DNAME, LOC)`

---

## Normal Forms

### First Normal Form (1NF)

1. No duplicate records.
2. Multivalued data should not be present.

#### Example
| QID | NAME | COURSE       |
|-----|------|--------------|
| 1   | A    | JAVA         |
| 2   | B    | JAVA, SQL    |
| 3   | C    | MT, SQL      |
| 1   | A    | MT           |

---

### Second Normal Form (2NF)

1. The table should be in 1NF.
2. The table should not have **Partial Functional Dependency**.

#### Example: EMPLOYEE Table
| EID | ENAME | SAL | DEPTNO | DNAME | LOC |
|-----|-------|-----|--------|-------|-----|

---

### Third Normal Form (3NF)

1. The table should be in 2NF.
2. The table should not have **Transitive Functional Dependency**.

#### Decomposition Example
| EID | ENAME | SAL |
|-----|-------|-----|
| 1   | A     | 100 |
| 2   | B     | 120 |
| 3   | C     | 320 |
| 4   | D     | 251 |

| DEPTNO | DNAME | LOC |
|--------|-------|-----|
| 10     | D1    | L1  |
| 20     | D2    | L2  |

**Transitive Functional Dependency**:
- **R1**: `(EID, ENAME, COMM)`
- **R2**: `(PINCODE, STATE, COUNTRY)`

#### Example: Employee Table
| EID | ENAME | SAL | COMM | PINCODE | STATE | COUNTRY |
|-----|-------|-----|------|---------|-------|---------|
- Functional Dependencies:
  - `EID -> ENAME, SAL, COMM, COUNTRY`
  - `PINCODE -> STATE, COUNTRY`
