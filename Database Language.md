## Database Languages
**DDL**      
DDL stands for data definition language which deals with database schemas and descriptions, of how the data should reside in the database.

1. **CREATE**   – Creates database objects (table, view, index, procedure, function, trigger)
2. **ALTER**    – Modifies the structure of existing objects
3. **DROP**     – Permanently removes a database object
4. **TRUNCATE** – Removes all rows from a table (faster than DELETE)
5. **sp_rename**– Renames database objects


**DML**

DML is the short name for Data Manipulation Language which deals with data manipulation and includes most common SQL statements such SELECT, INSERT, UPDATE, DELETE, etc., and it is used to store, modify, retrieve, delete and update data in a database. Data query language(DQL) is the subset of “Data Manipulation Language”. The most common command of DQL is SELECT statement. SELECT statement help on retrieving the data from the table without changing anything in the table.

1. **SELECT (DQL):** Retrieves data from one or more tables in a database.
2. **INSERT (DML):** Inserts new records (rows) into a table.
3. **UPDATE (DML):** Modifies existing records in a table.
4. **DELETE (DML):** Deletes records from a table.  
   - Can delete specific rows using a `WHERE` clause  
   - Deletes all rows if `WHERE` is omitted
5. **MERGE (DML):** Performs an **UPSERT** operation (inserts new records or updates existing records based on a condition).


**Data Control Language (DCL)**

DCL is short for Data Control Language which acts as an access specifier to the database.(basically to grant and revoke permissions to users in the database

1. **GRANT (DCL):**  
   Used to grant permissions to a user or role to perform DML operations  
   such as `SELECT`, `INSERT`, `UPDATE`, and `DELETE` on a database object.

2. **REVOKE (DCL):**  
   Used to remove (revoke) previously granted permissions from a user or role  
   on a specified database object.

**Transactional Control Language (TCL)**

TCL is short for Transactional Control Language which acts as an manager for all types of transactional data and all transactions. Some of the command of TCL are

1. **Roll Back:** Used to cancel  or Undo changes made in the database.
2. **Commit:** It is used to apply or save changes in the database.
3. **Save Point:** It is used to save the data on the temporary basis in the database.
   

