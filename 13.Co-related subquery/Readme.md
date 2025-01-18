# CO-RELATED SUBQUERY

## Definition

A query written inside another query such that the outer query and the inner query are dependent on each other is known as a **Co-Related Subquery**.

## Working Principle

Consider two queries: an inner query and an outer query.

1. The outer query executes first but only partially.
2. The partially executed output is given as an input to the inner query.
3. The inner query executes completely and generates an output.
4. The output of the inner query is fed as an input to the outer query.
5. The outer query produces the final result.

Thus, the outer query and inner query are **interdependent** (dependent on each other).

## Important Notes

- A **join condition is a must** in a co-related subquery and must be written only in the **inner query**.
- Co-related subqueries work with the principles of both **subqueries** and **joins**.

## Difference Between Subquery and Co-Related Subquery

| Subquery | Co-Related Subquery |
|----------|---------------------|
| Inner query executes first | Outer query is dependent on inner query |
| Join condition not mandatory | Join condition is mandatory and must be written in the inner query |
| Outer query executes once | Outer query executes multiple times |

## Example

Consider the following tables:

### `DEPT` Table

| DNAME | DNO |
|--------|----|
| D1 | 10 |
| D2 | 20 |
| D3 | 30 |
| D4 | 40 |

### `EMP` Table

| ENAME | DNO |
|--------|----|
| A | 20 |
| B | 10 |
| C | 20 |
| D | 30 |

### Query to Find Department Names Having Employees
```sql
SELECT DNAME 
FROM DEPT D 
WHERE D.DNO IN (SELECT E.DNO FROM EMP E WHERE D.DNO = E.DNO);
```

### Query to Find Department Names with No Employees
```sql
SELECT DNAME 
FROM DEPT D 
WHERE D.DNO NOT IN (SELECT E.DNO FROM EMP E WHERE D.DNO = E.DNO);
```

## EXISTS & NOT EXISTS Operators

### EXISTS Operator

**Definition:** "EXISTS is a unary operator (one operand) that accepts a co-related subquery as an operand. It returns TRUE if the subquery returns any value other than NULL."

```sql
SELECT DNAME 
FROM DEPT D 
WHERE EXISTS (SELECT E.DNO FROM EMP E WHERE D.DNO = E.DNO);
```

### NOT EXISTS Operator

**Definition:** "NOT EXISTS is a unary operator (one operand) that accepts a co-related subquery as an operand. It returns TRUE if the subquery returns NULL."

## Finding Maximum & Minimum Salary

### Query to Find Maximum Salary
```sql
SELECT SAL 
FROM EMP E1 
WHERE (SELECT COUNT(DISTINCT SAL) FROM EMP E2 WHERE E1.SAL < E2.SAL) = 0;
```

### Query to Find N-th Maximum Salary
```sql
SELECT SAL 
FROM EMP E1 
WHERE (SELECT COUNT(DISTINCT SAL) FROM EMP E2 WHERE E1.SAL < E2.SAL) = N-1;
```

### Query to Find Minimum Salary
```sql
SELECT SAL 
FROM EMP E1 
WHERE (SELECT COUNT(DISTINCT SAL) FROM EMP E2 WHERE E1.SAL > E2.SAL) = 0;
```

### Query to Find N-th Minimum Salary
```sql
SELECT SAL 
FROM EMP E1 
WHERE (SELECT COUNT(DISTINCT SAL) FROM EMP E2 WHERE E1.SAL > E2.SAL) = N-1;
```


