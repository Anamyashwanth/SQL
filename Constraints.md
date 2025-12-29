

## What are Constraints?

**Constraints** are rules applied to table columns to **enforce data integrity**.
They ensure that **only valid data** is stored in the database.

Constraints are enforced **automatically by SQL Server**.

---

## Types of Constraints in SQL Server

1. `NOT NULL`
2. `PRIMARY KEY`
3. `UNIQUE`
4. `FOREIGN KEY`
5. `CHECK`
6. `DEFAULT`

---

## 1. NOT NULL Constraint

### 📌 Purpose

Ensures that a column **must have a value**.

### When to use

* Mandatory fields (Name, Email, ID)

---

### Example

```sql
CREATE TABLE Employees (
    EmpID INT NOT NULL,
    EmpName VARCHAR(100) NOT NULL
);
```

### Invalid Insert

```sql
INSERT INTO Employees VALUES (1, NULL);
```

### Error (SSMS)

```
Cannot insert the value NULL into column 'EmpName'
```

---

## 2. PRIMARY KEY Constraint

### 📌 Purpose

* Uniquely identifies each row
* Does **not allow NULL values**
* Only **one PRIMARY KEY per table**

---

### Example

```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY,
    DeptName VARCHAR(100)
);
```

### Insert Data

```sql
INSERT INTO Departments VALUES (1, 'HR');
INSERT INTO Departments VALUES (2, 'IT');
```

### Invalid Insert (Duplicate)

```sql
INSERT INTO Departments VALUES (1, 'Finance');
```

### Error

```
Violation of PRIMARY KEY constraint
```

---

## 3. UNIQUE Constraint

### 📌 Purpose

Prevents **duplicate values** in a column.

### Difference from PRIMARY KEY

* Allows **one NULL value**
* Multiple UNIQUE constraints allowed per table

---

### Example

```sql
CREATE TABLE Users (
    UserID INT,
    Email VARCHAR(150) UNIQUE
);
```

### Valid Inserts

```sql
INSERT INTO Users VALUES (1, 'a@mail.com');
INSERT INTO Users VALUES (2, NULL);
```

### Invalid Insert

```sql
INSERT INTO Users VALUES (3, 'a@mail.com');
```

### Error

```
Violation of UNIQUE KEY constraint
```

---

## 4. FOREIGN KEY Constraint

### 📌 Purpose

Maintains **referential integrity** between two tables.

### Rule

* Child column must reference a **PRIMARY KEY or UNIQUE** column in parent table.

---

### Example

#### Parent Table

```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY,
    DeptName VARCHAR(100)
);
```

#### Child Table

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    EmpName VARCHAR(100),
    DeptID INT,
    FOREIGN KEY (DeptID) REFERENCES Departments(DeptID)
);
```

### Valid Insert

```sql
INSERT INTO Departments VALUES (1, 'HR');
INSERT INTO Employees VALUES (101, 'John', 1);
```

### Invalid Insert

```sql
INSERT INTO Employees VALUES (102, 'Alice', 5);
```

### Error

```
The INSERT statement conflicted with the FOREIGN KEY constraint
```

---

## 5. CHECK Constraint

### 📌 Purpose

Restricts values based on a **condition**.

### Common Use

* Age limits
* Salary ranges
* Status validation

---

### Example

```sql
CREATE TABLE Customers (
    Age INT CHECK (Age >= 18)
);
```

### Valid Insert

```sql
INSERT INTO Customers VALUES (25);
```

### Invalid Insert

```sql
INSERT INTO Customers VALUES (15);
```

### Error

```
The INSERT statement conflicted with the CHECK constraint
```

---

## 6. DEFAULT Constraint

### 📌 Purpose

Automatically assigns a value **when none is provided**.

---

### Example

```sql
CREATE TABLE Orders (
    OrderID INT,
    OrderDate DATETIME DEFAULT GETDATE(),
    Status VARCHAR(20) DEFAULT 'Pending'
);
```

### Insert Without Defaults

```sql
INSERT INTO Orders (OrderID)
VALUES (1);
```

### Output

```sql
SELECT * FROM Orders;
```

| OrderID | OrderDate               | Status  |
| ------: | ----------------------- | ------- |
|       1 | 2025-01-10 18:40:12.456 | Pending |

---

## 7. Adding Constraints Using ALTER TABLE

### Add PRIMARY KEY

```sql
ALTER TABLE Employees
ADD CONSTRAINT PK_EmpID PRIMARY KEY (EmpID);
```

---

### Add UNIQUE

```sql
ALTER TABLE Users
ADD CONSTRAINT UQ_Email UNIQUE (Email);
```

---

### Add CHECK

```sql
ALTER TABLE Customers
ADD CONSTRAINT CK_Age CHECK (Age >= 18);
```

---

### Add FOREIGN KEY

```sql
ALTER TABLE Employees
ADD CONSTRAINT FK_Dept
FOREIGN KEY (DeptID) REFERENCES Departments(DeptID);
```

---

## 8. Dropping Constraints

```sql
ALTER TABLE Employees
DROP CONSTRAINT PK_EmpID;
```

📌 Constraint names can be seen in **Object Explorer → Keys / Constraints**

---

## 9. Constraints Summary Table

| Constraint  | Allows NULL | Allows Duplicate | Purpose            |
| ----------- | ----------- | ---------------- | ------------------ |
| NOT NULL    | ❌           | ✅                | Mandatory value    |
| PRIMARY KEY | ❌           | ❌                | Row identification |
| UNIQUE      | ✅ (1)       | ❌                | Prevent duplicates |
| FOREIGN KEY | ✅           | ✅                | Relationship       |
| CHECK       | ✅           | ✅                | Value validation   |
| DEFAULT     | ✅           | ✅                | Auto value         |

---

## 10.Key Points

<br>✔ PRIMARY KEY = UNIQUE + NOT NULL
<br>✔ FOREIGN KEY enforces relationships
<br>✔ CHECK validates business rules
<br>✔ DEFAULT avoids insert errors
<br>✔ Constraints improve data quality

