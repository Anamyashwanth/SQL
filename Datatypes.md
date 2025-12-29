# DATA TYPES
# SQL Server Data Types (SSMS) 

## 1. INTEGER Data Types

### 📌 What they are

Integer data types store **whole numbers only** (no decimal values). They are commonly used for **IDs, counts, ages, quantities**, and other numeric fields where fractions are not required.

### 📌 When to use

* `INT` → general-purpose numbers
* `SMALLINT` → saves storage for small ranges
* `BIGINT` → very large values like system counters or financial totals

---

### Table Creation

```sql
CREATE TABLE EmployeeNumbers (
    EmpID INT,
    Age SMALLINT,
    CompanyAssets BIGINT
);
```

### Insert Data

```sql
INSERT INTO EmployeeNumbers VALUES (101, 25, 9000000000);
```

### Output

```sql
SELECT * FROM EmployeeNumbers;
```

| EmpID | Age | CompanyAssets |
| ----: | --: | ------------: |
|   101 |  25 |    9000000000 |

---

## 2. DECIMAL & FLOAT Data Types

### 📌 What they are

These data types store **numbers with decimal points**. SQL Server provides **exact precision** (`DECIMAL`) and **approximate precision** (`FLOAT`).

### 📌 Key Difference

* `DECIMAL` → **exact values**, no rounding errors
* `FLOAT` → **approximate**, faster but not precise

### 📌 Real-world usage

* `DECIMAL` → salary, balance, price
* `FLOAT` → scientific data, measurements, temperature

---

### Table Creation

```sql
CREATE TABLE SalaryDetails (
    Salary DECIMAL(10,2),
    Bonus FLOAT
);
```

### Insert Data

```sql
INSERT INTO SalaryDetails VALUES (55000.75, 1200.5);
```

### Output

```sql
SELECT * FROM SalaryDetails;
```

|   Salary |  Bonus |
| -------: | -----: |
| 55000.75 | 1200.5 |

📌 `DECIMAL(10,2)` = total **10 digits**, **2 after decimal**

---

## 3. STRING Data Types (CHAR & VARCHAR)

### 📌 What they are

String data types store **text, names, codes, and descriptions**.

### 📌 Key Difference

* `CHAR(n)` → fixed length (pads extra spaces)
* `VARCHAR(n)` → variable length (saves space)

### 📌 Real-world usage

* `CHAR` → country codes, gender, status flags
* `VARCHAR` → names, emails, usernames

---

### Table Creation

```sql
CREATE TABLE UserInfo (
    CountryCode CHAR(3),
    UserName VARCHAR(50)
);
```

### Insert Data

```sql
INSERT INTO UserInfo VALUES ('USA', 'John Smith');
```

### Output

```sql
SELECT * FROM UserInfo;
```

| CountryCode | UserName   |
| ----------- | ---------- |
| USA         | John Smith |

---

## 4. DATE & TIME Data Types

### 📌 What they are

Used to store **date-only**, **time-only**, or **combined date & time** values.

### 📌 Why SQL Server separates them

This improves **storage efficiency** and **query performance**.

### 📌 Real-world usage

* `DATE` → birthdays, order dates
* `TIME` → working hours
* `DATETIME` → logs, audit records

---

### Table Creation

```sql
CREATE TABLE OrderDates (
    OrderDate DATE,
    OrderTime TIME,
    CreatedAt DATETIME
);
```

### Insert Data

```sql
INSERT INTO OrderDates 
VALUES ('2025-01-10', '14:30:00', '2025-01-10 14:30:00');
```

### Output

```sql
SELECT * FROM OrderDates;
```

| OrderDate  | OrderTime | CreatedAt               |
| ---------- | --------- | ----------------------- |
| 2025-01-10 | 14:30:00  | 2025-01-10 14:30:00.000 |

---

## 5. BOOLEAN (BIT) Data Type

### 📌 What it is

SQL Server does **not support BOOLEAN** directly.
Instead, it uses the `BIT` data type.

### 📌 Values allowed

* `1` → TRUE
* `0` → FALSE
* `NULL` → Unknown

### 📌 Real-world usage

* Active / Inactive
* Yes / No
* Verified / Not Verified

---

### Table Creation

```sql
CREATE TABLE AccountStatus (
    IsActive BIT
);
```

### Insert Data

```sql
INSERT INTO AccountStatus VALUES (1);
```

### Output

```sql
SELECT * FROM AccountStatus;
```

| IsActive |
| -------: |
|        1 |

---

## 6. AUTO-INCREMENT (IDENTITY)

### 📌 What it is

`IDENTITY` automatically generates **unique numeric values** for each row.

### 📌 Why it is important

* Eliminates manual ID management
* Ensures uniqueness
* Commonly used as **Primary Keys**

---

### Table Creation

```sql
CREATE TABLE Products (
    ProductID INT IDENTITY(1,1) PRIMARY KEY,
    ProductName VARCHAR(100)
);
```

### Insert Data

```sql
INSERT INTO Products (ProductName)
VALUES ('Laptop'), ('Mouse');
```

### Output

```sql
SELECT * FROM Products;
```

| ProductID | ProductName |
| --------: | ----------- |
|         1 | Laptop      |
|         2 | Mouse       |

---

## 7. BINARY Data Types

### 📌 What they are

Binary data types store **raw binary data** such as files, images, encrypted values, or hashes.

### 📌 Common types in SQL Server

* `VARBINARY(n)`
* `VARBINARY(MAX)`

### 📌 Real-world usage

* File storage
* Password hashes
* Encrypted columns

---

### Table Creation

```sql
CREATE TABLE Files (
    FileData VARBINARY(MAX)
);
```

### Insert Data

```sql
INSERT INTO Files VALUES (CAST('Hello' AS VARBINARY));
```

### Output

```sql
SELECT * FROM Files;
```

| FileData     |
| ------------ |
| 0x48656C6C6F |

📌 Output is shown in **hexadecimal format**

---

## 8. COMPLETE REAL-WORLD TABLE (SSMS)

### 📌 Purpose

This table combines **multiple data types** used in real applications.

---

```sql
CREATE TABLE Customers (
    CustomerID INT IDENTITY(1,1) PRIMARY KEY,
    FullName VARCHAR(100),
    Email VARCHAR(150),
    Age INT,
    Balance DECIMAL(12,2),
    IsVerified BIT,
    CreatedAt DATETIME
);
```

### Insert Data

```sql
INSERT INTO Customers
VALUES ('Alice Brown', 'alice@mail.com', 30, 2500.75, 1, GETDATE());
```

### Output

```sql
SELECT * FROM Customers;
```

| CustomerID | FullName    | Email                                   | Age | Balance | IsVerified | CreatedAt               |
| ---------: | ----------- | --------------------------------------- | --: | ------: | ---------: | ----------------------- |
|          1 | Alice Brown | [alice@mail.com](mailto:alice@mail.com) |  30 | 2500.75 |          1 | 2025-01-10 15:12:45.123 |

---

## 9. SQL Server Best Practices (SSMS)

✔ Use `BIT` for boolean logic
✔ Use `IDENTITY` for surrogate keys
✔ Prefer `VARCHAR` over `NVARCHAR` unless Unicode is required
✔ Avoid deprecated `TEXT` → use `VARCHAR(MAX)`
✔ Match data type to real-world meaning


