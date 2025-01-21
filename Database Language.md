## Database Languages
**DDL**      
DDL stands for data definition language which deals with database schemas and descriptions, of how the data should reside in the database.

1. **CREATE:** to create a database and its objects like (table, index, views, store procedure, function, and triggers).
2. **ALTER:** To change the structure of the table.
3. **Drop:** To remove all objects from the database.
4. **TRUNCATE:** To remove all records and empty spaces from the table.
5. **RENAME:** To Rename the objects.
6. **Comment:** Add comments to the data dictionary.

**DML**

DML is the short name for Data Manipulation Language which deals with data manipulation and includes most common SQL statements such SELECT, INSERT, UPDATE, DELETE, etc., and it is used to store, modify, retrieve, delete and update data in a database. Data query language(DQL) is the subset of “Data Manipulation Language”. The most common command of DQL is SELECT statement. SELECT statement help on retrieving the data from the table without changing anything in the table.

1. SELECT: retrieve data from a database.
2. INSERT: insert data into a table.
3. UPDATE: updates existing data within a table.
4. DELETE: Delete all records from a database table.
5. MERGE: UPSERT operation (insert or update).
6. CALL: call a PL/SQL or Java subprogram.
7. EXPLAIN PLAN: interpretation of the data access path.
8. LOCK TABLE: concurrency Control.

**Data Control Language (DCL)**

DCL is short for Data Control Language which acts as an access specifier to the database.(basically to grant and revoke permissions to users in the database

1. GRANT: grant permissions to the user for running DML(SELECT, INSERT, DELETE,…) commands on the table.
2. REVOKE: revoke permissions to the user for running DML(SELECT, INSERT, DELETE,…) command on the specified table.

**Transactional Control Language (TCL)**

TCL is short for Transactional Control Language which acts as an manager for all types of transactional data and all transactions. Some of the command of TCL are

1. Roll Back: Used to cancel  or Undo changes made in the database.
2. Commit: It is used to apply or save changes in the database.
3. Save Point: It is used to save the data on the temporary basis in the database.
   

