
# 🚀A.C.I.D. Properties in SQL

## What is a Transaction?
![[Pasted image 20250803182131.png]]
### 1. **Atomicity**
![[Pasted image 20250803181804.png]]
> ✅ _All or nothing_

- A transaction is **atomic**, meaning **either all of its operations succeed or none do**.
    
- If any part of the transaction fails, the entire transaction is **rolled back**.
    

🧠 **Example:**

```sql
START TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;
COMMIT;
```

If the second update fails (e.g., account 2 doesn't exist), the first update is also undone.

---

### 2. **Consistency**
![[Pasted image 20250803181823.png]]
![[Pasted image 20250803181839.png]]

> ✅ _Database stays valid before & after_

- A transaction brings the database from **one valid state to another**.
    
- It ensures that all **rules, constraints, and triggers** are respected.
    

🧠 **Example:**

- If `balance` in a bank account must never be negative, a transaction trying to overdraw must fail.
    

---

### 3. **Isolation**
![[Pasted image 20250803181906.png]]
> ✅ _Transactions don’t interfere with each other_

- Multiple transactions can occur **simultaneously** without affecting each other’s outcome.
    
- SQL uses **isolation levels** (like `READ COMMITTED`, `REPEATABLE READ`, `SERIALIZABLE`) to control visibility of data during a transaction.
    

🧠 **Example:**

- Two users transferring money at the same time won't corrupt each other’s data.
    

---

### 4. **Durability**
![[Pasted image 20250803181933.png]]
> ✅ _Data is permanent after commit_

- Once a transaction is **committed**, the data is **permanently saved**, even in case of power failure or crash.
    
- It’s written to **non-volatile storage** (like disk).
    

🧠 **Example:**

- After a successful money transfer, even a sudden server crash won’t undo it.
    

---

## 🔁 Summary Table:

|Property|What it Ensures|
|---|---|
|**Atomicity**|All operations in a transaction complete or none|
|**Consistency**|Database remains valid before and after|
|**Isolation**|Transactions don’t affect each other|
|**Durability**|Changes persist after commit|

---

## 🔍 **Why ACID is Important**

### 1. 🧨 **Prevents Data Corruption**

- Imagine your app crashes while transferring ₹1,000 between accounts.
    
- Without **atomicity**, ₹1,000 might get deducted but not credited.
    
- With ACID, the database rolls back incomplete transactions — so your data isn't corrupted.
    

---

### 2. 🔒 **Maintains Accuracy (Consistency)**

- Databases have rules like “no duplicate IDs”, “email can’t be NULL”, or “balance can’t go negative”.
    
- **Consistency** ensures these rules are always enforced, even after complex operations.
    

---

### 3. 🕵️‍♂️ **Allows Safe Multi-User Access (Isolation)**

- In real-world apps, hundreds of users access the database at once.
    
- **Isolation** ensures that one user's transaction doesn’t mess up another’s.
    

**Example:**

- Two people booking the last train ticket at the same time — isolation prevents double booking.
    

---

### 4. 💾 **Guarantees Permanent Changes (Durability)**

- After a successful transaction, data **stays saved**, even if:
    
    - The server shuts down
        
    - The power goes out
        
    - The app crashes
        
- This builds **trust** in your system — users know their actions won’t be lost.
    

---

## ✅ Real-Life Applications of ACID

|Scenario|What ACID Ensures|
|---|---|
|💸 Bank Transfers|Money doesn't disappear or duplicate|
|🛒 Online Shopping|No over-selling, duplicate orders|
|📝 Exam Portals|Answer sheets are saved correctly|
|🚀 Airline Ticketing|Avoids double-booked seats|
|🏦 Finance Systems|Committed transactions are always traceable|

---

## 🧠 Without ACID, You Risk:

- Data corruption 🧨
    
- Lost customer trust 😤
    
- Security breaches 🔓
    
- Logical bugs that are hard to trace 🐞
    

---

### In short:

**ACID is the backbone of reliable, secure, and accurate database operations.**


# 🚀Normalization in SQL
##  **Definition of Normalization (in SQL)**

**Normalization** is the process of structuring a relational database in a way that:

- **Minimizes data redundancy**
    
- **Eliminates undesirable anomalies** (Insert, Update, Delete)[ A **data anomaly** refers to **inconsistencies or errors** that occur when data is **inserted, updated, or deleted** in a poorly structured database—**especially one that is not normalized properly**. ]
    
- **Improves data integrity**[Data integrity means making sure the data in your database is **correct**, **unchanged unless intended**, and **logically valid** at all times.]
    
- Makes relationships between tables clear and efficient
    

---

## 🔍 **Why Normalization Is Needed**

Imagine you're storing data in a single table like this:

|Student_ID|Name|Course_1|Course_2|Instructor_1|Instructor_2|
|---|---|---|---|---|---|
|101|Achyuth|DBMS|Networks|Mr. Ravi|Ms. Riya|

### Problems:

- Repeated data → **Redundancy**
    
- If a student takes 3+ courses, we must add columns → **Scalability issue**
    
- If Instructor_1 leaves, we must update everywhere → **Update anomaly**
    
- Can’t store a course without a student → **Insert anomaly**
    
- Deleting a student deletes course info too → **Delete anomaly**
    

These are exactly what **Normalization fixes.**

---

## 📚 **Goals of Normalization**

1. Divide larger tables into **smaller related tables**
    
2. Ensure that **each table represents one subject** (like Customers, Orders, Products)
    
3. Use **foreign keys** to maintain relationships
    
4. Eliminate **redundant (duplicate) data**
    
5. Ensure data is **logically stored**
    

---

## 🔢 **Normal Forms (NF)** Explained

Each stage in normalization is called a **normal form**. You go from 1NF → 2NF → 3NF → BCNF → 4NF → 5NF...

Let’s understand each with examples.

---

### 🔴 **1NF – First Normal Form**
![[Pasted image 20250803193905.png]]
> A table is in 1NF if:

- All columns contain **atomic values** (indivisible)
    
- Each record is **unique**
    

🚫 **Bad Table (Not 1NF):**

|ID|Name|Courses|
|---|---|---|
|1|Ajay|Math, Physics|

✅ **Good Table (1NF):**

|ID|Name|Course|
|---|---|---|
|1|Ajay|Math|
|1|Ajay|Physics|
![[Pasted image 20250803193954.png]]
![[Pasted image 20250803194009.png]]
---

### 🟡 **2NF – Second Normal Form**
![[Pasted image 20250803194026.png]]

> A table is in 2NF if:

- It is already in 1NF
    
- **Every non-key column is fully dependent** on the entire primary key
    

📌 **Applies only to composite keys**

🚫 Example of **Partial Dependency**:

|StudentID|CourseID|Name|CourseName|
|---|---|---|---|

- `Name` depends only on `StudentID`, not `CourseID`
    

✅ **Solution: Split into:**

**Students Table:**

|StudentID|Name|
|---|---|
|1|Ajay|

**Courses Table:**

|CourseID|CourseName|
|---|---|
|C1|Math|

**Enrollments:**

|StudentID|CourseID|
|---|---|
|1|C1|
![[Pasted image 20250803194120.png]]
![[Pasted image 20250803194157.png]]
---

### 🟢 **3NF – Third Normal Form**
![[Pasted image 20250803194418.png]]
> A table is in 3NF if:

- It is already in 2NF
    
- All fields are **only dependent on the primary key**, not on other non-key fields (i.e., no transitive dependencies)
    

🚫 **Bad (Transitive dependency):**

|OrderID|CustomerID|CustomerName|
|---|---|---|

Here `CustomerName` depends on `CustomerID`, not directly on `OrderID`

✅ **Fix by splitting:**

**Orders Table:**

| OrderID | CustomerID |
| ------- | ---------- |

**Customers Table:**

| CustomerID | CustomerName |

![[Pasted image 20250803194505.png]]
![[Pasted image 20250803194557.png]]

---

### 🔵 **BCNF – Boyce-Codd Normal Form**
![[Pasted image 20250803194635.png]]
> A stronger version of 3NF. Used when:

- A table has **more than one candidate key**
    
- Non-trivial functional dependencies violate 3NF
    

> Rare in beginner DBs; used in complex designs.

---

## 💡 **Practical Example**

**Before Normalization:**

|EmpID|Name|Department|Dept_Location|
|---|---|---|---|
|1|A|IT|2nd Floor|
|2|B|IT|2nd Floor|

Problems:

- Redundant department info
    
- If IT moves to another floor → must update everywhere
    

**After Normalization:**

**Employees Table:**

|EmpID|Name|DeptID|
|---|---|---|
|1|A|D1|

**Departments Table:**

|DeptID|Department|Location|
|---|---|---|
|D1|IT|2nd Floor|
![[Pasted image 20250803194728.png]]
![[Pasted image 20250803194819.png]]

---

## ✅ **Advantages of Normalization**

|Benefit|Description|
|---|---|
|Less Redundancy|Data isn't repeated unnecessarily|
|Improved Consistency|Data is stored and updated in one place only|
|Easier Maintenance|Adding/removing/updating data is cleaner|
|Saves Space|Smaller tables use less storage|
|Increases Integrity|Relationships are enforced through foreign keys|

---

## ⚠️ **Trade-offs**

- **Too much normalization = too many joins** = slower queries
    
- In reporting/data warehouses, **denormalized** data is often used
    

---

## 🧠 Summary

|Normal Form|Fixes|Key Idea|
|---|---|---|
|1NF|Repeating columns|Atomic data|
|2NF|Partial dependencies|All fields depend on full key|
|3NF|Transitive dependencies|Fields depend only on PK|
|BCNF|Complex key-based anomalies|Advanced dependency management|

---

# 🚀What is **Denormalization** in SQL?

**Denormalization** is the process of _intentionally adding redundancy_ to a database by combining normalized tables into larger tables to **improve read performance** at the cost of **data integrity and storage**.

---

## ✅ **Definition**:

> Denormalization is a database optimization technique where normalized tables are merged to reduce complex joins and improve query performance.

---

## 🧠 Why Denormalize?

While **normalization** helps avoid data redundancy and maintain consistency, it often requires:

- **Multiple joins** for retrieving data.
    
- Slower **read performance** in complex queries.
    

So when speed matters more than strict normalization, **denormalization is used**—especially in:

- Reporting dashboards
    
- Analytics systems
    
- Read-heavy applications
    

---

## 📌 When to Use Denormalization

|Use Case|Why Denormalize?|
|---|---|
|Read-heavy systems|Fewer joins → faster queries|
|Precomputed values needed|Store totals or calculated fields|
|Simplify complex queries|Reduce complexity for developers|
|Avoid frequent joins|Better performance with large datasets|
|OLAP systems|For quick analytical processing|

---

## 🎯 **Example**

### 🔹 Normalized Structure:

You have two tables:

#### `Orders` Table

|order_id|customer_id|order_date|
|---|---|---|
|1|101|2023-01-01|
|2|102|2023-01-05|

#### `Customers` Table

|customer_id|customer_name|
|---|---|
|101|Alice|
|102|Bob|

To get the customer name with each order, you must `JOIN`:

```sql
SELECT o.order_id, c.customer_name
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;
```

---

### 🔹 Denormalized Structure:

You merge customer name directly into `Orders`:

#### `Orders` Table (denormalized)

|order_id|customer_id|customer_name|order_date|
|---|---|---|---|
|1|101|Alice|2023-01-01|
|2|102|Bob|2023-01-05|

Now you can get customer names **without any JOINs**, which is faster.

---

## ⚖️ **Pros and Cons of Denormalization**

### ✅ Advantages:

- **Faster reads** – No need to join many tables.
    
- **Simpler queries** – Reduces query logic for reporting.
    
- **Better performance** – Especially in data warehouses or analytics.
    

### ❌ Disadvantages:

- **Redundant data** – Wastes space.
    
- **Update anomalies** – Hard to maintain consistency.
    
- **Data integrity issues** – Risk of mismatched or outdated values.
    

---

## 🚀 Practical Use Cases:

- Business Intelligence dashboards
    
- Pre-aggregated data reports
    
- Materialized views
    
- OLAP systems (e.g., star schema, snowflake schema)
    

---

## 🧩 Denormalization vs Normalization Summary:

|Aspect|Normalization|Denormalization|
|---|---|---|
|Goal|Minimize redundancy, ensure integrity|Improve performance|
|Query Speed|Slower (more joins)|Faster (fewer joins)|
|Data Redundancy|Low|High|
|Storage Usage|Low|High|
|Data Integrity|High (strict)|Lower (risk of inconsistency)|

---

# 🚀 What Are Constraints?

**Constraints** are **rules** you apply to columns or tables to **enforce data integrity and consistency**.

> Think of them like **guardrails** that ensure only valid, logical, and consistent data gets stored in the database.

---

## 🧩 Types of Constraints in SQL

### 1. **NOT NULL**

Ensures a column **cannot have NULL values**.

```sql
CREATE TABLE users (
  id INT,
  name VARCHAR(100) NOT NULL
);
```

- ✅ You **must** provide a value for `name`.
    

---

### 2. **UNIQUE**

Ensures all values in a column are **different** (no duplicates allowed).

```sql
CREATE TABLE employees (
  emp_id INT,
  email VARCHAR(100) UNIQUE
);
```

- ✅ You can't insert two rows with the same email.
    

---

### 3. **PRIMARY KEY**

- A combination of **NOT NULL** and **UNIQUE**
    
- Uniquely identifies each row in a table
    
- Only one per table
    

```sql
CREATE TABLE customers (
  customer_id INT PRIMARY KEY,
  name VARCHAR(100)
);
```

- ✅ `customer_id` must be unique and not null.
    

---

### 4. **FOREIGN KEY**

- Establishes a **relationship between two tables**
    
- Ensures that the value exists in the **referenced table**
    

```sql
CREATE TABLE orders (
  order_id INT PRIMARY KEY,
  customer_id INT,
  FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

- ✅ You can't insert an `order` unless the `customer_id` exists in the `customers` table.
    

---

### 5. **CHECK**

Validates data **based on a condition**.

```sql
CREATE TABLE students (
  id INT,
  age INT CHECK (age >= 5)
);
```

- ❌ Inserting a student with age `3` will fail.
    

---

### 6. **DEFAULT**

Automatically assigns a value **if none is provided**.

```sql
CREATE TABLE tasks (
  id INT,
  status VARCHAR(20) DEFAULT 'pending'
);
```

- ✅ If `status` is not specified, it defaults to `'pending'`.
    

---

## 🆚 Column-Level vs Table-Level Constraints

|Column-Level|Table-Level|
|---|---|
|Declared **with the column definition**|Declared **after all columns are defined**|
|Good for NOT NULL, DEFAULT, CHECK|Good for FOREIGN KEY, composite PRIMARY KEY, etc.|

#### Example:

```sql
-- Column-level
CREATE TABLE users (
  id INT PRIMARY KEY,
  name VARCHAR(50) NOT NULL
);

-- Table-level
CREATE TABLE orders (
  order_id INT,
  customer_id INT,
  PRIMARY KEY (order_id),
  FOREIGN KEY (customer_id) REFERENCES users(id)
);
```

---

## 🔄 Summary Table

|Constraint|Description|Can Be Null?|Allows Duplicates?|Use Case Example|
|---|---|---|---|---|
|NOT NULL|Field must have a value|❌ No|✅ Yes|Name, Age fields|
|UNIQUE|All values must be different|✅ Yes|❌ No|Email, Username|
|PRIMARY KEY|Unique + Not Null|❌ No|❌ No|User ID, Product ID|
|FOREIGN KEY|References another table|✅ Yes|✅ Yes|Linking orders to customers|
|CHECK|Value must satisfy a condition|✅ Yes|✅ Yes|Age > 18, Salary > 0|
|DEFAULT|Sets a default value|✅ Yes|✅ Yes|Status defaults to ‘pending’|

---

## ⚠️ Important Notes:

- You can combine constraints on the same column.
    

```sql
price DECIMAL(10,2) NOT NULL CHECK (price > 0)
```

- Use `ALTER TABLE` to **add constraints later** if needed.
    

```sql
ALTER TABLE students ADD CONSTRAINT check_age CHECK (age >= 5);
```

---

Want a real-life case study on constraints (like in an eCommerce DB)? Or maybe a small challenge to test this?

# 🚀SQL commands
 four main categories of SQL commands:  
**DML**, **DDL**, **DCL**, and **TCL**—each plays a unique role in interacting with the database.

---

## 📘 1. DML – **Data Manipulation Language**

### 🔹 Definition:

> DML is used to **manipulate data** stored in the database. It handles inserting, updating, deleting, and retrieving records.

### 📋 Common DML Commands:

- `SELECT` – Retrieve data
    
- `INSERT` – Add new data
    
- `UPDATE` – Modify existing data
    
- `DELETE` – Remove data
    

### 🔧 Example:

```sql
-- Add a new customer
INSERT INTO customers (name, email) VALUES ('Achyuth', 'achyuth@gmail.com');

-- Change email for a customer
UPDATE customers SET email = 'achyuthj@gmail.com' WHERE name = 'Achyuth';

-- Delete a customer
DELETE FROM customers WHERE name = 'Achyuth';

-- Fetch all customers
SELECT * FROM customers;
```

### 📌 Notes:

- DML operations **affect the data** in tables, **not the structure**.
    
- Most DML changes are **temporary** until a `COMMIT` is done (transactional behavior).
    

---

## 🏗️ 2. DDL – **Data Definition Language**

### 🔹 Definition:

> DDL is used to **define, alter, or remove** the structure of database objects such as tables, schemas, indexes, etc.

### 📋 Common DDL Commands:

- `CREATE` – Create database objects
    
- `ALTER` – Modify the structure of objects
    
- `DROP` – Delete objects
    
- `TRUNCATE` – Remove all records from a table (faster than DELETE)
    
- `RENAME` – Rename a table
    

### 🔧 Example:

```sql
-- Create a new table
CREATE TABLE users (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

-- Add a new column
ALTER TABLE users ADD age INT;

-- Delete the table
DROP TABLE users;

-- Empty all data in a table
TRUNCATE TABLE users;

-- Rename a table in database
RENAME TABLE employees TO staff;

```

### 📌 Notes:

- DDL statements are **auto-committed** (you can't roll them back).
    
- They **change the structure**, not the data inside.
    

---

## 🔐 3. DCL – **Data Control Language**

### 🔹 Definition:

> DCL is used to **control access to data** in the database. It handles permissions and privileges.

### 📋 Common DCL Commands:

- `GRANT` – Give permissions
    
- `REVOKE` – Remove permissions
    

### 🔧 Example:

```sql
-- Grant SELECT permission to a user
GRANT SELECT ON employees TO 'achyuth'@'localhost';

-- Revoke the permission
REVOKE SELECT ON employees FROM 'achyuth'@'localhost';
```

### 📌 Notes:

- DCL commands control **who can access** or change data.
    
- Permissions can be set for users, roles, or sessions.
    

---

## 🔄 4. TCL – **Transaction Control Language**

### 🔹 Definition:

> TCL manages transactions in the database, ensuring data integrity and consistency.

### 📋 Common TCL Commands:

- `COMMIT` – Save changes permanently
    
- `ROLLBACK` – Undo changes since the last commit
    
- `SAVEPOINT` – Set a save point for partial rollback
    
- `SET TRANSACTION` – Define properties of a transaction (like isolation level)
    

### 🔧 Example:

```sql
-- Start a transaction (implicit in most databases)
UPDATE accounts SET balance = balance - 1000 WHERE id = 1;
UPDATE accounts SET balance = balance + 1000 WHERE id = 2;

-- If everything is fine, commit
COMMIT;

-- If something went wrong
ROLLBACK;

-- Use a savepoint
SAVEPOINT transfer_step1;
UPDATE accounts SET balance = balance - 500 WHERE id = 3;
ROLLBACK TO transfer_step1;
```

### 📌 Notes:

- TCL ensures **ACID properties**.
    
- Only relevant for DML operations (DDL auto-commits).
    

---

## 🧩 Summary Table:

|Category|Full Form|Purpose|Examples|
|---|---|---|---|
|DML|Data Manipulation Language|Manipulate data|`SELECT`, `INSERT`, `UPDATE`, `DELETE`|
|DDL|Data Definition Language|Define/modify structure|`CREATE`, `ALTER`, `DROP`, `TRUNCATE`|
|DCL|Data Control Language|Control user access|`GRANT`, `REVOKE`|
|TCL|Transaction Control Language|Manage transactions|`COMMIT`, `ROLLBACK`, `SAVEPOINT`|

---
# 🚀Relationship in SQL database
In relational databases, **relationships** define how data in one table is related to data in another. There are **three main types** of relationships:

---

## 🔹 1. **One-to-One (1:1)**

### ✅ Definition:

Each row in **Table A** is linked to **one and only one** row in **Table B**, and vice versa.

### 🧠 Use Case:

Used when you want to **split less frequently used data** into a separate table or **store sensitive info** separately.

### 📦 Example:

- **Users Table**
    
    - `user_id`, `name`
        
- **UserDetails Table**
    
    - `user_id`, `phone_number`, `address`
        

Each user has **exactly one** set of details.

```sql
-- Users
| user_id | name   |
|---------|--------|
| 1       | Alice  |

-- UserDetails
| user_id | phone_number | address     |
|---------|--------------|-------------|
| 1       | 9876543210   | Bangalore   |
```

---

## 🔹 2. **One-to-Many (1:N)**

### ✅ Definition:

A single row in **Table A** can be related to **many rows** in **Table B**, but each row in Table B is linked to **only one** row in Table A.

### 🧠 Use Case:

This is the **most common** relationship in databases.

### 📦 Example:

- **Customers Table**
    
    - `customer_id`, `name`
        
- **Orders Table**
    
    - `order_id`, `customer_id`, `order_date`
        

One customer can place **many orders**.

```sql
-- Customers
| customer_id | name    |
|-------------|---------|
| 101         | Ramesh  |

-- Orders
| order_id | customer_id | order_date  |
|----------|--------------|-------------|
| 1        | 101          | 2023-01-01  |
| 2        | 101          | 2023-01-15  |
```

---

## 🔹 3. **Many-to-Many (M:N)**

### ✅ Definition:

A row in **Table A** can be linked to **many rows** in **Table B**, and vice versa.

### 🧠 Use Case:

Use when both sides can have **multiple connections**, and you typically create a **junction (bridge) table**.

### 📦 Example:

- **Students Table**
    
    - `student_id`, `name`
        
- **Courses Table**
    
    - `course_id`, `title`
        
- **Student_Courses Table** (junction table)
    
    - `student_id`, `course_id`
        

One student can take **many courses**, and one course can have **many students**.

```sql
-- Students
| student_id | name     |
|------------|----------|
| 1          | Meera    |

-- Courses
| course_id | title         |
|-----------|---------------|
| 101       | Data Science  |

-- Student_Courses (bridge table)
| student_id | course_id |
|------------|-----------|
| 1          | 101       |
```

---

## 🧩 Summary Table

|Relationship Type|Description|Real-Life Example|
|---|---|---|
|One-to-One|One record ↔ One record|Person ↔ Passport|
|One-to-Many|One record ↔ Many records|Customer ↔ Orders|
|Many-to-Many|Many records ↔ Many records|Students ↔ Courses|

---
# 🚀What are **Aggregate Functions** ?

**Aggregate functions** perform **calculations on a set of values** and return a **single summary value** — often used with `GROUP BY`.

They are **extremely useful** for **reporting, analysis, and summarizing data**.

---

### 🔑 **Common Aggregate Functions:**

|Function|Description|
|---|---|
|`COUNT()`|Returns the number of rows|
|`SUM()`|Returns the total sum of a numeric column|
|`AVG()`|Returns the average value|
|`MIN()`|Returns the smallest value|
|`MAX()`|Returns the largest value|

---

### 🧠 Usage Syntax:

```sql
SELECT AGGREGATE_FUNCTION(column_name)
FROM table_name
WHERE condition;
```

---

### ✅ 1. **COUNT()** – Counts rows

```sql
SELECT COUNT(*) FROM orders;
```

🔹 Counts total number of orders.

---

### ✅ 2. **SUM()** – Adds values

```sql
SELECT SUM(invoice_total) FROM invoices;
```

🔹 Returns the total revenue from invoices.

---

### ✅ 3. **AVG()** – Calculates average

```sql
SELECT AVG(points) FROM customers;
```

🔹 Gets the average reward points earned by customers.

---

### ✅ 4. **MIN() / MAX()** – Finds extremes

```sql
SELECT MIN(invoice_total), MAX(invoice_total)
FROM invoices;
```

🔹 Returns the smallest and largest invoice amounts.

---

### 📦 Real-life Application Scenarios:

|Scenario|Query Example|
|---|---|
|Count how many users signed up|`SELECT COUNT(*) FROM users;`|
|Find total sales by each salesperson|`SELECT salesperson_id, SUM(sales) FROM orders GROUP BY salesperson_id;`|
|Get highest salary per department|`SELECT department_id, MAX(salary) FROM employees GROUP BY department_id;`|
|Calculate average order value|`SELECT AVG(order_total) FROM orders;`|

---

### 🔀 Used With `GROUP BY` (Very Powerful Combo)

```sql
SELECT customer_id, COUNT(*) AS total_orders
FROM orders
GROUP BY customer_id;
```

This gives you the **number of orders placed by each customer**.

---

### 🧩 Summary:

|Feature|Value|
|---|---|
|Used for|Data summarization & reports|
|Output|Single value or grouped rows|
|Works with|`GROUP BY`, `HAVING`|
|Not used for|Row-level manipulation|

---

# 🚀Views ,Stored Procedures and Functions
## 🔹 1. **Views** — _Virtual Tables_

### 🧠 What it is:

A **View** is like a **shortcut** to a complex SQL query.

- It **does not store data** itself.
    
- It shows **real-time data** from existing tables.
    
- You can **query it like a table**, but it's based on a **SELECT** statement.
    

### 💡 Think of it like:

A **custom filter or lens** over a table. Like a saved Instagram filter on top of your photo feed.

### 📦 Example:

Suppose you have a table:

```sql
CREATE TABLE customers (
  customer_id INT,
  name VARCHAR(50),
  points INT
);
```

And you want to frequently see **customers who have more than 3000 points**.

Instead of writing:

```sql
SELECT name, points FROM customers WHERE points > 3000;
```

You can **create a View**:

```sql
CREATE VIEW gold_customers AS
SELECT name, points
FROM customers
WHERE points > 3000;
```

Now, just do:

```sql
SELECT * FROM gold_customers;
```

It will always show **updated results**, just like a live shortcut.

---

## 🔹 2. **Stored Procedures** — _Saved SQL Tasks_

### 🧠 What it is:

A **Stored Procedure** is a **set of SQL commands** you save with a name.

- You **call it** whenever needed.
    
- It can take **inputs** and **do multiple tasks**.
    

### 💡 Think of it like:

A **reusable function** in code — like a **macro** that performs a task.

### 📦 Example:

Let’s say you often want to **get details of a customer by ID**:

```sql
DELIMITER //

CREATE PROCEDURE GetCustomerDetails(IN cid INT)
BEGIN
  SELECT name, points
  FROM customers
  WHERE customer_id = cid;
END //

DELIMITER ;
```

To use it:

```sql
CALL GetCustomerDetails(1);
```

✅ You don’t have to rewrite the SELECT each time. Just reuse the stored procedure.

---

## 🔹 3. **Functions** — _Return a Single Value_

### 🧠 What it is:

A **Function** in SQL is like a stored procedure but it must **return one value**.

- You can use it inside `SELECT`, `WHERE`, etc.
    
- It’s perfect for **calculations or transformations**.
    

### 💡 Think of it like:

A **calculator** that returns one answer based on your input.

### 📦 Example:

You want to **add 18% tax** to any price.

Create this function:

```sql
DELIMITER //

CREATE FUNCTION AddTax(amount DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
  RETURN amount * 1.18;
END //

DELIMITER ;
```

Now, you can do:

```sql
SELECT AddTax(1000);  -- Output: 1180.00
```

Or even:

```sql
SELECT name, AddTax(price) AS final_price
FROM products;
```

---

## 🧩 Differences Made Simple:

|Feature|View|Stored Procedure|Function|
|---|---|---|---|
|What is it?|Virtual table|Saved SQL task|Calculation that returns value|
|Can take input?|❌ No|✅ Yes|✅ Yes|
|Returns what?|Table-like result|Table or none|Single value|
|Use inside SELECT?|✅ Yes|❌ No (must use `CALL`)|✅ Yes|
|Use case|Filter data easily|Reuse complex operations|Return computed values|

---

### ✅ Summary:

- Use **Views** for creating reusable filters of data.
    
- Use **Stored Procedures** when you want to automate tasks or handle inputs.
    
- Use **Functions** when you need to return a calculated value.
    


# 🚀`GROUP BY` and `HAVING` clause
## 🔹 What is `GROUP BY` in SQL?

### ✅ Definition:

`GROUP BY` is used to **group rows that have the same values** in one or more columns. It is usually used **with aggregate functions** like:

- `COUNT()`
    
- `SUM()`
    
- `AVG()`
    
- `MAX()`
    
- `MIN()`
    

### 💡 Think of it like:

"Group all orders **by customer** and show total amount they spent."

---

### 📦 Example:

Let's say we have this table `orders`:

|order_id|customer_id|amount|
|---|---|---|
|1|101|500|
|2|102|800|
|3|101|300|
|4|103|1000|

We want to know **how much each customer spent in total**:

```sql
SELECT customer_id, SUM(amount) AS total_spent
FROM orders
GROUP BY customer_id;
```

🧾 Output:

|customer_id|total_spent|
|---|---|
|101|800|
|102|800|
|103|1000|

---

## 🔹 What is `HAVING` in SQL?

### ✅ Definition:

`HAVING` is **used to filter grouped data**, just like `WHERE` is used to filter rows **before grouping**.

> You can’t use aggregate functions in `WHERE`, but you **can** in `HAVING`.

---

### 📦 Example:

Let’s extend the previous example.

Now you want to **see only those customers who spent more than ₹800**.

```sql
SELECT customer_id, SUM(amount) AS total_spent
FROM orders
GROUP BY customer_id
HAVING total_spent > 800;
```

🧾 Output:

|customer_id|total_spent|
|---|---|
|103|1000|

---

## 🧠 Summary Table

|Clause|Works on...|Used for...|
|---|---|---|
|`WHERE`|Individual rows|Filter data **before grouping**|
|`GROUP BY`|Groups of rows|Grouping rows based on column values|
|`HAVING`|Groups of data|Filtering groups **after aggregation**|

---

### 🎯 Real-World Use Case Example:

Suppose you have an `invoices` table and want to find:

> All clients who made **more than 3 payments** in total.

```sql
SELECT client_id, COUNT(payment_id) AS total_payments
FROM payments
GROUP BY client_id
HAVING total_payments > 3;
```

---


# 🚀**What is Indexing in SQL?**

**Indexing** is a **database optimization technique** used to speed up the retrieval of rows from a table.

Think of it like the index of a book:  
Instead of scanning every page to find a topic, you look it up in the index and go directly to the right page.

**Without an index**:  
When you search for data, SQL performs a **full table scan** (reads every row).

**With an index**:  
SQL jumps directly to the location of the desired data, **just like searching a dictionary**.

---

## ✅ **Use Case of Indexing**

- **Faster data retrieval** for `SELECT` queries.
    
- Used when filtering with `WHERE`, joining tables with `JOIN`, or sorting with `ORDER BY`.
    

---

## 📦 **Types of Indexes in SQL**

1. ### 🔹 **Single-column Index**
    
    - Created on a **single column**.
        
    - Useful when queries filter using **only that column**.
        
    
    **Example**:
    
    ```sql
    CREATE INDEX idx_employee_name ON employees(name);
    ```
    
    Now queries like:
    
    ```sql
    SELECT * FROM employees WHERE name = 'John';
    ```
    
    will be faster.
    

---

2. ### 🔹 **Composite (Multi-column) Index**
    
    - Created on **multiple columns**.
        
    - Helps when queries use **those columns together**.
        
    
    **Example**:
    
    ```sql
    CREATE INDEX idx_emp_name_dept ON employees(name, department_id);
    ```
    
    This index helps:
    
    ```sql
    SELECT * FROM employees WHERE name = 'Alice' AND department_id = 2;
    ```
    
    ⚠️ **Order matters!**  
    The index will **not** help for:
    
    ```sql
    SELECT * FROM employees WHERE department_id = 2;
    ```
    

---

3. ### 🔹 **Unique Index**
    
    - Ensures **no duplicate values** in the column(s).
        
    - Used to enforce **data integrity**.
        
    
    **Example**:
    
    ```sql
    CREATE UNIQUE INDEX idx_email ON users(email);
    ```
    
    This prevents two users from having the same email.
    

---

4. ### 🔹 **Primary Key Index**
    
    - Automatically created when you define a `PRIMARY KEY`.
        
    - It's a **unique** index and cannot have `NULL`.
        
    
    **Example**:
    
    ```sql
    CREATE TABLE employees (
      id INT PRIMARY KEY,
      name VARCHAR(100)
    );
    ```
    

---

5. ### 🔹 **Clustered Index (In MySQL: only 1 per table)**
    
    - The **actual table data is stored in the index**.
        
    - **Only one** clustered index per table (typically the primary key).
        
    
    **Use case**: Fast retrieval by primary key.
    

---

6. ### 🔹 **Non-clustered Index**
    
    - Stores a **pointer** to the actual data row.
        
    - You can have **many non-clustered indexes**.
        
    
    **Example**:
    
    ```sql
    CREATE INDEX idx_salary ON employees(salary);
    ```
    

---

7. ### 🔹 **Full-Text Index**
    
    - Used for **searching words or phrases** in large text fields (like blog posts, descriptions).
        
    - Supports searching with `MATCH ... AGAINST`.
        
    
    **Example**:
    
    ```sql
    CREATE FULLTEXT INDEX idx_content ON articles(content);
    ```
    
    Then:
    
    ```sql
    SELECT * FROM articles WHERE MATCH(content) AGAINST('MySQL indexing');
    ```
    

---

## ⚙️ **How Indexing Works Internally (In Simple Terms)**

- Most indexes use a **B-Tree structure** (like a balanced tree).
    
- Searching in a B-Tree is **logarithmic**, i.e., **fast even with millions of records**.
    
- Index points to **row locations** in memory or disk, so retrieval is direct.
    

---

## ⚠️ **When Not to Use Indexes**

1. On columns with **very few unique values** (e.g., gender = 'M' or 'F').
    
2. On **frequently updated columns** – too many index updates slow down `INSERT/UPDATE/DELETE`.
    
3. On **small tables** – full scan is faster than index lookup.
    

---

## 📉 Drawbacks of Indexing

- **Slower INSERTs/UPDATEs** – Every time you add or modify data, indexes also get updated.
    
- **More storage** – Indexes occupy space.
    
- **Improper use can degrade performance**.
    

---

## 🧠 Example Use Case Summary

### Table: `orders`

|order_id|customer_id|order_date|total_amount|
|---|---|---|---|
|101|1001|2024-01-01|2500|
|102|1002|2024-01-02|500|

---

### ❌ Without Index:

```sql
SELECT * FROM orders WHERE customer_id = 1002;
```

- Full scan of all rows.
    

---

### ✅ With Index:

```sql
CREATE INDEX idx_customer_id ON orders(customer_id);
```

- Engine jumps directly to rows with `customer_id = 1002`.
    

---

## 💡 Real-World Analogy

- **Without Index** = Searching for a word in a dictionary by reading each page.
    
- **With Index** = Using the alphabetical index to jump straight to the word.
    

---

# 🚀Clustered VS Non-Clustered Indexing

## 🔥 First, What is Indexing? (Again, quick recap)

Indexing is like creating a **shortcut** to find data faster in a database.

Without index = the DB reads **every row** to find the data = **slow**.

With index = DB uses a **map** to directly jump to the data = **fast**.

---

## 🧱 What is a Clustered Index?

### 🧠 Simple Meaning:

- A **clustered index sorts and stores the actual data rows in order** based on the indexed column.
    
- The **data itself is physically arranged** in the storage based on that column.
    
- There can be **only one** clustered index because the data can be sorted in only one way.
    

---

### 📦 Example:

Imagine a table called `Students`:

|RollNo|Name|Marks|
|---|---|---|
|102|Alice|85|
|101|Bob|78|
|104|Charlie|92|

Now if you create a **clustered index on RollNo**:

```sql
CREATE CLUSTERED INDEX idx_rollno ON Students(RollNo);
```

The table is now **physically arranged like this**:

|RollNo|Name|Marks|
|---|---|---|
|101|Bob|78|
|102|Alice|85|
|104|Charlie|92|

So when you search `WHERE RollNo = 102`, the DB knows exactly where to find it, because the data is **already sorted** by `RollNo`.

---

### 🔍 Real Life Example:

Like a **dictionary** – the words (data) are **sorted alphabetically**. So if you're looking for "Laptop", you directly jump to "L" section.

> That’s clustered index. Data is **stored in order** of the index.

---

## 🚚 What is a Non-Clustered Index?

### 🧠 Simple Meaning:

- A **non-clustered index is a separate structure** from the data.
    
- It contains **only the column values + pointers** (like memory addresses) to the actual rows in the main table.
    
- The **data itself stays unsorted**, but the index is sorted.
    
- You can create **many non-clustered indexes** on different columns.
    

---

### 📦 Example:

Same `Students` table again:

|RollNo|Name|Marks|
|---|---|---|
|102|Alice|85|
|101|Bob|78|
|104|Charlie|92|

Now create a non-clustered index on `Marks`:

```sql
CREATE INDEX idx_marks ON Students(Marks);
```

The index looks like this (sorted):

```
Marks   | Pointer to row
--------|----------------
78      | → Bob (Row 2)
85      | → Alice (Row 1)
92      | → Charlie (Row 3)
```

So when you run:

```sql
SELECT * FROM Students WHERE Marks = 85;
```

It looks up 85 in the index, finds the pointer → and goes to the actual row.

---

### 🔍 Real Life Example:

Like a **book index at the back** – "Photosynthesis → Page 52".

But the actual content is on Page 52. So index helps you **find where** the data is.

> That’s non-clustered index. **Pointer-based shortcut** to reach the data.

---

## 🎯 Key Differences (Super Simple Table):

|Feature|Clustered Index|Non-Clustered Index|
|---|---|---|
|🧱 Data Sorted|Yes, actual table is sorted|No, separate index with pointers|
|🔁 How Many Allowed?|Only **one** per table|**Many** allowed|
|📍 Data Location|Stored inside the index itself|Stored **separately**, index just points to data|
|⚡ Fast For|Primary key search, range queries|Frequent filters like `WHERE`, `JOIN`, `ORDER BY`|
|🧠 Analogy|Dictionary with sorted pages|Book index at the back with page numbers|

---

## 💥 Real World Analogy:

Let’s say you go to a library to find a book chapter.

- **Clustered index** = the book is already arranged in **chapter order** → You just open to the correct chapter directly.
    
- **Non-clustered index** = there's an index at the back saying "Chapter 4 → Page 73", so you use the pointer to go to that page.
    

---

## 💡 When Should You Use Which?

|Situation|Use|
|---|---|
|Searching by **Primary Key**|Clustered Index|
|Sorting by a column (e.g., dates)|Clustered Index|
|Filtering by other columns (e.g., name)|Non-Clustered Index|
|You want multiple search filters|Non-Clustered Index|

---

## 🛑 Important Things to Remember

- In **MySQL InnoDB**, the primary key **automatically becomes the clustered index**.
    
- Non-clustered indexes **do not change** the order of the table.
    
- Too many indexes = **more storage + slower inserts/updates** (because they all need to be updated).
    

---

## 👨‍🔬 Test Example

```sql
CREATE TABLE Products (
  ProductID INT PRIMARY KEY,  -- Clustered index
  Name VARCHAR(100),
  Price INT
);

CREATE INDEX idx_price ON Products(Price);  -- Non-clustered index
```

Now:

- Searching by `ProductID` is **super fast** due to clustered index.
    
- Searching by `Price` is **fast**, because non-clustered index helps find the row quickly.
    

---

# 🚀What is a Scalar Function?

A **scalar function** is a type of **built-in function in SQL** that:

- **Takes input**
    
- **Performs some operation**
    
- **Returns a single value (scalar)**
    

> 💬 "Scalar" just means: it returns **one value**, not a table or multiple rows.

---

### 🧠 Simple Analogy:

Think of it like a calculator function:

- `sqrt(9)` → gives 3
    
- `UPPER('hello')` → gives `'HELLO'`
    
- `LEN('Achyuth')` → gives 7
    

Each time, you give one input (or more), and get **one output**.

---

## 🔢 Types of Scalar Functions in SQL

Here’s a breakdown based on what they do:

---

### 1. 🔠 **String Functions**

These work with text (VARCHAR, CHAR, etc.)

|Function|Description|Example|Result|
|---|---|---|---|
|`UPPER()`|Converts to uppercase|`UPPER('achyuth')`|`'ACHYUTH'`|
|`LOWER()`|Converts to lowercase|`LOWER('BOSS')`|`'boss'`|
|`LENGTH()`|Returns length of string|`LENGTH('hello')`|`5`|
|`CONCAT()`|Joins strings together|`CONCAT('Achyuth', ' J')`|`'Achyuth J'`|
|`SUBSTRING()`|Extracts part of a string|`SUBSTRING('Achyuth', 1, 3)`|`'Ach'`|
|`TRIM()`|Removes spaces from both ends|`TRIM(' Hello ')`|`'Hello'`|

---

### 2. 🧮 **Mathematical Functions**

Work with numeric values

|Function|Description|Example|Result|
|---|---|---|---|
|`ABS()`|Absolute value|`ABS(-5)`|`5`|
|`ROUND()`|Rounds to nearest value|`ROUND(3.14159, 2)`|`3.14`|
|`CEIL()` / `CEILING()`|Next higher integer|`CEIL(4.2)`|`5`|
|`FLOOR()`|Next lower integer|`FLOOR(4.9)`|`4`|
|`POWER()`|Power of a number|`POWER(2, 3)`|`8`|
|`SQRT()`|Square root|`SQRT(16)`|`4`|

---

### 3. 🕰️ **Date and Time Functions**

|Function|Description|Example|Result|
|---|---|---|---|
|`NOW()`|Current date and time|`NOW()`|`2025-08-03 23:45`|
|`CURDATE()`|Current date|`CURDATE()`|`2025-08-03`|
|`YEAR()`|Extracts year|`YEAR('2025-08-03')`|`2025`|
|`MONTH()`|Extracts month|`MONTH('2025-08-03')`|`8`|
|`DAY()`|Extracts day|`DAY('2025-08-03')`|`3`|
|`DATEDIFF()`|Difference between two dates (in days)|`DATEDIFF('2025-08-10', '2025-08-03')`|`7`|

---

### 4. 🔀 **Conversion Functions**

| Function    | Description                           | Example               | Result |
| ----------- | ------------------------------------- | --------------------- | ------ |
| `CAST()`    | Converts data type                    | `CAST(12.3 AS INT)`   | `12`   |
| `CONVERT()` | Another way to convert types (MS SQL) | `CONVERT(INT, '123')` | `123`  |

---

### 5. 🔍 **System Functions** (Depends on the DB engine)

|Function|Description|Example|Result|
|---|---|---|---|
|`USER()`|Returns current user|`USER()`|`'root@localhost'`|
|`DATABASE()`|Returns current database|`DATABASE()`|`'my_database'`|

---

## 📌 Real-Life Example:

### Table: `students`

|id|name|marks|
|---|---|---|
|1|Achyuth|88|
|2|Rahul|92|

Query:

```sql
SELECT UPPER(name), ROUND(marks/10, 1) AS grade FROM students;
```

Result:

|UPPER(name)|grade|
|---|---|
|ACHYUTH|8.8|
|RAHUL|9.2|

---

## 🔧 Use Case in Real Projects:

- Formatting output (`UPPER`, `CONCAT`)
    
- Calculating grades/salaries (`ROUND`, `FLOOR`, `ABS`)
    
- Handling dates like birthday, expiry (`DATEDIFF`, `YEAR`)
    
- Converting data between types (`CAST`, `CONVERT`)
    

---

## ✅ Summary Table:

|Topic|Scalar Function Does…|
|---|---|
|🔍 Returns|A single value (one row → one value)|
|📄 Used in|`SELECT`, `WHERE`, `ORDER BY`, etc.|
|📊 Operates On|Strings, Numbers, Dates, etc.|
|🔄 Examples|`UPPER()`, `ABS()`, `NOW()`, `ROUND()`, `LEN()`|

---


# 🚀 Major Categories of SQL Data Types

> 🔑 **Data types in SQL** define **what kind of data** can be stored in each column of a table.  
> They are like “data containers” — some store numbers, some store text, some store dates, etc.
---

## 1. 🔢 **Numeric Data Types**

Used to store **numbers** – both **whole** and **decimal**.

### A. Integer Types (Whole Numbers)

|Data Type|Size (Bytes)|Range|Example|
|---|---|---|---|
|`TINYINT`|1 byte|-128 to 127 (or 0 to 255 unsigned)|120|
|`SMALLINT`|2 bytes|-32,768 to 32,767|20000|
|`MEDIUMINT`|3 bytes|-8 million to +8 million approx.|550000|
|`INT`|4 bytes|-2.1B to 2.1B|100000|
|`BIGINT`|8 bytes|Very large numbers|9876543210|

💡 Use when: You know you'll store **whole numbers** (like age, count, IDs, etc.)

---

### B. Decimal / Floating-Point Types (Numbers with decimal point)

|Data Type|Description|Example|
|---|---|---|
|`DECIMAL(p,s)`|Precise decimal numbers. p = precision, s = scale|`DECIMAL(5,2)` stores `999.99`|
|`FLOAT`|Approximate values (less precision)|123.456|
|`DOUBLE`|More precise than FLOAT|123456.7890|

💡 Use `DECIMAL` for **money**, `FLOAT`/`DOUBLE` for scientific or approximate values.

---

## 2. 🔤 **String (Character/Text) Data Types**

Used to store **text**, like names, emails, etc.

|Data Type|Description|Example|
|---|---|---|
|`CHAR(n)`|Fixed length string. Always uses `n` characters.|`CHAR(5)` stores 'AB '|
|`VARCHAR(n)`|Variable length. Stores up to `n` characters.|`VARCHAR(50)` → 'Achyuth'|
|`TEXT`|Large amount of text (like paragraphs)|65,535 characters max|
|`TINYTEXT`|Up to 255 characters||
|`MEDIUMTEXT`|Up to 16 MB||
|`LONGTEXT`|Up to 4 GB||

💡 Use:

- `CHAR` for fixed-length (like country code).
    
- `VARCHAR` for normal text (names, emails).
    
- `TEXT` for large inputs (descriptions, blogs).
    

---

## 3. 🕓 **Date and Time Data Types**

Used to store **dates, times, timestamps**.

|Data Type|Description|Example|
|---|---|---|
|`DATE`|Stores only the date|`2025-08-03`|
|`TIME`|Stores only the time|`14:30:00`|
|`DATETIME`|Stores both date and time|`2025-08-03 14:30:00`|
|`TIMESTAMP`|Same as DATETIME (used for logging)|`2025-08-03 14:30:00`|
|`YEAR`|Stores only the year (2 or 4 digit)|`2025`|

💡 Use:

- `DATETIME` for events like order time, registration.
    
- `DATE` for birth date.
    
- `TIMESTAMP` for auto-recording update time.
    

---

## 4. ✅ **Boolean Data Type**

|Data Type|Description|Example|
|---|---|---|
|`BOOLEAN`|Stores `TRUE` or `FALSE`|`TRUE`|

> In MySQL, it’s stored as `TINYINT(1)` internally — so `1` = `TRUE`, `0` = `FALSE`.

💡 Use for: flags like `is_active`, `is_deleted`, etc.

---

## 5. 🆔 **Auto-Increment / Identity Columns**

Used to **automatically generate unique values**, usually for primary keys.

```sql
id INT AUTO_INCREMENT PRIMARY KEY
```

Every new row will get an auto-generated ID (1, 2, 3…).

---

## 6. 🧪 **Binary Data Types (for files, images, etc.)**

|Data Type|Description|
|---|---|
|`BINARY(n)`|Fixed-length binary data|
|`VARBINARY(n)`|Variable-length binary data|
|`BLOB`|Large binary objects (for images, files)|

💡 Used when storing **images, PDFs, videos, or encrypted data** in the DB.

---

## ⚙️ Choosing the Right Data Type — Tips

|Data Type|Use it for...|Example|
|---|---|---|
|`INT`|IDs, counters|User ID, product count|
|`VARCHAR`|Names, emails, short text|`name VARCHAR(50)`|
|`TEXT`|Paragraphs or articles|`description TEXT`|
|`DATE`|Date only|`birth_date DATE`|
|`BOOLEAN`|Yes/No, True/False fields|`is_active BOOLEAN`|
|`DECIMAL`|Money, precision math|`price DECIMAL(8,2)`|
|`FLOAT`|Approximate decimal values|scientific numbers, scores|

---

## ✅ Example Table with Data Types

```sql
CREATE TABLE Users (
  user_id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(255),
  birthdate DATE,
  is_active BOOLEAN,
  wallet_balance DECIMAL(10, 2),
  bio TEXT,
  profile_picture BLOB
);
```

---

## 🚨 Common Mistakes to Avoid

1. ❌ Using `FLOAT` for money — use `DECIMAL` instead for accuracy.
    
2. ❌ Using `VARCHAR(1000)` when only 20 chars are needed — wastes memory.
    
3. ❌ Using `TEXT` when `VARCHAR` is enough — TEXT can’t be indexed easily.
    

---

## 🧠 Summary Table

|Category|Data Types Examples|
|---|---|
|Numeric|`INT`, `TINYINT`, `BIGINT`, `DECIMAL`, `FLOAT`, `DOUBLE`|
|Text|`CHAR`, `VARCHAR`, `TEXT`, `TINYTEXT`, `LONGTEXT`|
|Date/Time|`DATE`, `TIME`, `DATETIME`, `TIMESTAMP`, `YEAR`|
|Boolean|`BOOLEAN` (stored as 0 or 1)|
|Binary|`BINARY`, `VARBINARY`, `BLOB`|
|Auto-Increment|`AUTO_INCREMENT`|

---

# 🚀CHAR vs VARCHAR 

|Feature|`CHAR(n)` 🔷|`VARCHAR(n)` 🔶|
|---|---|---|
|✅ Type|**Fixed-length**|**Variable-length**|
|📏 Storage|Always takes **n bytes**, even if shorter|Takes only **actual data size**|
|🧱 Padding|Pads extra space with blanks (`' '`)|No padding – stores only the input|
|⚡ Performance|Slightly faster for **fixed-size**|Slightly slower, but saves space|
|📦 Best Use|**Fixed-size values** (e.g. codes)|**Variable-length values** (e.g. names)|

---

## 🔎 What They Actually Store (with Examples)

```sql
CREATE TABLE Test (
  char_col CHAR(5),
  varchar_col VARCHAR(5)
);
```

```sql
INSERT INTO Test VALUES ('ABC', 'ABC');
```

### CHAR(5) stores:

```
'ABC  '  ← padded with 2 spaces
```

### VARCHAR(5) stores:

```
'ABC'   ← only 3 characters
```

So although both look the same visually, CHAR uses **5 bytes**, while VARCHAR uses only **3 + 1 byte (length info)**.

---

## 💡 Real Life Analogy

|Type|Analogy|
|---|---|
|`CHAR`|Like **boxes** of fixed size. Even if the item is small, the box stays big.|
|`VARCHAR`|Like **bags** that adjust to the item’s size – more flexible.|

---

## 📦 When to Use CHAR?

Use `CHAR(n)` when:

- All values are **same length**
    
- Example:
    
    - Country codes: `'USA'`, `'IND'`, `'UAE'`
        
    - Gender: `'M'`, `'F'`
        
    - Status flags: `'Y'`, `'N'`
        

Why? Because:

- No extra overhead
    
- Faster access (DB knows exact size of every row)
    

---

## 📦 When to Use VARCHAR?

Use `VARCHAR(n)` when:

- Data length **varies a lot**
    
- Example:
    
    - Names (`'Ram'`, `'Suryanarayanan'`)
        
    - Emails
        
    - Product descriptions
        
    - Comments
        

Why?

- Saves space
    
- Avoids unnecessary blanks
    

---

## 🧠 Storage Notes (In MySQL InnoDB):

- `CHAR(n)` → Always stores **n bytes**
    
- `VARCHAR(n)` → Stores **actual length + 1 or 2 extra bytes**
    
    - +1 byte if length ≤ 255
        
    - +2 bytes if length > 255
        

---

## 🧪 Performance Tip:

- `CHAR` is slightly faster when:
    
    - You do a lot of **reads** on short, fixed-length fields.
        
- `VARCHAR` is better when:
    
    - You want to **optimize storage**.
        

---

## ✅ Final Summary

|CHAR|VARCHAR|
|---|---|
|Fixed size (padded with spaces)|Flexible size (no padding)|
|Uses more space for short values|Uses exact space needed|
|Faster for fixed-length reads|More efficient for varying text|
|Best for codes, flags, identifiers|Best for names, emails, comments, etc.|

---


# 🚀What is a Trigger in SQL?

A **trigger** is a special kind of **stored procedure** that **automatically executes** when certain events happen in a table.

> You **don’t call a trigger** – it’s **triggered automatically** when `INSERT`, `UPDATE`, or `DELETE` operations occur.

---

## 🎯 Why Do We Use Triggers?

To **automate reactions** to data changes. Triggers are used for:

- **Auditing** (e.g., log who changed what)
    
- **Validation** before/after changes
    
- **Automatic updates** to other tables
    
- **Enforcing business rules** (e.g., preventing deletes)
    

---

## ⚙️ Types of Triggers (based on time):

|Type|Description|
|---|---|
|`BEFORE` trigger|Fires **before** the action happens|
|`AFTER` trigger|Fires **after** the action happens|
|`INSTEAD OF`|(in some DBs) Replaces the action|

---

## 📍 Events That Can Trigger:

- `INSERT`
    
- `UPDATE`
    
- `DELETE`
    

---

## 🧪 Syntax Example (MySQL):

Let’s say we have two tables:

```sql
CREATE TABLE employees (
  id INT,
  name VARCHAR(100),
  salary INT
);

CREATE TABLE audit_log (
  id INT AUTO_INCREMENT PRIMARY KEY,
  emp_id INT,
  old_salary INT,
  new_salary INT,
  changed_at DATETIME
);
```

We want to log every **salary change**.

### ✅ Create Trigger:

```sql
DELIMITER //

CREATE TRIGGER salary_update_trigger
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
  IF OLD.salary != NEW.salary THEN
    INSERT INTO audit_log (emp_id, old_salary, new_salary, changed_at)
    VALUES (OLD.id, OLD.salary, NEW.salary, NOW());
  END IF;
END;
//

DELIMITER ;
```

---

## 🔄 What Happens?

When someone runs:

```sql
UPDATE employees
SET salary = 55000
WHERE id = 2;
```

➡️ The **trigger fires automatically** and inserts a new row in `audit_log` — without the user even knowing!

---

## 🧠 OLD vs NEW Keywords

Inside triggers:

- `OLD.column_name` → Value **before** the change
    
- `NEW.column_name` → Value **after** the change
    

Used for comparisons and conditional logic inside triggers.

---

## 📌 Where Triggers Are Super Useful:

1. **Audit Logs** (track changes)
    
2. **Cascade Updates** (auto update related tables)
    
3. **Prevent Deletion** (e.g., if a condition is not met)
    
4. **Calculate Values** (e.g., auto fill total cost)
    
5. **Data Validation** (e.g., restrict values)
    

---

## ❌ Downsides of Triggers

|Drawback|Why It Matters|
|---|---|
|Hidden logic|Triggers run silently – hard to trace|
|Performance issues|Can slow down inserts/updates|
|Debugging is tricky|Errors inside triggers are harder to catch|
|Hard to manage at scale|Too many triggers = complex system|

---

## ✅ Quick Summary:

|Feature|Description|
|---|---|
|What it is|Auto-executed stored procedure|
|When it runs|On `INSERT`, `UPDATE`, or `DELETE`|
|Types|`BEFORE`, `AFTER`, (`INSTEAD OF`)|
|Common use|Auditing, validation, automation, security|
|Pros|Automation, integrity, less code duplication|
|Cons|Hidden logic, harder to debug, performance hit|

---

# 🚀**What is Sharding?**

**Sharding** is a **database partitioning technique** that breaks large databases into **smaller, faster, and more manageable pieces called "shards"**.

Each **shard** is an independent database containing a **subset of the total data**. The idea is to **distribute the load** and **store data across multiple servers** (called horizontal scaling).

---

### 🔍 Why Do We Need Sharding?

Imagine an e-commerce platform like Amazon with:

- Millions of users
    
- Billions of transactions
    
- Terabytes of product data
    

As the data grows:

- Query speed reduces
    
- Server resources max out
    
- Backup and maintenance become tough
    

👉 **Sharding helps solve this by splitting the data across servers, so no single server becomes a bottleneck.**

---

### 📦 Types of Sharding

#### 1. **Horizontal Sharding (most common)**

- Each shard has **rows** from the original table.
    
- Example:
    
    - Table: `Users`
        
    - Shard 1: Users with `user_id 1–10000`
        
    - Shard 2: Users with `user_id 10001–20000`
        
- All shards have the **same schema**, just different data.
    

#### 2. **Vertical Sharding**

- Each shard holds a **subset of columns**.
    
- You split a table by **function or access pattern**.
    
- Example:
    
    - Shard 1: `Users(id, name, email)`
        
    - Shard 2: `Users(id, password, login_attempts)`
        
- Often used in microservices to split logically separate domains.
    

#### 3. **Geo Sharding (or Directory-Based Sharding)**

- Shards are divided based on **geographical region**.
    
- Example:
    
    - Asia customers go to one shard
        
    - US customers go to another
        

#### 4. **Hash-Based Sharding**

- Use a **hash function** on a key (e.g., user_id) to assign the row to a shard.
    
- Ensures **uniform data distribution** but makes rebalancing harder.
    

---

### ⚙️ How Sharding Works – Step-by-Step

Let’s say you have a `Users` table with 1 million records.

You want to shard it horizontally into 3 shards.

#### Step 1: Define Shard Key

- Choose a column to split on: `user_id`
    

#### Step 2: Define Shard Ranges (Range-Based Sharding)

- Shard 1: `user_id` 1–333333
    
- Shard 2: `user_id` 333334–666666
    
- Shard 3: `user_id` 666667–1000000
    

#### Step 3: Distribute Shards

- Place these shards on different **databases or servers**
    

#### Step 4: Query Routing

- You need a **shard router** or application logic to route queries to the correct shard based on the `user_id`.
    

---

### ⚠️ Challenges of Sharding

|Problem|Description|
|---|---|
|**Query Complexity**|Queries involving data from multiple shards require **cross-shard joins**, which are slow and complex.|
|**Rebalancing**|Adding/removing shards means moving data, which can be **costly**.|
|**Data Consistency**|Maintaining ACID properties across shards is **difficult**.|
|**Backup and Restore**|You need to **individually back up** and **restore** each shard.|

---

### ✅ Benefits of Sharding

|Advantage|Explanation|
|---|---|
|**Scalability**|More users or data? Just add more shards!|
|**Performance**|Queries are faster because each shard has less data.|
|**Reliability**|A failure in one shard doesn’t bring down the entire system.|
|**Manageability**|Easier to maintain smaller databases.|

---

### 🧠 Example Scenario (Real Life)

**Facebook Messages System:**

- You can’t store every message ever sent in a single table.
    
- Instead, messages are **sharded by user_id**, so each user’s messages go to a different shard.
    
- When a user logs in, the system knows where to find their messages.
    

---

### 💬 SQL Doesn’t Support Native Sharding. So How Do We Implement It?

- SQL (e.g., MySQL, PostgreSQL) doesn’t **natively** support sharding.
    
- You need to handle it via:
    
    - **Middleware or proxy layers** (e.g., Vitess for MySQL)
        
    - **Application logic** (your backend decides which shard to query)
        
    - **Third-party tools** or database clustering systems
        

---

### 🔚 Summary

|Term|Meaning|
|---|---|
|**Sharding**|Splitting a large database into smaller pieces for better performance and scalability|
|**Shard**|An independent, smaller database|
|**Shard Key**|The column used to decide which row goes to which shard|

Sharding is like breaking a huge problem into smaller pieces that can be solved faster and in parallel.

---

#  🚀Three-Schema Architecture 

---

The **Three-Schema Architecture** is a **conceptual framework** that helps in **designing and managing databases**. It was proposed by the **ANSI/SPARC** (American National Standards Institute / Standards Planning And Requirements Committee).

This architecture helps separate the database into **three levels**, each with different concerns. It improves **data abstraction**, **security**, and **flexibility**.

---

## 🧠 Why Is This Architecture Needed?

- Users don't need to know how data is stored physically.
    
- Developers don’t need to worry about internal storage details.
    
- If changes are made in one layer, other layers won’t break — this makes the system flexible.
    

---

## 🔺 Three Levels of Schema

```
               +------------------------+
               |  External Schema (View)|
               +------------------------+
                         ↑
                         |
               +------------------------+
               | Conceptual Schema      |
               +------------------------+
                         ↑
                         |
               +------------------------+
               | Internal Schema (Storage)|
               +------------------------+
```

---

### 1. **External Level (View Level)**

👤 **Who uses it?** End users, application programs

📄 **What it shows?** Just a **subset of the database** needed by the user.

💡 **Key Idea:** Users see only the data relevant to them.

✅ **Example:**

- A teacher sees only student names and marks.
    
- A student sees only their own attendance and grades.
    

✅ **SQL Example (View):**

```sql
CREATE VIEW student_view AS
SELECT name, marks FROM students;
```

This view **hides columns like student address or phone number** — users don’t see more than they need.

---

### 2. **Conceptual Level (Logical Level)**

🛠️ **Who uses it?** Database designers and developers

📊 **What it shows?** The **entire logical structure** of the database

💡 **Key Idea:** It defines **what data** is stored and the **relationships** between them — **without showing how** the data is stored.

✅ **Includes:**

- Table names
    
- Column names, data types
    
- Relationships (like foreign keys)
    
- Constraints (like UNIQUE, NOT NULL)
    

✅ **Example:**

```sql
CREATE TABLE students (
  student_id INT PRIMARY KEY,
  name VARCHAR(100),
  marks INT,
  course_id INT,
  FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

---

### 3. **Internal Level (Physical Level)**

💾 **Who uses it?** Database administrators and system software

🧱 **What it shows?** How data is **physically stored on disk**

💡 **Key Idea:** Defines **file structures**, **indexing**, **compression**, **data placement**, etc.

✅ **Includes:**

- File paths
    
- B+ Tree indexes
    
- Page size and block size
    
- Partitioning or Sharding
    

✅ **You don’t see this in SQL** directly — it’s controlled by the **DBMS internally**, but sometimes you configure it:

```sql
CREATE INDEX idx_student_name ON students(name);
```

This helps speed up searches — a concept related to internal schema.

---

## 🔁 Benefits of Three-Schema Architecture

|Feature|Benefit|
|---|---|
|**Data Abstraction**|Users don't need to know internal storage details|
|**Data Independence**|You can change storage or logic without affecting users|
|**Security**|Views can hide sensitive data|
|**Scalability**|Easy to manage growing systems|
|**Flexibility**|Application changes don’t require schema redesign|

---

## 🎯 Real-World Analogy

Think of it like an **ATM**:

- **External Level:** You see your balance, withdraw cash (user interface)
    
- **Conceptual Level:** Bank records your account, transactions, limits (logic)
    
- **Internal Level:** Data stored in servers, files, backup systems (physical)
    

---

## 📝 Summary Table

|Schema Level|What it Describes|Who Uses It|Example|
|---|---|---|---|
|External|User-specific views|Users, apps|`CREATE VIEW`|
|Conceptual|Full logical design|Developers|`CREATE TABLE`, constraints|
|Internal|Physical storage|DBA, DBMS|Indexes, partitions|

---

Let me know if you want a **diagram**, **real project-based use case**, or **MCQ-style questions** to test this concept.