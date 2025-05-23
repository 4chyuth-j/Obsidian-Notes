# **What is a Database?

**Formal Definition**: A database is an organized collection of structured information, or data, typically stored electronically in a computer system. It is usually managed by a database management system (DBMS).

**Simple Explanation**: Imagine a digital filing cabinet where you store information. This makes it easy to find and use the information when you need it.

### Key Components of a Database:

1. **Data**: The actual information being stored, such as names, addresses, or sales records.
2. **DBMS (Database Management System)**: Software that allows you to create, manage, and manipulate databases. Examples include MySQL, PostgreSQL, and MongoDB.
3. **Schema**: The structure or blueprint of the database that defines how data is organized and how relationships between data are managed.

### Types of Databases:

1. **Relational Databases**:
    - Store data in tables (rows and columns).
    - Use Structured Query Language (SQL) for managing data.
    - Examples: MySQL, PostgreSQL, Oracle.

2. **NoSQL Databases**:
    - Store data in various formats such as documents, key-value pairs, graphs, or wide-columns.
    - Examples: MongoDB, Cassandra, Redis.

### Example of How a Relational Database Works:
- **Table**: Think of a table as a spreadsheet.
- **Row**: Each row represents a single record.
- **Column**: Each column represents a specific piece of data for the records.

#### Example Table:
| ID  | Name  | Age | Email            |
|-----|-------|-----|------------------|
| 1   | Alice | 30  | alice@example.com|
| 2   | Bob   | 25  | bob@example.com  |

### Example of How a NoSQL Database Works (e.g., MongoDB):
- **Document**: Instead of tables, MongoDB stores data in documents (similar to JSON objects).
- **Collection**: A group of documents.

#### Example Document in MongoDB:
```json
{
  "name": "Alice",
  "age": 30,
  "email": "alice@example.com",
  "address": {
    "street": "123 Main St",
    "city": "Springfield",
    "zip": "12345"
  }
}
```

### Why Use a Database?
- **Organization**: Keeps data structured and easy to access.
- **Efficiency**: Allows quick retrieval and manipulation of data.
- **Scalability**: Can handle large amounts of data and users.

# **What is Mongodb?

MongoDB is a popular **NoSQL database**, which means it doesn't rely on the traditional table-based structure used in relational databases like MySQL or PostgreSQL. Instead, it stores data in a flexible, JSON-like format called **documents**.

Here’s what you need to know as a beginner:

### Key Features of MongoDB:

1. **Document-Based**:  
    Data is stored in "documents," which are similar to JSON objects. Each document is a collection of key-value pairs. Example:
    
    ```json
    {
      "name": "John",
      "age": 30,
      "skills": ["JavaScript", "Node.js", "MongoDB"]
    }
    ```
    
2. **Collections**:  
    Similar to tables in relational databases, a collection is a group of related documents. For example, a "users" collection could store all user data.
    
3. **Schema-Less**:  
    Unlike relational databases, MongoDB doesn’t require a fixed structure or schema for your data. This means each document in a collection can have different fields.
    
4. **Scalable and Fast**:  
    MongoDB is designed to handle large amounts of data and can scale across many servers.
    

---

### Why Use MongoDB?

- **Flexibility**: You don’t need to define the data structure upfront, making it easy to work with changing requirements.
- **High Performance**: It’s optimized for read and write operations, which is useful for applications that need fast performance.
- **Suitable for Modern Apps**: Often used in web, mobile, and IoT applications due to its ability to store various data types.

---

### Simple Example:

Let’s say you’re creating a database for an e-commerce website.

1. A relational database would store product information like this:
    
    ```sql
    Table: Products
    | id | name      | price | category  |
    |----|-----------|-------|-----------|
    | 1  | Laptop    | 50000 | Electronics|
    | 2  | T-Shirt   | 500   | Clothing  |
    ```
    
2. In MongoDB, the same data could look like this:
    
    ```json
    [
      { "id": 1, "name": "Laptop", "price": 50000, "category": "Electronics" },
      { "id": 2, "name": "T-Shirt", "price": 500, "category": "Clothing" }
    ]
    ```
    

---

### How to Use MongoDB:

1. **Install MongoDB**: Download and install from [MongoDB’s official site](https://www.mongodb.com/).
2. **Run MongoDB Server**: Start the server locally or use a cloud-based service like MongoDB Atlas.
3. **Connect to MongoDB**: Use a programming language like JavaScript with libraries like **Mongoose** or the **MongoDB driver**.

---

MongoDB is great for beginners because it’s easy to set up and use. It’s particularly powerful for handling unstructured or semi-structured data in modern applications.

![[Screenshot 2025-01-14 102357.png]]

![[Screenshot 2025-01-14 102839.png]]




# **What is MongoDB Shell and MongoDB Compass?

MongoDB provides tools to interact with your database. Here’s an overview of **MongoDB Shell** and **MongoDB Compass**, designed to suit different use cases.

---

### **1. MongoDB Shell (mongosh)**

#### **What is it?**

- **MongoDB Shell** (or `mongosh`) is a **command-line tool** for interacting with your MongoDB database.
- It allows you to run queries, manage databases, and perform administrative tasks directly from a terminal or command prompt.

#### **Key Features:**

- **Query Execution:** Run commands to retrieve, insert, update, or delete data.
- **Database Administration:** Create and manage databases, collections, and indexes.
- **Scripting Support:** Write JavaScript-based scripts to automate tasks.
- **Lightweight:** Requires no graphical interface and is suitable for developers who prefer the command line.

#### **Example Usage:**

```bash
mongosh
```

- **Switch to a database:**
    
    ```javascript
    use myDatabase
    ```
    
- **Insert data:**
    
    ```javascript
    db.myCollection.insertOne({ name: "Alice", age: 30 })
    ```
    
- **Query data:**
    
    ```javascript
    db.myCollection.find()
    ```
    

---

### **2. MongoDB Compass**

#### **What is it?**

- **MongoDB Compass** is a **graphical user interface (GUI)** for MongoDB.
- It provides a user-friendly way to visualize and interact with your data without writing commands.

#### **Key Features:**

- **Data Exploration:** Browse collections, view documents, and visualize data.
- **Schema Analysis:** Understand the structure of your data, including field types and patterns.
- **Query Builder:** Use a GUI-based query interface without writing code.
- **Performance Insight:** Analyze and optimize your queries.
- **Aggregation Pipeline Builder:** Create and test complex data transformations visually.

#### **Example Usage:**

1. **Open MongoDB Compass**.
2. **Connect to MongoDB:**
    - Use the default connection string:
        
        ```
        mongodb://localhost:27017
        ```
        
3. **Explore Data:**
    - View all databases and collections.
    - Click on a collection to see documents.
4. **Run a Query:**
    - Enter filter criteria like `{ age: { $gt: 25 } }` to find people older than 25.

---

### **Differences Between MongoDB Shell and Compass**

|Feature|MongoDB Shell (`mongosh`)|MongoDB Compass (GUI)|
|---|---|---|
|**Interface**|Command-line|Graphical|
|**Ease of Use**|Requires familiarity with MongoDB commands|User-friendly, intuitive GUI|
|**Performance**|Lightweight|Slightly heavier due to GUI|
|**Use Case**|For developers comfortable with commands|For beginners or quick data exploration|
|**Data Visualization**|Limited|Rich visualization features|

---

### **Which Should You Use?**

- **Use MongoDB Shell** if:
    - You’re a developer comfortable with coding.
    - You need precise control or want to automate tasks.
- **Use MongoDB Compass** if:
    - You’re new to MongoDB.
    - You prefer a graphical interface for browsing and managing data.

---

Together, MongoDB Shell and Compass offer flexibility for interacting with your databases, catering to both advanced developers and beginners!

# **Show dbs, use user, db, db.dropDatabase()

Here’s a simple explanation of the MongoDB commands **`show dbs`**, **`use <database>`**, **`db`**, and **`db.dropDatabase()`** for beginners:

---

### **1. `show dbs`**

- **What It Does:**
    
    - Displays a list of all existing databases on your MongoDB server.
    - Shows the size of each database.
- **Example:**
    
    ```javascript
    show dbs
    ```
    
    - **Output:**
        
        ```
        admin       0.000GB
        config      0.000GB
        local       0.000GB
        myDatabase  0.001GB
        ```
        

---

### **2. `use <database>`**

- **What It Does:**
    
    - Switches the context to the specified database. Any commands you run afterward will apply to this database.
    - If the database doesn’t exist, it will be created when data is added.
- **Example:**
    
    ```javascript
    use userDatabase
    ```
    
    - **Output:**
        
        ```
        switched to db userDatabase
        ```
        

---

### **3. `db`**

- **What It Does:**
    
    - Displays the name of the currently selected database.
    - Useful to confirm which database you're working with.
- **Example:**
    
    ```javascript
    db
    ```
    
    - **Output:**
        
        ```
        userDatabase
        ```
        

---

### **4. `db.dropDatabase()`**

- **What It Does:**
    
    - Deletes the currently selected database, including all collections and data in it.
    - **Warning:** This action is irreversible.
- **How to Use:**
    
    1. Switch to the database you want to delete using `use <database>`.
    2. Run `db.dropDatabase()`.
- **Example:**
    
    ```javascript
    use userDatabase
    db.dropDatabase()
    ```
    
    - **Output:**
        
        ```
        { "ok": 1 }
        ```
        

---

### **Putting It All Together**

```javascript
// Step 1: Show existing databases
show dbs

// Step 2: Switch to a database
use myDatabase

// Step 3: Check the current database
db

// Step 4: Delete the database
db.dropDatabase()

// Step 5: Verify by checking the list of databases again
show dbs
```

These commands help you navigate, manage, and clean up databases in MongoDB effectively!




# **What is a Collection

In MongoDB, a **collection** is similar to a **table** in traditional databases. It is a container that stores multiple **documents**, where each document is a unit of data in **JSON-like format** (key-value pairs).

---

### **Key Features of a Collection:**

1. **Flexible Structure:**
    
    - Unlike tables with predefined schemas, collections can store documents with different structures (fields can vary from document to document).
2. **No Schema Enforcement:**
    
    - MongoDB collections do not enforce a strict schema, meaning you can add new fields to documents without predefined rules.
3. **Grouped Documents:**
    
    - All related data is stored together in a single collection, making it easy to query and manage.

---

### **Example**

If you were managing user information in a MongoDB database, you might have a collection called `users`.

This collection could store documents like:

```json
{
  "name": "Alice",
  "age": 25,
  "email": "alice@example.com"
}
```

and

```json
{
  "name": "Bob",
  "city": "New York",
  "hobbies": ["reading", "gaming"]
}
```

Notice that the documents can have different fields and structures.

---

### **How to Create a Collection**

You don't always need to manually create a collection. MongoDB automatically creates a collection the first time you insert data into it.

Manually creating one:

```javascript
db.createCollection("users");
```

---

### **Why Use Collections?**

- To organize and group related data.
- To perform queries, updates, and deletions on a specific set of documents.
- To separate different kinds of data (e.g., `orders`, `products`, `customers`).

---

In simple terms, a collection in MongoDB is where your data lives, and it works like a folder that holds JSON-like files (documents).
#  **Create Collection

In MongoDB, the `db.createCollection()` method is used to explicitly create a **collection** in a database.

Think of a collection as a folder where you store your data (documents). While MongoDB automatically creates a collection the first time you insert data into it, you might sometimes want to create it manually, especially when you need special settings.

### **Why Use `db.createCollection()`?**

- To create collections with specific features (e.g., a limited size or special validation rules).
- To ensure a collection exists before adding data to it.

---

### **Syntax**

```javascript
db.createCollection("collectionName", options);
```

- **`collectionName`**: The name of the collection you want to create.
- **`options`**: Optional settings to customize the collection (e.g., size limits, validation rules).

---

### **Examples**

1. **Basic Collection Creation**
    
    ```javascript
    db.createCollection("myCollection");
    ```
    
    - This creates a collection named `myCollection` with default settings.
2. **Capped Collection (Fixed Size)**
    
    ```javascript
    db.createCollection("cappedCollection", { capped: true, size: 1024 });
    ```
    
    - A **capped collection** has a fixed size.
    - In this example:
        - The collection is capped.
        - It can hold up to 1 KB of data.
### **How to Check if It Worked**

After running `db.createCollection()`, you can check your collections using:

```javascript
show collections;
```

---

### **Key Points for Beginners**

- You don't always need to use `db.createCollection()`; MongoDB can create collections automatically when you insert data.
- Use `db.createCollection()` if you want to customize the collection with special rules or limits.
- It’s a handy tool when your app needs to control how data is stored and validated.



# **Drop()


The command `db.<name of collection>.drop()` in MongoDB is used to **delete a collection** from the database.

When you use this command:

1. The specified collection is permanently removed.
2. All the documents (data) inside the collection are also deleted.
3. This action **cannot be undone**, so use it carefully.

---

### **Syntax**

```javascript
db.collectionName.drop();
```

- Replace `collectionName` with the name of the collection you want to delete.

---

### **Example**

1. **Delete a Collection Named `users`:**
    
    ```javascript
    db.users.drop();
    ```
    
    - This will delete the `users` collection and all its data.
2. **Check the Result:** After running the `drop()` command, you can check if the collection is gone by listing all collections:
    
    ```javascript
    show collections;
    ```
    
    - If the collection was successfully deleted, it won’t appear in the list.

---

### **Important Notes**

- **Use With Caution:** Once a collection is dropped, the data is permanently lost unless you have a backup.
- **No Confirmation Prompt:** The command doesn’t ask for confirmation, so double-check the collection name before running it.

---

In short, `db.<name of collection>.drop()` is a simple way to delete an entire collection and its data, but make sure you really want to remove it before using this command!


# **What is a `document` in mongodb



In MongoDB, a **document** is like a single entry or record in a database. Think of it as a detailed form you fill out with information.

A **collection** is a group of these documents, similar to a folder containing multiple forms.

Here’s a simplified view:

### Document Example:
```json
{
  "_id": "123456",
  "name": "John Doe",
  "age": 30,
  "address": {
    "street": "123 Main St",
    "city": "Springfield",
    "state": "IL"
  },
  "hobbies": ["reading", "traveling", "swimming"]
}
```

- **_id**: A unique identifier for each document. Think of it like a social security number.
- **name** and **age**: Fields holding simple pieces of information. These are like name and age fields on a form.
- **address**: A nested document, meaning it's a document within a document. It has more details like street, city, and state.
- **hobbies**: An array, which is a list of items. Here, it's a list of things the person enjoys doing.

### Collection:
Imagine you have several documents like the one above. These documents are stored together in a collection. It's like having a folder with several forms, each detailing a different person's information.

So, MongoDB's documents are flexible and can store various types of data. This makes it easy to handle complex data without needing strict rules like traditional databases.



# **CRUD Operations in Mongodb

Sure! CRUD stands for Create, Read, Update, and Delete. These are the four basic operations you can perform on any data stored in a database. Here's how you can perform these operations in MongoDB:

### 1. Create (Insert)
Creating or inserting a new document into a MongoDB collection is like adding a new record.

**Example**:
```javascript
db.users.insertOne({
  "name": "Alice",
  "age": 30,
  "email": "alice@example.com"
});
```
This command inserts a new document into the `users` collection.

### 2. Read (Find)
Reading or finding documents means querying the database to retrieve data.

**Example**:
```javascript
// Find all documents
db.users.find();

// Find documents with a specific condition
db.users.find({"age": 30});
```
These commands retrieve all documents in the `users` collection and those where `age` is 30, respectively.

### 3. Update
Updating a document means modifying existing data.

**Example**:
```javascript
// Update a single document
db.users.updateOne(
  {"name": "Alice"},
  {$set: {"age": 31}}
);

// Update multiple documents
db.users.updateMany(
  {"age": 30},
  {$set: {"verified": true}}
);
```
These commands update Alice’s age to 31 and add a `verified` field to all documents where `age` is 30.

### 4. Delete
Deleting a document means removing data from the database.

**Example**:
```javascript
// Delete a single document
db.users.deleteOne({"name": "Alice"});

// Delete multiple documents
db.users.deleteMany({"age": {$lt: 25}});
```
These commands delete Alice’s document and remove all documents where `age` is less than 25.

### Summary
- **Create**: `insertOne()`, `insertMany()`
- **Read**: `find()`, `findOne()`
- **Update**: `updateOne()`, `updateMany()`
- **Delete**: `deleteOne()`, `deleteMany()`

I hope this gives you a clear understanding of CRUD operations in MongoDB! Let me know if you have more questions or need further details.
# **MongoDB `mongosh` Insert



---

## Insert Documents

There are 2 methods to insert documents into a MongoDB database.

### **insertOne()

To insert a single document, use the `insertOne()` method.

This method inserts a single object into the database.

` Note: When typing in the shell, after opening an object with curly braces "{" you can press enter to start a new line in the editor without executing the command. The command will execute when you press enter after closing the braces.`

### Example

```jsx
db.posts.insertOne({
  title: "Post Title 1",
  body: "Body of post.",
  category: "News",
  likes: 1,
  tags: ["news", "events"],
  date: Date()
})
```

` Note: If you try to insert documents into a collection that does not exist, MongoDB will create the collection automatically.`

### **insertMany()

To insert multiple documents at once, 
use the `insertMany()` method.

This method inserts an array of objects into the database.

### Example

```jsx
db.posts.insertMany([  
  {
    title: "Post Title 2",
    body: "Body of post.",
    category: "Event",
    likes: 2,
    tags: ["news", "events"],
    date: Date()
  },
  {
    title: "Post Title 3",
    body: "Body of post.",
    category: "Technology",
    likes: 3,
    tags: ["news", "events"],
    date: Date()
  },
  {
    title: "Post Title 4",
    body: "Body of post.",
    category: "Event",
    likes: 4,
    tags: ["news", "events"],
    date: Date()
  }
])
```


# **find & findOne()

Here’s a simple explanation of MongoDB’s `find()` and `findOne()` methods with **query** and **projection**, using examples to make it beginner-friendly:

---

### **1. What is `find()`?**

The `find()` method retrieves multiple documents (data entries) from a collection that match a given query. If no query is provided, it retrieves **all documents**.

#### **Example: Using `find()` with Query and Projection**

Let’s say you have a collection named `products` with these documents:

```json
[
  { "name": "Dell Laptop", "price": 75000, "rating": 4.5 },
  { "name": "HP Laptop", "price": 72000, "rating": 4.3 },
  { "name": "MacBook", "price": 120000, "rating": 4.8 }
]
```

- **Find All Documents:**
    
    ```javascript
    db.products.find();
    ```
    
    **Output:**
    
    ```json
    { "name": "Dell Laptop", "price": 75000, "rating": 4.5 }
    { "name": "HP Laptop", "price": 72000, "rating": 4.3 }
    { "name": "MacBook", "price": 120000, "rating": 4.8 }
    ```
    
- **Find Specific Documents (Query):** Retrieve only the document where `name` is "MacBook."
    
    ```javascript
    db.products.find({ name: "MacBook" });
    ```
    
    **Output:**
    
    ```json
    { "name": "MacBook", "price": 120000, "rating": 4.8 }
    ```
    
- **Find with Projection:** Retrieve all documents but show only the `name` and `price` fields (exclude `rating`).
    
    ```javascript
    db.products.find({}, { name: 1, price: 1, _id: 0 });
    ```
    
    **Output:**
    
    ```json
    { "name": "Dell Laptop", "price": 75000 }
    { "name": "HP Laptop", "price": 72000 }
    { "name": "MacBook", "price": 120000 }
    ```
    

---

### **2. What is `findOne()`?**

The `findOne()` method retrieves **only the first document** that matches the query. If no query is provided, it retrieves the first document in the collection.

#### **Example: Using `findOne()` with Query and Projection**

Using the same `products` collection:

- **Find the First Document:**
    
    ```javascript
    db.products.findOne();
    ```
    
    **Output:**
    
    ```json
    { "name": "Dell Laptop", "price": 75000, "rating": 4.5 }
    ```
    
- **Find One Specific Document (Query):** Retrieve the first document where `price` is 72000.
    
    ```javascript
    db.products.findOne({ price: 72000 });
    ```
    
    **Output:**
    
    ```json
    { "name": "HP Laptop", "price": 72000, "rating": 4.3 }
    ```
    
- **Find One with Projection:** Retrieve the first document but only show `name` and `rating`.
    
    ```javascript
    db.products.findOne({}, { name: 1, rating: 1, _id: 0 });
    ```
    
    **Output:**
    
    ```json
    { "name": "Dell Laptop", "rating": 4.5 }
    ```
    

---

### **Key Points for Query and Projection:**

- **Query**: Defines the condition to filter the data you want.
    - Example: `{ key: value }` → `find({ name: "MacBook" })`
- **Projection**: Specifies which fields to include or exclude in the result.
    - `1` → Include the field.
    - `0` → Exclude the field.
    - Example: `{ name: 1, price: 1, _id: 0 }` → Include `name` and `price`, exclude `_id`.

---

### **Differences Between `find()` and `findOne()`:**

|Feature|`find()`|`findOne()`|
|---|---|---|
|**Returns**|Multiple documents|A single document|
|**Query Type**|Returns all matches|Returns the first match|
|**Usage**|For bulk data retrieval|For specific or first document|

---

### **Real-Life Analogy:**

- **`find()`**: Searching through an entire library and getting all books written by a specific author.
- **`findOne()`**: Asking for the first book written by that author.

This makes MongoDB querying more flexible and easy to understand!


# **What is a Cursor in MongoDB? 

A cursor is a pointer  to a list of documents(also known as [batches.]) .
find() method does not return all the documents in that collection in one go, it returns documents in batches (list of documents) and that batch is called cursor.

A **cursor** in MongoDB is like a **pointer** that helps you navigate through the results of a query **one document at a time**.

When you run a **find()** query, MongoDB does not return all documents at once. Instead, it creates a **cursor**, which allows you to **retrieve and process documents one by one or in batches**.

---

### **🔹 Why is a Cursor Needed?**

Imagine you have a **huge database** with **millions of records**.

- If MongoDB sent all the data at once, it would **slow down** your system and consume too much memory.
- Instead, it gives you a **cursor**, which helps you fetch and process **small chunks of data efficiently**.

---

### **1️⃣ Basic Example of a Cursor**

Let's say we have a **users** collection with multiple documents:

```json
db.users.find()
```

This query **does not return all documents immediately**. Instead, it gives you a **cursor** that can be used to fetch data.

To **see the documents**, you can use the **`.toArray()`** method:

```json
db.users.find().toArray()
```

- This **converts the cursor** into an array and displays all the results.

---

### **2️⃣ How to Use a Cursor?**

MongoDB provides methods to **navigate** and **control** the cursor.

### **🔹 Looping Through a Cursor (`forEach()`)**

```json
db.users.find().forEach(doc => printjson(doc))
```

- This **iterates over each document** in the cursor and prints it.

---

### **🔹 Limiting Results (`limit()`)**

```json
db.users.find().limit(5)
```

- **Returns only the first 5 documents** from the cursor.

---

### **🔹 Skipping Results (`skip()`)**

```json
db.users.find().skip(10)
```

- **Ignores the first 10 documents** and returns the next set.

---

### **🔹 Sorting Results (`sort()`)**

```json
db.users.find().sort({ age: 1 })
```

- **Sorts documents by `age` in ascending order**.

---

### **3️⃣ Cursor Methods in MongoDB**

|**Method**|**Description**|
|---|---|
|`.toArray()`|Converts the cursor into an array of documents.|
|`.forEach()`|Iterates over each document in the cursor.|
|`.limit(n)`|Returns only `n` documents.|
|`.skip(n)`|Skips the first `n` documents.|
|`.sort({ field: 1 })`|Sorts the results (`1` for ascending, `-1` for descending).|
|`.next()`|Retrieves the next document in the cursor.|
|`.hasNext()`|Checks if more documents exist in the cursor.|
|`.count()`|Returns the total number of matching documents.|

---

### **4️⃣ Real-World Example**

Imagine an **e-commerce app** where a user searches for **laptops**.

### **Query to Find Laptops**

```json
db.products.find({ category: "laptop" })
```

- Instead of **loading all laptops** at once, MongoDB **creates a cursor**.

### **Paginating Results (Fetching in Small Chunks)**

```json
db.products.find({ category: "laptop" }).skip(10).limit(5)
```

- This **skips the first 10 laptops** and **retrieves the next 5**.

---

### **📌 Summary**

✔ **A cursor is like a pointer** that lets you retrieve documents **one by one or in batches**.  
✔ Prevents **slow performance and memory overload** by **fetching data efficiently**.  
✔ Can be **looped, limited, skipped, and sorted** using built-in methods.

---


# **Update Queries

Update queries in MongoDB are used to modify the existing documents in a collection. These queries allow you to change the data stored in your documents based on specific criteria.

There are several types of update operations you can perform:

### 1. **updateOne()**
This updates a single document that matches the filter criteria.

Example:
```javascript
db.collection.updateOne(
   { name: "John Doe" },
   { $set: { age: 31 } }
)
```
This query finds a document where the `name` is "John Doe" and updates the `age` field to 31.

### 2. **updateMany()**
This updates all documents that match the filter criteria.

Example:
```javascript
db.collection.updateMany(
   { age: { $gt: 25 } },
   { $set: { status: "Senior" } }
)
```
This query updates the `status` field to "Senior" for all documents where the `age` is greater than 25.

### 3. **replaceOne()**

The `replaceOne()` method in MongoDB is used to **completely replace** an existing document with a new document. Unlike `updateOne()`, which modifies specific fields, `replaceOne()` **replaces the entire document** except for the `_id` field (if it exists in the new document).

---

### Syntax:

```json
db.collection.replaceOne(
   { <filter> },   // Query to find the document
   { <replacementDocument> }  // New document that replaces the old one
)
```

---

### Example:

#### ✅ Replacing a document completely

```json
db.users.replaceOne(
   { "name": "John" },  
   { "name": "John", "age": 30, "city": "New York" }
)
```

🔹 This finds the document where `"name": "John"` and **replaces it entirely** with the new document.  
🔹 If the old document had extra fields (e.g., `"status": "active"`), they will be **removed** unless included in the replacement.

---

### Key Differences Between `replaceOne()` and `updateOne()`

| Feature                       | `replaceOne()`                                                  | `updateOne()`                                            |
| ----------------------------- | --------------------------------------------------------------- | -------------------------------------------------------- |
| **Replaces entire document?** | ✅ Yes                                                           | ❌ No (only modifies specific fields)                     |
| **Keeps old fields?**         | ❌ No                                                            | ✅ Yes (if not updated)                                   |
| **Example Usage**             | `replaceOne({ "name": "John" }, { "name": "John", "age": 30 })` | `updateOne({ "name": "John" }, { $set: { "age": 30 } })` |

---

### When to Use `replaceOne()`?

- ✅ When you want to **completely overwrite** an existing document.
- ❌ When you just need to update **specific fields** (use `updateOne()` instead).

Would you like an example where `replaceOne()` is used with upsert? 🚀

### **Update Operators
MongoDB provides several operators to update fields within a document:
- `$set`: Sets the value of a field.
- `$unset`: Removes the specified field.
- `$inc`: Increments the value of a field.
- `$rename`: Renames a field.

Example using multiple operators:
```javascript
db.collection.updateOne(
   { name: "John Doe" },
   {
     $set: { age: 32 },
     $inc: { visits: 1 },
     $rename: { city: "location" }
   }
)
```
This query updates the `age` field to 32, increments the `visits` field by 1, and renames the `city` field to `location`.

Update queries are powerful tools for modifying your data efficiently. If you have more questions or need further examples, feel free to ask! 😊

# **Upsert

**Upsert** is a combination of **update** and **insert** in MongoDB. It is a special option used with the `update` operation. When you use **upsert**, MongoDB will try to **update** an existing document that matches the filter condition. If no document matches the condition, MongoDB will **insert** a new document instead.

### Key Points:

- **Update**: If a document matching the filter exists, MongoDB will update it with the new values.
- **Insert**: If no matching document is found, MongoDB will create a new document with the specified fields.

### Syntax:

The upsert option is used with the `updateOne` or `updateMany` methods by setting the `upsert` flag to `true`.

```js
db.collection.updateOne(
  { _id: 1 }, // Filter condition (e.g., match document with _id = 1)
  { $set: { name: "John Doe" } }, // Update operation
  { upsert: true } // Enable upsert (will insert if no document matches)
);
```

### Example 1: **Update Existing Document**

If a document with `_id: 1` exists, the `name` field will be updated to `"John Doe"`. If it does not exist, a new document will be created with `_id: 1` and `name: "John Doe"`.

### Example 2: **Insert New Document**

If no document with `_id: 1` exists, the operation will insert a new document like this:

```json
{
  "_id": 1,
  "name": "John Doe"
}
```

### Use Case:

- **Upsert** is useful when you are unsure if a document already exists and you want to ensure either an update happens, or a new document is created if it doesn’t exist.

### Is Upsert only used with Update?

Yes, upsert is mainly used with the **update** operation (e.g., `updateOne`, `updateMany`), because it combines the behavior of updating and inserting a document. It cannot be used with other operations like `find`, `insert`, or `remove`.

### Why use Upsert?

- **Efficiency**: Instead of doing a separate `find` to check if a document exists and then deciding whether to update or insert, you can do it all in one operation.
- **Simplicity**: It simplifies your code, as you don't need to handle checking if the document exists beforehand.

### Example Scenario:

Let’s say you are tracking a user’s last login time. If the user exists in the database, you want to update their last login time; if they don't exist, you want to create a new document for them.

```js
db.users.updateOne(
  { username: "john_doe" }, // Filter by username
  { $set: { lastLogin: new Date() } }, // Update last login time
  { upsert: true } // If no such user exists, create one
);
```

In this case:

- If `john_doe` exists, it updates the `lastLogin` field.
- If `john_doe` does not exist, it creates a new document for `john_doe` with a `lastLogin` field.

### In Short:

- **Upsert** is used in the `update` operation to either **update** an existing document or **insert** a new one if the document doesn't exist.
- It is only applicable to **update** operations (`updateOne`, `updateMany`).

Let me know if that clears things up!
# **Update operators

 list of update operators:

- `$set`
- `$unset`
- `$inc`
- `$mul`
- `$rename`
- `$min`
- `$max`
- `$currentDate`
- `$addToSet`
- `$push`
- `$pull`
- `$pop`
## **i. $set 

The `$set` operator in MongoDB is used in update queries to update specific fields of a document without modifying the rest of the document. If the field does not exist, `$set` will create it.

### **Syntax:**

```json
db.collection.updateOne(
   { <query> },
   { $set: { <field1>: <value1>, <field2>: <value2> } }
)
```

or

```json
db.collection.updateMany(
   { <query> },
   { $set: { <field1>: <value1>, <field2>: <value2> } }
)
```

### **Example:**

#### **Updating a single document**

```json
db.users.updateOne(
   { "name": "John" },
   { $set: { "age": 30, "city": "New York" } }
)
```

✅ This updates **John's** `age` to `30` and `city` to `"New York"` while keeping other fields unchanged.

#### **Updating multiple documents**

```json
db.users.updateMany(
   { "status": "inactive" },
   { $set: { "status": "active" } }
)
```

✅ This updates **all** users who have `"status": "inactive"` to `"status": "active"`.



## **ii. $unset

The `$unset` operator in MongoDB is used to **remove specific fields** from a document. If the field exists, `$unset` will delete it; if the field does not exist, it does nothing.

### **Syntax:**

```json
db.collection.updateOne(
   { <query> },
   { $unset: { <field1>: "", <field2>: "" } }
)
```

or

```json
db.collection.updateMany(
   { <query> },
   { $unset: { <field1>: "", <field2>: "" } }
)
```

### **Example:**

#### **Removing a single field**

```json
db.users.updateOne(
   { "name": "John" },
   { $unset: { "age": "" } }
)
```

✅ This removes the `"age"` field from John's document.

#### **Removing multiple fields**

```json
db.users.updateMany(
   { "status": "inactive" },
   { $unset: { "lastLogin": "", "tempData": "" } }
)
```

✅ This removes both `"lastLogin"` and `"tempData"` fields from **all** users who have `"status": "inactive"`.

## **iii) $rename

The `$rename` operator is used to **change the name of a field** in a MongoDB document. Instead of manually retrieving a document, removing a field, and adding a new field, `$rename` lets you rename it in a **single update operation**.

---

### Syntax:

```json
db.collection.updateOne(
   { <query> },
   { $rename: { "<oldFieldName>": "<newFieldName>" } }
)
```

or

```json
db.collection.updateMany(
   { <query> },
   { $rename: { "<oldFieldName>": "<newFieldName>" } }
)
```

---

### Example: Renaming a Single Field

```json
db.users.updateOne(
   { "name": "John" },
   { $rename: { "phoneNumber": "contactNumber" } }
)
```

✅ **What happens here?**

- The field `"phoneNumber"` is **renamed** to `"contactNumber"` for the user **John**.

---

### Example: Renaming Multiple Fields

```json
db.users.updateOne(
   { "name": "Alice" },
   { $rename: { "dob": "dateOfBirth", "addr": "address" } }
)
```

✅ **What happens here?**

- `"dob"` is renamed to `"dateOfBirth"`.
- `"addr"` is renamed to `"address"`.

---

### Example: Renaming Fields in Multiple Documents

```json
db.users.updateMany(
   { "status": "active" },
   { $rename: { "created_at": "registrationDate" } }
)
```

✅ **What happens here?**

- `"created_at"` is renamed to `"registrationDate"` **for all users** with `"status": "active"`.

---

### Important Notes:

✔ **Data is not lost** – Only the field name changes, not the value.  
✔ **Cannot rename to an existing field** – The new name must be **unique** in the document.  
✔ **Can be combined with other update operators** like `$set`, `$unset`, `$inc`, etc.

## **iv. $currentDate

The `$currentDate` operator sets a field to the **current date and time** when updating a document. It is often used for **timestamps**, tracking updates, and maintaining `createdAt` or `updatedAt` fields.

---

### **Syntax:**

```json
db.collection.updateOne(
   { <query> },
   { $currentDate: { "<fieldName>": <typeSpecifier> } }
)
```

or

```json
db.collection.updateMany(
   { <query> },
   { $currentDate: { "<fieldName>": <typeSpecifier> } }
)
```

👉 The `<typeSpecifier>` can be:

- `true` → Sets the field to the current date as an ISODate (`Date` type).
- `{ $type: "timestamp" }` → Stores the value as a BSON `Timestamp`.

---

### **Example: Setting an `updatedAt` Timestamp**

```json
db.users.updateOne(
   { "name": "John" },
   { $currentDate: { "updatedAt": true } }
)
```

✅ **What happens here?**

- The `"updatedAt"` field is set to the **current date and time** (`ISODate`).

---

### **Example: Using `$type: "timestamp"`**

```json
db.users.updateOne(
   { "name": "Alice" },
   { $currentDate: { "lastLogin": { "$type": "timestamp" } } }
)
```

✅ **What happens here?**

- The `"lastLogin"` field is set to a **BSON Timestamp** instead of a standard Date.

---

### **Example: Updating Multiple Documents**

```json
db.orders.updateMany(
   { "status": "shipped" },
   { $currentDate: { "lastUpdated": true } }
)
```

✅ **What happens here?**

- The `"lastUpdated"` field is set to the **current date and time** for all documents where `"status": "shipped"`.

---

### **Combining `$currentDate` with Other Update Operators**

You can use `$currentDate` along with other update operators like `$set` and `$inc`.

```json
db.products.updateOne(
   { "productId": 101 },
   { 
      $set: { "status": "sold" }, 
      $currentDate: { "lastSold": true }
   }
)
```

✅ **What happens here?**

- The `"status"` field is updated to `"sold"`.
- The `"lastSold"` field is set to the **current date and time**.

---

### **Key Takeaways:**

✔ **Automatically updates timestamps** without manual date handling.  
✔ **Can store as either `Date` or `Timestamp` format.**  
✔ **Can be combined** with `$set`, `$inc`, `$unset`, etc.  
✔ **Useful for tracking updates and modifications in documents.**

Would you like an example using `$currentDate` with an upsert operation? 🚀



# **Array update operators

1️⃣ **`$push`** – Add an element to an array  
2️⃣ **`$addToSet`** – Add a unique element (prevents duplicates)  
3️⃣ **`$pop`** – Remove the first (`-1`) or last (`1`) element  
4️⃣ **`$pull`** – Remove specific elements from an array  
5️⃣ **`$pullAll`** – Remove multiple specified values  
6️⃣ **`$each`** – Add multiple elements with `$push`  
7️⃣ **`$slice`** – Limit array size when adding elements  
8️⃣ **`$sort`** – Sort array elements while adding  
9️⃣ **`$set`** – Update an array element at a specific index

commonly used [[$push, $each,  $addToSet,  $pop,  $pull,  $pullAll,  $sort 

## **i) $push, $each, $sort

### **Understanding `$push`, `$each`, and `$sort` in MongoDB (For Beginners)**

MongoDB allows you to update array fields inside documents using the **`$push`** operator. To **add multiple elements**, we use **`$each`**, and to **sort the array after inserting elements**, we use **`$sort`**.

---

### **1️⃣ `$push` – Add Elements to an Array**

`$push` is used to add **one or more elements** to an array in a MongoDB document.

### **Example 1: Adding a Single Element**

```json
db.users.updateOne(
   { "name": "John" },
   { $push: { "hobbies": "reading" } }
)
```

✅ **Before:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling"] }
```

✅ **After `$push`:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling", "reading"] }
```

📌 **`"reading"` is added to the `"hobbies"` array.**

---

### **2️⃣ `$each` – Add Multiple Elements to an Array**

`$each` is used **inside** `$push` to **add multiple elements at once** instead of making multiple update calls.

### **Example 2: Adding Multiple Elements with `$each`**

```json
db.users.updateOne(
   { "name": "John" },
   { $push: { "hobbies": { $each: ["gaming", "coding"] } } }
)
```

✅ **Before:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling"] }
```

✅ **After `$each`:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling", "gaming", "coding"] }
```

📌 Both `"gaming"` and `"coding"` are added at the same time.

---

### **3️⃣ `$sort` – Sort an Array While Pushing Elements**

`$sort` is used **inside `$push`** to **automatically arrange elements** in ascending (`1`) or descending (`-1`) order after adding them.

**`$sort` cannot be used alone** in an update operation. It must always be used **inside** `$push` when adding elements to an array.

If you want to sort an existing array without adding new elements, you must **use `$set` with aggregation (`$sortArray`)** in MongoDB 5.2+.

### **Example 3: Adding and Sorting Scores Automatically**

```json
db.users.updateOne(
   { "name": "John" },
   { $push: { "scores": { $each: [85, 90, 100], $sort: 1 } } }
)
```

✅ **Before:**

```json
{ "name": "John", "scores": [95, 80] }
```

✅ **After `$each` with `$sort`:**

```json
{ "name": "John", "scores": [80, 85, 90, 95, 100] }
```

📌 The array is **automatically sorted in ascending order**.

---

### **📌 Sorting in Descending Order (`$sort: -1`)**

```json
db.users.updateOne(
   { "name": "John" },
   { $push: { "scores": { $each: [70, 75, 85], $sort: -1 } } }
)
```

✅ **Before:**

```json
{ "name": "John", "scores": [95, 80] }
```

✅ **After `$sort: -1`:**

```json
{ "name": "John", "scores": [95, 85, 80, 75, 70] }
```

📌 The array is **sorted in descending order** (largest to smallest).

---

### **🔹 Quick Summary**

|Operator|Purpose|
|---|---|
|**`$push`**|Adds one or more elements to an array|
|**`$each`**|Allows multiple elements to be added at once|
|**`$sort`**|Sorts elements in ascending (`1`) or descending (`-1`) order|
## **ii) $addToSet

#### **What is `$addToSet`?**

- `$addToSet` **adds an element to an array** **only if it doesn’t already exist**.
- It **prevents duplicates** automatically.
- If the array does not exist, MongoDB **creates it** and adds the element.

---

### **1️⃣ Basic Example: Preventing Duplicates**

#### **Add a hobby only if it’s not already in the array**

```json
db.users.updateOne(
   { "name": "John" },
   { $addToSet: { "hobbies": "reading" } }
)
```

✅ **Before:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling"] }
```

✅ **After:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling", "reading"] }
```

📌 `"reading"` is added because it **wasn't in the array before**.

✅ **If `"reading"` already exists, nothing changes.**

---

### **2️⃣ Using `$addToSet` with Multiple Elements (`$each`)**

Since `$addToSet` only accepts **one** value, we use `$each` to add **multiple elements**.

```json
db.users.updateOne(
   { "name": "John" },
   { $addToSet: { "hobbies": { $each: ["music", "traveling", "sports"] } } }
)
```

✅ **Before:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling", "reading"] }
```

✅ **After:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling", "reading", "music", "sports"] }
```

📌 `"traveling"` was **not added again** (already exists).

---

### **3️⃣ Difference Between `$push` and `$addToSet`**

|Operator|Adds Duplicates?|Adds Multiple Elements?|Example Usage|
|---|---|---|---|
|**`$push`**|✅ Yes|✅ Yes (with `$each`)|Adding scores, timestamps|
|**`$addToSet`**|❌ No|✅ Yes (with `$each`)|Adding unique tags, categories|

---

### **📌 When to Use `$addToSet`?**

- When you **want to avoid duplicates** in an array.
- When working with **tags, categories, or unique lists**.
- When you **don’t want to manually check if an item exists** before adding it.

Would you like an example with nested documents? 🚀😊


## **iii) $pop

### **MongoDB `$pop` Operator**

#### **What is `$pop`?**

`$pop` is used to **remove** an element from the beginning or end of an array.

---

### **1️⃣ Remove the Last Element (`$pop: 1`)**

Removes the **last element** from an array.

```json
db.users.updateOne(
   { "name": "John" },
   { $pop: { "hobbies": 1 } }
)
```

✅ **Before:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling", "reading"] }
```

✅ **After:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling"] }
```

📌 The **last element (`"reading"`) is removed.**

---

### **2️⃣ Remove the First Element (`$pop: -1`)**

Removes the **first element** from an array.

```json
db.users.updateOne(
   { "name": "John" },
   { $pop: { "hobbies": -1 } }
)
```

✅ **Before:**

```json
{ "name": "John", "hobbies": ["swimming", "traveling", "reading"] }
```

✅ **After:**

```json
{ "name": "John", "hobbies": ["traveling", "reading"] }
```

📌 The **first element (`"swimming"`) is removed.**

---

### **📌 Key Takeaways**

|Command|Effect|
|---|---|
|**`$pop: 1`**|Removes the **last** element|
|**`$pop: -1`**|Removes the **first** element|

### **MongoDB `$pop` with Nested Arrays**

#### **Example: Removing Elements from a Nested Array**

Let's say we have a collection `students` with an array field `subjects` inside a nested `grades` object.

#### **Sample Document:**

```json
{
   "_id": 1,
   "name": "Alice",
   "grades": {
      "subjects": ["Math", "Science", "History", "English"]
   }
}
```

---

### **1️⃣ Removing the Last Subject from `grades.subjects` (`$pop: 1`)**

```json
db.students.updateOne(
   { "name": "Alice" },
   { $pop: { "grades.subjects": 1 } }
)
```

✅ **Before:**

```json
{
   "_id": 1,
   "name": "Alice",
   "grades": {
      "subjects": ["Math", "Science", "History", "English"]
   }
}
```

✅ **After:**

```json
{
   "_id": 1,
   "name": "Alice",
   "grades": {
      "subjects": ["Math", "Science", "History"]
   }
}
```

📌 **The last subject (`"English"`) is removed.**

---

### **2️⃣ Removing the First Subject from `grades.subjects` (`$pop: -1`)**

```json
db.students.updateOne(
   { "name": "Alice" },
   { $pop: { "grades.subjects": -1 } }
)
```

✅ **Before:**

```json
{
   "_id": 1,
   "name": "Alice",
   "grades": {
      "subjects": ["Math", "Science", "History", "English"]
   }
}
```

✅ **After:**

```json
{
   "_id": 1,
   "name": "Alice",
   "grades": {
      "subjects": ["Science", "History", "English"]
   }
}
```

📌 **The first subject (`"Math"`) is removed.**

---

### **📌 Summary**

|Command|Effect|
|---|---|
|**`$pop: 1`**|Removes the **last** element from the array|
|**`$pop: -1`**|Removes the **first** element from the array|
|**Works on Nested Arrays?**|✅ Yes, by using **dot notation** (e.g., `"grades.subjects"`)|


## **iv) $pull

The **`$pull`** operator is used to **remove elements from an array** **based on a condition**.  
It is useful when you want to delete **specific values** or **objects** inside an array.

---

### **1️⃣ Basic Syntax**

```json
db.collection.updateOne(
   { <query> }, 
   { $pull: { <arrayField>: <condition> } }
)
```

✅ **`$pull` removes matching elements** from an array.

---

### **2️⃣ Example 1: Removing a Simple Value from an Array**

Let's say we have this **`users`** collection:

### **🔹 Sample Data Before Update**

```json
{
   "_id": 1,
   "name": "John",
   "hobbies": ["reading", "gaming", "swimming"]
}
```

### **🔄 Remove `"gaming"` from the `hobbies` Array**

```json
db.users.updateOne(
   { "name": "John" },
   { $pull: { "hobbies": "gaming" } }
)
```

### ✅ **Updated Data After Execution**

```json
{
   "_id": 1,
   "name": "John",
   "hobbies": ["reading", "swimming"]
}
```

📌 **`"gaming"` is removed from `hobbies`!**

---

### **3️⃣ Example 2: Removing Multiple Matching Values**

Let's say the `tags` array has **duplicate or unnecessary values**:

### **🔹 Sample Data Before Update**

```json
{
   "_id": 2,
   "name": "Alice",
   "tags": ["red", "blue", "green", "blue"]
}
```

### **🔄 Remove All `"blue"` Values**

```json
db.users.updateOne(
   { "name": "Alice" },
   { $pull: { "tags": "blue" } }
)
```

### ✅ **Updated Data After Execution**

```json
{
   "_id": 2,
   "name": "Alice",
   "tags": ["red", "green"]
}
```

📌 **All `"blue"` values were removed!**

---

### **4️⃣ Example 3: Removing Objects from an Array**

If an array contains **objects**, `$pull` can remove objects that **match a condition**.

### **🔹 Sample Data Before Update**

```json
{
   "_id": 3,
   "name": "Mike",
   "contacts": [
      { "type": "email", "value": "mike@example.com" },
      { "type": "phone", "value": "+1234567890" },
      { "type": "email", "value": "mike.work@example.com" }
   ]
}
```

### **🔄 Remove All `email` Type Contacts**

```json
db.users.updateOne(
   { "name": "Mike" },
   { $pull: { "contacts": { "type": "email" } } }
)
```

### ✅ **Updated Data After Execution**

```json
{
   "_id": 3,
   "name": "Mike",
   "contacts": [
      { "type": "phone", "value": "+1234567890" }
   ]
}
```

📌 **Both `email` contacts are removed because they match the condition!**

---

### **5️⃣ Example 4: Removing Elements Based on a Condition**

We can use **comparison operators** like `$lt`, `$gt`, `$in`, etc., inside `$pull`.

### **🔹 Sample Data Before Update**

```json
{
   "_id": 4,
   "name": "Emma",
   "scores": [98, 45, 67, 29, 88]
}
```

### **🔄 Remove All Scores Less Than `50` (`$lt: 50`)**

```json
db.users.updateOne(
   { "name": "Emma" },
   { $pull: { "scores": { $lt: 50 } } }
)
```

### ✅ **Updated Data After Execution**

```json
{
   "_id": 4,
   "name": "Emma",
   "scores": [98, 67, 88]
}
```

📌 **`45` and `29` were removed because they are less than `50`!**

---

###
**📌 Key Takeaways**

|Feature|Description|
|---|---|
|**Removes elements from an array**|`$pull` removes **specific values or objects** from an array.|
|**Works with simple values**|`{ $pull: { hobbies: "gaming" } }` removes `"gaming"`.|
|**Works with objects**|`{ $pull: { contacts: { type: "email" } } }` removes all objects where `"type": "email"`.|
|**Supports conditions**|`{ $pull: { scores: { $lt: 50 } } }` removes **all numbers less than 50**.|
|**Removes multiple matches**|All matching elements will be removed.|

---

## **v) $pullAll

The **`$pullAll`** operator is similar to **`$pull`**, but instead of removing elements **based on a condition**, it removes **multiple specific values** from an array at once.

---

### **1. Basic Syntax**

```json
db.collection.updateOne(
   { <query> }, 
   { $pullAll: { <arrayField>: [<value1>, <value2>, ...] } }
)
```

**`$pullAll` removes multiple specified values from an array**.

---

### **2. Example 1: Removing Multiple Values from an Array**

Let's say we have this **`users`** collection:

### **Sample Data Before Update**

```json
{
   "_id": 1,
   "name": "John",
   "hobbies": ["reading", "gaming", "swimming", "cycling", "gaming"]
}
```

### **Remove `"gaming"` and `"cycling"` from the `hobbies` Array**

```json
db.users.updateOne(
   { "name": "John" },
   { $pullAll: { "hobbies": ["gaming", "cycling"] } }
)
```

### **Updated Data After Execution**

```json
{
   "_id": 1,
   "name": "John",
   "hobbies": ["reading", "swimming"]
}
```

Both `"gaming"` and `"cycling"` were removed from the array.

---

### **3. Example 2: Removing Multiple Numbers from an Array**

### **Sample Data Before Update**

```json
{
   "_id": 2,
   "name": "Alice",
   "scores": [98, 45, 67, 29, 88, 45, 67]
}
```

### **Remove `45` and `67` from `scores`**

```json
db.users.updateOne(
   { "name": "Alice" },
   { $pullAll: { "scores": [45, 67] } }
)
```

### **Updated Data After Execution**

```json
{
   "_id": 2,
   "name": "Alice",
   "scores": [98, 29, 88]
}
```

All occurrences of `45` and `67` were removed.

---

### **4. Difference Between `$pull` and `$pullAll`**


|Feature|`$pull`|`$pullAll`|
|---|---|---|
|**Removes specific values**|✅ Yes|✅ Yes|
|**Removes all occurrences**|✅ Yes|✅ Yes|
|**Removes based on a condition**|✅ Yes (`$gt`, `$lt`, etc.)|❌ No|
|**Can remove objects from an array**|✅ Yes|❌ No|

---

### **Example Comparison**

If we want to remove **all values less than 50**, we use **`$pull`**:

```json
db.users.updateOne(
   { "name": "Alice" },
   { $pull: { "scores": { $lt: 50 } } }
)
```

This removes only numbers **less than 50** (e.g., `45` & `29`).

If we want to remove only **specific numbers (e.g., `45` and `67`)**, we use **`$pullAll`**:

```json
db.users.updateOne(
   { "name": "Alice" },
   { $pullAll: { "scores": [45, 67] } }
)
```

This removes only `45` and `67`, even if they are greater than `50`.

---

### **5. Key Takeaways**

|Feature|Description|
|---|---|
|**Removes multiple specific values**|`$pullAll` removes only **the values you specify**, nothing else.|
|**Works with arrays of numbers or strings**|`{ $pullAll: { tags: ["red", "blue"] } }` removes both `"red"` and `"blue"`.|
|**Does not work with conditions**|Unlike `$pull`, `$pullAll` cannot use `$lt`, `$gt`, etc.|
|**Removes all occurrences of specified values**|If a value appears multiple times in the array, **all instances are removed**.|



## **vi) $ positional operator & $`[]`

The **`$` positional operator** in MongoDB is used to **update specific elements** in an array when you don’t know their exact index. It matches the **first element** in the array that satisfies the query condition.

---

### **🔹 Syntax**

```json
db.collection.updateOne(
   { <query-condition> },
   { $set: { "array.$": <new-value> } }
)
```

- The `$` operator **replaces only the first matching element** inside an array.

---

### **🔹 Example 1: Updating a Specific Element in an Array**

### **📌 Before Update**

```json
{
   "_id": 1,
   "name": "Alice",
   "scores": [45, 78, 90]
}
```

### **✅ Query: Update the first element that is `78` to `85`**

```json
db.students.updateOne(
   { "scores": 78 },
   { $set: { "scores.$": 85 } }
)
```

### **🔹 After Update**

```json
{
   "_id": 1,
   "name": "Alice",
   "scores": [45, 85, 90]
}
```

✅ **Only the first matching `78` is replaced with `85`.**

---

### **🔹 Example 2: Updating a Specific Field in an Object Inside an Array**

If we have **nested objects inside an array**, `$` helps update the right object.

### **📌 Before Update**

```json
{
   "_id": 2,
   "name": "John",
   "contacts": [
      { "type": "email", "value": "john@example.com" },
      { "type": "phone", "value": "+1234567890" }
   ]
}
```

### **✅ Query: Update John's Email**

```json
db.users.updateOne(
   { "contacts.type": "email" },
   { $set: { "contacts.$.value": "john.new@example.com" } }
)
```

### **🔹 After Update**

```json
{
   "_id": 2,
   "name": "John",
   "contacts": [
      { "type": "email", "value": "john.new@example.com" },
      { "type": "phone", "value": "+1234567890" }
   ]
}
```

✅ **Only the email field was updated!**

---

### **🔹 Limitations of `$` Operator**

❌ Only works on **the first matching element**  
❌ Cannot be used for **multiple updates in one command**

For **updating multiple elements**, use `$[<identifier>]` with **arrayFilters**.

---
### **🔹 `$[]` (Positional All Operator)

The **`$[]` operator** is used when you want to **update all elements** of an array **at once**. Unlike `$`, which updates only the first matching element, `$[]` applies the update to **every** element in the array.

---

### **1️⃣ Basic Example: Updating All Elements in an Array**

### **📌 Before Update**

```json
{
   "_id": 1,
   "name": "Alice",
   "scores": [45, 78, 90, 55]
}
```

### **✅ Query: Add 5 to Every Score**

```json
db.students.updateOne(
   { "name": "Alice" },
   { $inc: { "scores.$[]": 5 } }
)
```

### **🔹 After Update**

```json
{
   "_id": 1,
   "name": "Alice",
   "scores": [50, 83, 95, 60]
}
```

✅ **Every element in `scores` array increased by 5!**

---

### **2️⃣ Example: Setting a Default Value for All Elements**

If we want to **set all elements** of an array to `"pending"`:

### **📌 Before Update**

```json
{
   "_id": 2,
   "tasks": ["in progress", "done", "not started"]
}
```

### **✅ Query: Set All Tasks to `"pending"`**

```json
db.tasks.updateOne(
   { _id: 2 },
   { $set: { "tasks.$[]": "pending" } }
)
```

### **🔹 After Update**

```json
{
   "_id": 2,
   "tasks": ["pending", "pending", "pending"]
}
```

✅ **All elements are now `"pending"`!**

---

### **3️⃣ Updating All Objects in an Array of Objects**

If an array contains **objects**, `$[]` can be used to **update a field in every object**.

### **📌 Before Update**

```json
{
   "_id": 3,
   "name": "John",
   "contacts": [
      { "type": "email", "value": "john@example.com", "verified": false },
      { "type": "phone", "value": "+1234567890", "verified": false }
   ]
}
```

### **✅ Query: Mark All Contacts as Verified**

```json
db.users.updateOne(
   { _id: 3 },
   { $set: { "contacts.$[].verified": true } }
)
```

### **🔹 After Update**

```json
{
   "_id": 3,
   "name": "John",
   "contacts": [
      { "type": "email", "value": "john@example.com", "verified": true },
      { "type": "phone", "value": "+1234567890", "verified": true }
   ]
}
```

✅ **All `verified` fields were set to `true`!**

---

### **🔹 Key Differences Between `$` and `$[]`**

|Operator|Updates|Works On|
|---|---|---|
|**`$`**|First matching element only|Single update|
|**`$[]`**|All elements in the array|Bulk update|

---

### **🔹 Final Thoughts**

- Use **`$[]`** when you need to **update every element** in an array.
- If you only need to update **some elements** based on a condition, use **`$[identifier]` with `arrayFilters`** (e.g., `$[lowScores]` for scores below 50).




## **vii) update with arrayFilters $`[identifer]`


MongoDB's **`$[<identifier>]` + `arrayFilters`** allows you to **update specific elements inside an array** without affecting others.

---

### **🔹 Why Do We Need `arrayFilters`?**

Normally, we can update **the first matching element** in an array using **the `$` positional operator**, but what if we want to update **multiple specific elements** based on conditions?

That’s where **`arrayFilters`** helps!

---

### **🚀 Basic Syntax**

```json
db.collection.updateOne(
   { <query> },
   { $set: { "arrayField.$[identifier]": <new_value> } },
   { arrayFilters: [ { "identifier.<condition>" } ] }
)
```

### **🛠 Key Parts**

1️⃣ **`"arrayField.$[identifier]"`** → Specifies which elements inside the array should be updated.  
2️⃣ **`arrayFilters: [ { "identifier.<condition>" } ]`** → Defines which array elements should be modified.  
3️⃣ **`identifier` (custom name)** → A variable that represents **each element in the array** while filtering.

---

### **📍 Example 1: Update a Specific Element in an Array**

### **🎯 Task: Increase Math score for all students who scored below 80**

### **🔹 Sample Data (Before Update)**

```json
{
   "_id": 1,
   "name": "Alice",
   "scores": [
      { "subject": "Math", "score": 75 },
      { "subject": "Science", "score": 90 }
   ]
}
```

### **✅ Update Query**

```json
db.students.updateOne(
   { "name": "Alice" },
   { $set: { "scores.$[elem].score": 80 } },
   { arrayFilters: [ { "elem.subject": "Math", "elem.score": { $lt: 80 } } ] }
)
```

✔ **Explanation:**

- `"scores.$[elem].score": 80` → Updates only elements in the `"scores"` array that match the filter.
- **`arrayFilters`**: `{ "elem.subject": "Math", "elem.score": { $lt: 80 } }` → Targets only **Math scores below 80**.

### **🔹 Updated Data (After Execution)**

```json
{
   "_id": 1,
   "name": "Alice",
   "scores": [
      { "subject": "Math", "score": 80 },  ✅ Updated!
      { "subject": "Science", "score": 90 } ❌ Unchanged
   ]
}
```

---

### **📍 Example 2: Update Multiple Matching Elements**

### **🎯 Task: Change `"Pending"` status to `"In Progress"` for specific projects**

### **🔹 Sample Data (Before Update)**

```json
{
   "_id": 101,
   "name": "John",
   "projects": [
      { "title": "Website Redesign", "status": "Pending" },
      { "title": "Mobile App", "status": "In Progress" },
      { "title": "SEO Optimization", "status": "Pending" }
   ]
}
```

### **✅ Update Query**

```json
db.employees.updateOne(
   { "name": "John" },
   { $set: { "projects.$[task].status": "In Progress" } },
   { arrayFilters: [ { "task.status": "Pending" } ] }
)
```

✔ **Explanation:**

- `"projects.$[task].status": "In Progress"` → Updates the `"status"` field inside the `"projects"` array.
- **`arrayFilters`**: `{ "task.status": "Pending" }` → Targets **only the elements where `"status"` is `"Pending"`**.

### **🔹 Updated Data (After Execution)**

```json
{
   "_id": 101,
   "name": "John",
   "projects": [
      { "title": "Website Redesign", "status": "In Progress" },  ✅ Updated!
      { "title": "Mobile App", "status": "In Progress" },        ❌ Unchanged
      { "title": "SEO Optimization", "status": "In Progress" }   ✅ Updated!
   ]
}
```

---

### **📍 Example 3: Increase Salary for Employees Based on a Condition**

### **🎯 Task: Increase salary for employees earning less than `50000`**

### **🔹 Sample Data (Before Update)**

```json
{
   "_id": 301,
   "name": "Emma",
   "salaries": [
      { "year": 2022, "amount": 45000 },
      { "year": 2023, "amount": 52000 }
   ]
}
```

### **✅ Update Query**

```json
db.employees.updateOne(
   { "name": "Emma" },
   { $inc: { "salaries.$[salary].amount": 5000 } },
   { arrayFilters: [ { "salary.amount": { $lt: 50000 } } ] }
)
```

✔ **Explanation:**

- `"$inc"` → Increases `"amount"` by `5000`.
- **`arrayFilters`**: `{ "salary.amount": { $lt: 50000 } }` → Applies only to salaries **less than 50000**.

### **🔹 Updated Data (After Execution)**

```json
{
   "_id": 301,
   "name": "Emma",
   "salaries": [
      { "year": 2022, "amount": 50000 }, ✅ Updated!
      { "year": 2023, "amount": 52000 }  ❌ Unchanged
   ]
}
```

---

### **💡 When to Use `$[]` Instead of `$[<identifier>]`?**

### **✅ `$[<identifier>]` → Updates only elements that match a condition**

- Example: Update only `"Math"` scores below `80`.

### **✅ `$[]` → Updates all elements inside an array**

- Example: Increase all scores in an array, regardless of subject.

```json
db.students.updateOne(
   { "name": "Alice" },
   { $inc: { "scores.$[].score": 5 } }
)
```

✔ **This updates all elements inside the `scores` array!**

---

### **📌 Summary**

|Feature|`$[]` (Wildcard)|`$[<identifier>] + arrayFilters`|
|---|---|---|
|**Updates all elements?**|✅ Yes|❌ No (Only matching elements)|
|**Needs conditions?**|❌ No|✅ Yes|
|**Example use case**|Increase all prices by 10%|Update specific elements based on conditions|

---

### **🎯 Key Takeaways**

✔ **`$[<identifier>]` + `arrayFilters` lets you update specific elements inside an array based on conditions.**  
✔ Useful when **multiple elements in an array match a condition**, and **you don’t want to update all of them**.  
✔ **`$[]` updates all elements inside the array, while `$[<identifier>]` is selective.**


# **Array Query Operators

### **🔹 List of Array Query Operators in MongoDB**

MongoDB provides several operators to **query arrays** efficiently. Here’s a list:

#### **1️⃣ `$all`** – Matches documents where an array contains **all the specified values**.

#### **2️⃣ `$elemMatch`** – Matches documents where **at least one element** in an array **meets multiple conditions**.

#### **3️⃣ `$size`** – Matches arrays with an **exact number of elements**.

#### **4️⃣ `$in`** – Matches arrays that contain **at least one of the specified values**.

#### **5️⃣ `$nin`** – Matches arrays that **do not contain** any of the specified values.


## **1) $size

The **`$size`** operator is used in MongoDB to **find documents where an array has a specific number of elements**.

---

### **1️⃣ Example: Finding Documents with an Exact Array Size**

📌 **Find students who have exactly 3 subjects in their `subjects` array.**

### **📝 Sample Data**

```json
{
   "_id": 1,
   "name": "Alice",
   "subjects": ["Math", "Science", "English"]
},
{
   "_id": 2,
   "name": "Bob",
   "subjects": ["Math", "Science"]
}
```

### **✅ Query Using `$size`**

```json
db.students.find({
   "subjects": { $size: 3 }
})
```

### **🔹 Result**

```json
{
   "_id": 1,
   "name": "Alice",
   "subjects": ["Math", "Science", "English"]
}
```

✅ **Only Alice's document is returned because her `subjects` array has exactly 3 elements!**

---

### **🔹 Key Points**

✅ `$size` **only works for exact matches** (e.g., `$size: 3`).  
✅ Use `$expr` if you need **greater than (`$gt`) or less than (`$lt`)** conditions.  
✅ Works best when filtering **arrays with a specific number of elements**.


## **2) $all
 

The **`$all`** operator is used to **match arrays that contain all the specified values**, regardless of their order or position.

---

### **1️⃣ Why Use `$all`?**

Normally, when searching for an array, we can use **`$in`**, but it only checks if **at least one value** exists.  
✅ **`$all` ensures that ALL specified values are present in the array.**

---

### **2️⃣ Basic Example: Querying Students with Specific Subjects**

Let’s say we have a **students collection** where each student is enrolled in multiple subjects.

### **📌 Sample Data**

```json
{ "_id": 1, "name": "Alice", "subjects": ["Math", "Science", "English"] }
{ "_id": 2, "name": "Bob", "subjects": ["Math", "History"] }
{ "_id": 3, "name": "Charlie", "subjects": ["Science", "English", "Math"] }
```

### **❌ Problem: If We Use `$in`**

If we try using **`$in`**, it will return **students who have at least one of the values**, but not necessarily both.

```json
db.students.find({ subjects: { $in: ["Math", "Science"] } })
```

### **🔹 Output**

```json
{ "_id": 1, "name": "Alice", "subjects": ["Math", "Science", "English"] }
{ "_id": 2, "name": "Bob", "subjects": ["Math", "History"] }
{ "_id": 3, "name": "Charlie", "subjects": ["Science", "English", "Math"] }
```

🚫 **Bob is included, but he doesn’t have "Science".**

---

### **✅ Solution: Using `$all` to Require Both Values**

If we want to find **students who have both "Math" and "Science"**, we should use `$all`:

```json
db.students.find({ subjects: { $all: ["Math", "Science"] } })
```

### **🔹 Output**

```json
{ "_id": 1, "name": "Alice", "subjects": ["Math", "Science", "English"] }
{ "_id": 3, "name": "Charlie", "subjects": ["Science", "English", "Math"] }
```

✅ **Only students with both "Math" AND "Science" are included.**

---

### **3️⃣ Example: Querying Products with Multiple Features**

Let’s say we have an **e-commerce collection** where each product has multiple features.

### **📌 Sample Data**

```json
{
   "_id": 101,
   "product": "Laptop",
   "features": ["Touchscreen", "Backlit Keyboard", "8GB RAM"]
}
{
   "_id": 102,
   "product": "Tablet",
   "features": ["Touchscreen", "Portable"]
}
```

### **✅ Query: Find Products That Have Both "Touchscreen" and "Backlit Keyboard"**

```json
db.products.find({ features: { $all: ["Touchscreen", "Backlit Keyboard"] } })
```

### **🔹 Output**

```json
{
   "_id": 101,
   "product": "Laptop",
   "features": ["Touchscreen", "Backlit Keyboard", "8GB RAM"]
}
```

✅ **Only the laptop matches because it has both features.**

---

### **4️⃣ Example: Querying Employees with Required Skills**

Let’s say we have an **employees collection** where each employee has multiple skills.

### **📌 Sample Data**

```json
{
   "_id": 501,
   "name": "John",
   "skills": ["JavaScript", "Python", "React"]
}
{
   "_id": 502,
   "name": "Emma",
   "skills": ["Java", "Python"]
}
{
   "_id": 503,
   "name": "Lucas",
   "skills": ["JavaScript", "React"]
}
```

### **✅ Query: Find Employees Who Have Both "JavaScript" and "React"**

```json
db.employees.find({ skills: { $all: ["JavaScript", "React"] } })
```

### **🔹 Output**

```json
{
   "_id": 501,
   "name": "John",
   "skills": ["JavaScript", "Python", "React"]
}
{
   "_id": 503,
   "name": "Lucas",
   "skills": ["JavaScript", "React"]
}
```

✅ **Both John and Lucas have the required skills.**

---

### **5️⃣ `$all` vs. `$in`**

|Feature|`$all`|`$in`|
|---|---|---|
|**Matches documents containing ALL values**|✅ Yes|❌ No|
|**Matches documents containing AT LEAST one value**|❌ No|✅ Yes|
|**Best for...**|Ensuring multiple required values exist|Finding at least one match|

---

### **6️⃣ Summary**

✔ **`$all` is used to match arrays that contain ALL the specified values.**  
✔ **Order does NOT matter.**  
✔ **Unlike `$in`, it does NOT return results if only one value is present—it requires ALL values.**  
✔ **Useful for filtering students with required subjects, products with features, employees with skills, etc.**

## **3) $elemMatch

The **`$elemMatch`** operator is used to **query arrays of objects**, ensuring that **at least one element** in the array satisfies **multiple conditions**.

---

### **1️⃣ Why Use `$elemMatch`?**

Normally, when querying an array, MongoDB matches elements **independently**. But when we need to check multiple conditions on **the same array element**, we use **`$elemMatch`**.

---

### **2️⃣ Basic Example: Querying Student Scores**

Let’s say we have a **students collection** where each student has multiple scores for different subjects.

### **📌 Sample Data**

```json
{
   "_id": 1,
   "name": "Alice",
   "scores": [
      { "subject": "Math", "score": 95 },
      { "subject": "Science", "score": 80 }
   ]
}
```

### **❌ Problem: Without `$elemMatch`**

Let’s say we want to find students who have:

- **Math score > 90**
- **Science score < 85**

If we try the following query **without `$elemMatch`**, it will return incorrect results:

```json
db.students.find({
   "scores.subject": "Math",
   "scores.score": { $gt: 90 },
   "scores.subject": "Science",
   "scores.score": { $lt: 85 }
})
```

🚫 **This will not work correctly because MongoDB will match these conditions across different elements instead of the same object!**

---

### **✅ Solution: Using `$elemMatch`**

We need to ensure that **a single object** in the `scores` array satisfies both conditions.

```json
db.students.find({
   scores: {
      $elemMatch: { subject: "Math", score: { $gt: 90 } }
   }
})
```

### **🔹 Output**

```json
{
   "_id": 1,
   "name": "Alice",
   "scores": [
      { "subject": "Math", "score": 95 },
      { "subject": "Science", "score": 80 }
   ]
}
```

✅ **Now, MongoDB correctly returns students who have a Math score greater than 90!**

---

### **3️⃣ Example: Finding Products with Specific Reviews**

Let’s say we have an **e-commerce collection** where each product has multiple reviews.

### **📌 Sample Data**

```json
{
   "_id": 101,
   "product": "Laptop",
   "reviews": [
      { "rating": 5, "country": "USA" },
      { "rating": 3, "country": "India" }
   ]
}
```

### **✅ Query: Find Products Where a Review Has**

- **Rating ≥ 4**
- **Country = "USA"**

```json
db.products.find({
   reviews: {
      $elemMatch: { rating: { $gte: 4 }, country: "USA" }
   }
})
```

### **🔹 Output**

```json
{
   "_id": 101,
   "product": "Laptop",
   "reviews": [
      { "rating": 5, "country": "USA" },
      { "rating": 3, "country": "India" }
   ]
}
```

✅ **The query ensures that one specific review meets both conditions.**

---

### **4️⃣ Example: Searching for Employees With a Specific Skill Level**

Let’s say we have a **company database** where employees have multiple skills.

### **📌 Sample Data**

```json
{
   "_id": 501,
   "name": "John",
   "skills": [
      { "name": "JavaScript", "level": "Advanced" },
      { "name": "Python", "level": "Intermediate" }
   ]
}
```

### **✅ Query: Find Employees Who Are "Advanced" in JavaScript**

```json
db.employees.find({
   skills: {
      $elemMatch: { name: "JavaScript", level: "Advanced" }
   }
})
```

### **🔹 Output**

```json
{
   "_id": 501,
   "name": "John",
   "skills": [
      { "name": "JavaScript", "level": "Advanced" },
      { "name": "Python", "level": "Intermediate" }
   ]
}
```

✅ **Only employees with "JavaScript" at "Advanced" level are returned.**

---

### **5️⃣ `$elemMatch` vs. Regular Queries**

|Feature|Without `$elemMatch`|With `$elemMatch`|
|---|---|---|
|**Condition on separate elements?**|✅ Allowed|❌ Not Allowed|
|**Condition on the same element?**|❌ Incorrect results|✅ Ensures conditions match in the same object|
|**Best for...**|Simple queries|Arrays of objects|

---

### **6️⃣ Summary**

✔ **`$elemMatch` is used for querying arrays of objects where multiple conditions must apply to the same element.**  
✔ **It is useful for filtering structured data like reviews, skills, test scores, etc.**  
✔ **Without `$elemMatch`, MongoDB applies conditions independently to all elements in the array.**



## **4) $in and $nin

The **`$in`** and **`$nin`** operators in MongoDB are used to **filter documents based on whether a field's value is present (or not) in a given list of values**.

---

### **1️⃣ What is `$in`?**

✅ The `$in` operator **matches** documents where a field's value is **one of the values** in a specified array.

### **📌 Syntax:**

```json
{ field: { $in: [value1, value2, value3] } }
```

---

### **2️⃣ What is `$nin`?**

🚫 The `$nin` operator **excludes** documents where a field's value is **one of the values** in a specified array.

### **📌 Syntax:**

```json
{ field: { $nin: [value1, value2, value3] } }
```

---

### **3️⃣ Example: Querying Students by Subjects**

Let's say we have a **students collection** where each student has a `favoriteSubject`.

### **📌 Sample Data**

```json
{ "_id": 1, "name": "Alice", "favoriteSubject": "Math" }
{ "_id": 2, "name": "Bob", "favoriteSubject": "Science" }
{ "_id": 3, "name": "Charlie", "favoriteSubject": "English" }
{ "_id": 4, "name": "David", "favoriteSubject": "History" }
```

### **✅ Query: Find Students Who Like "Math" or "Science" (`$in`)**

```json
db.students.find({ favoriteSubject: { $in: ["Math", "Science"] } })
```

### **🔹 Output**

```json
{ "_id": 1, "name": "Alice", "favoriteSubject": "Math" }
{ "_id": 2, "name": "Bob", "favoriteSubject": "Science" }
```

✅ **It returns students whose `favoriteSubject` is either "Math" or "Science".**

---

### **🚫 Query: Find Students Who Do NOT Like "Math" or "Science" (`$nin`)**

```json
db.students.find({ favoriteSubject: { $nin: ["Math", "Science"] } })
```

### **🔹 Output**

```json
{ "_id": 3, "name": "Charlie", "favoriteSubject": "English" }
{ "_id": 4, "name": "David", "favoriteSubject": "History" }
```

✅ **It excludes students who like "Math" or "Science" and returns the rest.**

---

### **4️⃣ Example: Querying Products by Category**

Let's say we have a **products collection** where each product belongs to a `category`.

### **📌 Sample Data**

```json
{ "_id": 101, "product": "Laptop", "category": "Electronics" }
{ "_id": 102, "product": "T-shirt", "category": "Clothing" }
{ "_id": 103, "product": "Headphones", "category": "Electronics" }
{ "_id": 104, "product": "Shoes", "category": "Footwear" }
```

### **✅ Query: Find Products in "Electronics" or "Clothing" (`$in`)**

```json
db.products.find({ category: { $in: ["Electronics", "Clothing"] } })
```

### **🔹 Output**

```json
{ "_id": 101, "product": "Laptop", "category": "Electronics" }
{ "_id": 102, "product": "T-shirt", "category": "Clothing" }
{ "_id": 103, "product": "Headphones", "category": "Electronics" }
```

✅ **It returns only products in "Electronics" or "Clothing".**

---

### **🚫 Query: Find Products That Are NOT in "Electronics" or "Clothing" (`$nin`)**

```json
db.products.find({ category: { $nin: ["Electronics", "Clothing"] } })
```

### **🔹 Output**

```json
{ "_id": 104, "product": "Shoes", "category": "Footwear" }
```

✅ **It excludes "Electronics" and "Clothing" products and returns the rest.**

---

### **5️⃣ `$in` and `$nin` with Arrays**

These operators also work with **arrays inside documents**.

### **📌 Sample Data**

```json
{
   "_id": 1,
   "name": "Alice",
   "hobbies": ["Reading", "Cooking", "Swimming"]
}
{
   "_id": 2,
   "name": "Bob",
   "hobbies": ["Gaming", "Cooking"]
}
{
   "_id": 3,
   "name": "Charlie",
   "hobbies": ["Swimming", "Traveling"]
}
```

### **✅ Query: Find People Who Have "Cooking" or "Swimming" as a Hobby (`$in`)**

```json
db.people.find({ hobbies: { $in: ["Cooking", "Swimming"] } })
```

### **🔹 Output**

```json
{ "_id": 1, "name": "Alice", "hobbies": ["Reading", "Cooking", "Swimming"] }
{ "_id": 2, "name": "Bob", "hobbies": ["Gaming", "Cooking"] }
{ "_id": 3, "name": "Charlie", "hobbies": ["Swimming", "Traveling"] }
```

✅ **Anyone with "Cooking" or "Swimming" is included.**

---

### **🚫 Query: Find People Who Do NOT Have "Cooking" or "Swimming" (`$nin`)**

```json
db.people.find({ hobbies: { $nin: ["Cooking", "Swimming"] } })
```

### **🔹 Output**

```json
{ "_id": 3, "name": "Charlie", "hobbies": ["Swimming", "Traveling"] }
```

✅ **It excludes people who have "Cooking" or "Swimming".**

---

### **6️⃣ `$in` vs. `$nin`**

|Feature|`$in`|`$nin`|
|---|---|---|
|**Includes documents where the field contains any of the values**|✅ Yes|❌ No|
|**Excludes documents where the field contains any of the values**|❌ No|✅ Yes|
|**Works with arrays**|✅ Yes|✅ Yes|
|**Best for...**|Finding specific matches|Filtering out specific values|

---

### **7️⃣ Summary**

✔ **`$in` finds documents where the field matches any value from a given list.**  
✔ **`$nin` excludes documents where the field matches any value from a given list.**  
✔ **Both work with simple fields and arrays inside documents.**  
✔ **Great for filtering by categories, hobbies, skills, or preferences.**



# **📌 Evaluation Query Operators in MongoDB**

1️⃣ **`$expr`** – Allows aggregation expressions in queries.  
2️⃣ **`$jsonSchema`** – Validates documents against a JSON schema.  
3️⃣ **`$mod`** – Filters numbers based on remainder when divided.  
4️⃣ **`$regex`** – Matches text patterns using regular expressions.  
5️⃣ **`$text`** – Performs full-text searches on indexed fields.  
6️⃣ **`$where`** – Uses JavaScript expressions for filtering.
# **Combining Multiple Update Operators in MongoDB**

MongoDB allows multiple update operators (`$set`, `$unset`, `$inc`, `$push`, etc.) to be used **together** in a single update operation. This makes updates more efficient by applying multiple changes in **one query** instead of multiple separate queries.

---

### **Syntax:**

```json
db.collection.updateOne(
   { <query> },
   { 
      <updateOperator1>: { <field1>: <value1>, <field2>: <value2> },
      <updateOperator2>: { <field3>: <value3> }
   }
)
```

---

### **Example: Updating multiple fields at once**

```json
db.users.updateOne(
   { "name": "John" },
   { 
      $set: { "age": 30, "city": "New York" }, 
      $inc: { "loginCount": 1 }, 
      $unset: { "tempData": "" } 
   }
)
```

✅ **What happens here?**

- `$set`: Updates `"age"` to `30` and `"city"` to `"New York"`.
- `$inc`: Increments `"loginCount"` by `1`.
- `$unset`: Removes the `"tempData"` field.

---

### **Example: Updating an array and a field together**

```json
db.users.updateOne(
   { "name": "Alice" },
   { 
      $set: { "status": "active" }, 
      $push: { "hobbies": "reading" }
   }
)
```

✅ **What happens here?**

- `$set`: Updates `"status"` to `"active"`.
- `$push`: Adds `"reading"` to the `"hobbies"` array.

---

### **Example: Updating multiple documents**

```json
db.users.updateMany(
   { "status": "inactive" },
   { 
      $set: { "status": "active" }, 
      $currentDate: { "lastUpdated": true }
   }
)
```

✅ **What happens here?**

- `$set`: Changes `"status"` to `"active"` for all matching documents.
- `$currentDate`: Sets `"lastUpdated"` to the **current timestamp**.

---

### **Key Takeaways**

✔️ You can combine multiple update operators in **one** query.  
✔️ `$set`, `$inc`, `$unset`, `$push`, `$pull`, and `$currentDate` are commonly used together.  
✔️ **Order matters** – MongoDB processes operators in the order they appear.

Would you like more examples with array updates? 🚀
# **updateOne, updateMany() and replaceOne()

In MongoDB, **`updateOne()`** and **`updateMany()`** are methods used to update documents in a collection. Here's an in-depth explanation with simple examples:

---

### **1. `updateOne()`**

- **Purpose**: Updates the first document that matches the given filter.
    
- **Syntax**:
    
    ```javascript
    db.collection.updateOne(filter, update, options)
    ```
    
    - `filter`: Specifies the condition to find the document(s).
    - `update`: Defines how the document(s) should be updated.
    - `options` (optional): Additional options like `upsert` (whether to insert if no document matches).
- **Key Feature**: Only updates the **first matching document**.
    

#### **Example**

Suppose you have a `students` collection:

```json
[
  { "_id": 1, "name": "Alice", "score": 85 },
  { "_id": 2, "name": "Bob", "score": 70 },
  { "_id": 3, "name": "Charlie", "score": 70 }
]
```

**Update the score of the first student with a score of 70 to 75:**

```javascript
db.students.updateOne(
  { score: 70 },                     // Filter: Find a student with score 70
  { $set: { score: 75 } }            // Update: Set the score to 75
);
```

**Result**:

```json
[
  { "_id": 1, "name": "Alice", "score": 85 },
  { "_id": 2, "name": "Bob", "score": 75 },  // Updated!
  { "_id": 3, "name": "Charlie", "score": 70 }
]
```

---

### **2. `updateMany()`**

- **Purpose**: Updates **all documents** that match the given filter.
    
- **Syntax**:
    
    ```javascript
    db.collection.updateMany(filter, update, options)
    ```
    
    - Same parameters as `updateOne()`.
- **Key Feature**: Updates **all matching documents**.
    

#### **Example**

Using the same `students` collection:

**Update the score of all students with a score of 70 to 75:**

```javascript
db.students.updateMany(
  { score: 70 },                     // Filter: Find students with score 70
  { $set: { score: 75 } }            // Update: Set the score to 75
);
```

**Result**:

```json
[
  { "_id": 1, "name": "Alice", "score": 85 },
  { "_id": 2, "name": "Bob", "score": 75 },  // Updated!
  { "_id": 3, "name": "Charlie", "score": 75 }  // Updated!
]
```

---

### **Comparison**

|Feature|`updateOne()`|`updateMany()`|
|---|---|---|
|**Number of Updates**|Updates the **first match only**|Updates **all matches**|
|**Use Case**|Use when only one document needs updating|Use when multiple documents need the same update|

---

### **Options**

Both methods support options like:

1. **`upsert`**: Inserts a new document if no match is found.
    
    ```javascript
    db.students.updateOne(
      { name: "Daisy" },                   // No student named Daisy exists
      { $set: { score: 90 } },             // Insert { name: "Daisy", score: 90 }
      { upsert: true }
    );
    ```
    
2. **Array Filters**: For advanced updates, such as updating specific elements in an array.
    

---

### 3. **replaceOne()**

The `replaceOne()` method in MongoDB is used to **completely replace** an existing document with a new document. Unlike `updateOne()`, which modifies specific fields, `replaceOne()` **replaces the entire document** except for the `_id` field (if it exists in the new document).

---

### Syntax:

```json
db.collection.replaceOne(
   { <filter> },   // Query to find the document
   { <replacementDocument> }  // New document that replaces the old one
)
```

---

### Example:

#### ✅ Replacing a document completely

```json
db.users.replaceOne(
   { "name": "John" },  
   { "name": "John", "age": 30, "city": "New York" }
)
```

🔹 This finds the document where `"name": "John"` and **replaces it entirely** with the new document.  
🔹 If the old document had extra fields (e.g., `"status": "active"`), they will be **removed** unless included in the replacement.

---

### Key Differences Between `replaceOne()` and `updateOne()`

| Feature                       | `replaceOne()`                                                  | `updateOne()`                                            |
| ----------------------------- | --------------------------------------------------------------- | -------------------------------------------------------- |
| **Replaces entire document?** | ✅ Yes                                                           | ❌ No (only modifies specific fields)                     |
| **Keeps old fields?**         | ❌ No                                                            | ✅ Yes (if not updated)                                   |
| **Example Usage**             | `replaceOne({ "name": "John" }, { "name": "John", "age": 30 })` | `updateOne({ "name": "John" }, { $set: { "age": 30 } })` |

---

### When to Use `replaceOne()`?

- ✅ When you want to **completely overwrite** an existing document.
- ❌ When you just need to update **specific fields** (use `updateOne()` instead).

Would you like an example where `replaceOne()` is used with upsert? 🚀



# **deleteOne & deleteMany()


 the `deleteOne()` and `deleteMany()` methods in MongoDB.

### deleteOne()
The `deleteOne()` method is used to remove a single document from a collection that matches a specified filter. If multiple documents match the filter, only the first one encountered will be deleted.

#### Syntax:
```javascript
db.collection.deleteOne(filter, options)
```

- **filter**: A query that matches the document you want to delete.
- **options**: Optional settings for the operation, such as collation.

#### Example:
Let's say we have a collection called `students` with the following documents:
```json
{ "_id": 1, "name": "John", "age": 18 }
{ "_id": 2, "name": "Jane", "age": 20 }
{ "_id": 3, "name": "Mike", "age": 18 }
```

To delete the first document where the age is 18:
```javascript
db.students.deleteOne({ age: 18 })
```

After running the command, the collection will look like this:
```json
{ "_id": 2, "name": "Jane", "age": 20 }
{ "_id": 3, "name": "Mike", "age": 18 }
```

### deleteMany()
The `deleteMany()` method is used to remove all documents from a collection that match a specified filter.

#### Syntax:
```javascript
db.collection.deleteMany(filter, options)
```

- **filter**: A query that matches the documents you want to delete.
- **options**: Optional settings for the operation, such as collation.

#### Example:
Using the same `students` collection:

To delete all documents where the age is 18:
```javascript
db.students.deleteMany({ age: 18 })
```

After running the command, the collection will look like this:
```json
{ "_id": 2, "name": "Jane", "age": 20 }
```

### Summary
- **`deleteOne()`**: Deletes the first document that matches the filter.
- **`deleteMany()`**: Deletes all documents that match the filter.

Feel free to ask if you need more examples or have any other questions!


# Delete all documents from a collection


### Code for `deleteMany`:

```javascript
db.collection.deleteMany({})
```

### Explanation:

1. **`db.collection`**: Refers to the name of your collection. Replace `collection` with your actual collection name (e.g., `users`).
2. **`deleteMany`**: Deletes multiple documents that match the given filter.
3. **`{}`**: An empty filter matches **all documents** in the collection.

This command will remove **all documents** from the specified collection while keeping the collection structure intact.

# **Query Document

A **query document** in MongoDB is a JSON-like object that defines the conditions for selecting documents from a collection. It specifies the criteria used to filter and retrieve matching documents.

Think of it as asking MongoDB:  
_"Find all documents where this condition is true."_

---

### Example:

Suppose you have a collection named `students` with the following documents:

```json
[
  { "name": "Alice", "age": 20, "grade": "A" },
  { "name": "Bob", "age": 22, "grade": "B" },
  { "name": "Charlie", "age": 20, "grade": "C" }
]
```

#### Query Document Example:

To find all students with `age` equal to 20:

```javascript
db.students.find({ "age": 20 })
```

**Explanation of the Query Document:**

1. `{ "age": 20 }` is the **query document**.
2. **Key (`age`)**: Specifies the field you want to filter on.
3. **Value (`20`)**: Specifies the value to match in the `age` field.

---

### More Examples of Query Documents:

1. **Find students with grade "A":**
    
    ```javascript
    db.students.find({ "grade": "A" })
    ```
    
2. **Find students with age greater than 20:**
    
    ```javascript
    db.students.find({ "age": { $gt: 20 } })
    ```
    
3. **Find students with age 20 and grade "A":**
    
    ```javascript
    db.students.find({ "age": 20, "grade": "A" })
    ```
    

---

### Key Points:

- A query document is like a question you ask MongoDB.
- It uses field-value pairs to specify the criteria for matching documents.
- You can use operators like `$gt` (greater than), `$lt` (less than), and `$eq` (equal) for more complex queries.

# **What is `limit()` in MongoDB?

The `limit()` method in MongoDB is used to **restrict the number of documents** returned by a query. It is especially useful when working with large datasets, as it allows you to control the number of results to avoid overloading your application or screen.

---

### Why Use `limit()`?

1. To display only a specific number of results (e.g., the first 5 documents).
2. To improve query performance by fetching fewer documents.
3. To implement pagination (when combined with `skip()`).

---

### Syntax:

```javascript
db.collection.find(query).limit(number)
```

- **`query`**: The filter to match documents (can be empty `{}` to fetch all documents).
- **`number`**: The maximum number of documents to return.

---

### Example:

Suppose you have a collection named `laptops` with 10 documents.

#### Fetching all documents:

```javascript
db.laptops.find()
```

Returns all 10 documents.

#### Fetching only the first 3 documents:

```javascript
db.laptops.find().limit(3)
```

Returns **3 documents** from the collection.

---

### Example with Filtering:

If you want to find laptops with a price less than `80,000` but limit the results to 2 documents:

```javascript
db.laptops.find({ price: { $lt: 80000 } }).limit(2)
```

---

### Key Points:

1. **`limit()` works on the result set**, not on the collection.
2. It only limits the **number of documents displayed**, not the total number of documents in the collection.
3. When used with `sort()` or `skip()`, it helps in implementing **pagination** for large datasets.

---

**In Simple Terms:**  
`limit()` is like saying, "Show me only the first few results, not everything!"


# **What is `skip()` in MongoDB?

The `skip()` method in MongoDB is used to **skip a specific number of documents** in the query results. It’s helpful when you need to retrieve a subset of documents after ignoring some of the initial ones. This is commonly used for **pagination** in combination with the `limit()` method.

---

### Why Use `skip()`?

1. To ignore a specified number of documents in the result.
2. To implement pagination by skipping documents for previous pages.

---

### Syntax:

```javascript
db.collection.find(query).skip(number)
```

- **`query`**: The filter to match documents (can be empty `{}` to fetch all documents).
- **`number`**: The number of documents to skip.

---

### Example:

Suppose you have a collection named `laptops` with 10 documents.

#### Fetching all documents:

```javascript
db.laptops.find()
```

Returns all 10 documents.

#### Skipping the first 3 documents:

```javascript
db.laptops.find().skip(3)
```

Starts from the 4th document and returns the remaining **7 documents**.

---

### Using `skip()` with `limit()` for Pagination:

Pagination typically involves showing a few results at a time, like displaying 3 documents per page.

#### Page 1 (first 3 documents):

```javascript
db.laptops.find().limit(3)
```

#### Page 2 (next 3 documents):

```javascript
db.laptops.find().skip(3).limit(3)
```

#### Page 3 (next 3 documents):

```javascript
db.laptops.find().skip(6).limit(3)
```

---

### Example with Filtering:

If you want to find laptops with a price less than `80,000`, skip the first 2 results, and limit the next 3 results:

```javascript
db.laptops.find({ price: { $lt: 80000 } }).skip(2).limit(3)
```

---

### Key Points:

1. **`skip()` ignores a number of documents** at the beginning of the result set.
2. **When combined with `limit()`**, it helps fetch specific "pages" of results.
3. Skipping too many documents in very large collections can affect performance, as MongoDB still processes those skipped documents internally.

---

**In Simple Terms:**  
`skip()` is like saying, "Ignore the first few results and show me what comes after!" Together with `limit()`, it’s like flipping through pages of search results.


# **Query Operators

Let's create an example collection named `products` with some sample documents. These documents will represent products with fields such as `name`, `category`, `price`, and `quantity`.

### Example Collection: `products`

Here are 5 sample documents in the `products` collection:

```json
[
  {
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 150,
    "quantity": 50
  },
  {
    "name": "Gaming Laptop",
    "category": "Electronics",
    "price": 75000,
    "quantity": 10
  },
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  },
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  },
  {
    "name": "Leather Jacket",
    "category": "Clothing",
    "price": 5000,
    "quantity": 30
  }
]
```

Now let's explain the query operators used above, along with examples from this `products` collection.

---

### 1. **$eq (Equal)**

The `$eq` operator matches documents where the value of a field is **equal** to the specified value.

#### Example:

Find products where the **category** is **"Electronics"**:

```javascript
db.products.find({ "category": { $eq: "Electronics" } })
```

This will return the following documents:

```json
[
  {
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 150,
    "quantity": 50
  },
  {
    "name": "Gaming Laptop",
    "category": "Electronics",
    "price": 75000,
    "quantity": 10
  }
]
```

---

### 2. **$ne (Not Equal)**

The `$ne` operator matches documents where the value of a field is **not equal** to the specified value.

#### Example:

Find products where the **category** is **not** "Clothing":

```javascript
db.products.find({ "category": { $ne: "Clothing" } })
```

This will return the following documents:

```json
[
  {
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 150,
    "quantity": 50
  },
  {
    "name": "Gaming Laptop",
    "category": "Electronics",
    "price": 75000,
    "quantity": 10
  },
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  }
]
```

---

### 3. **$gt (Greater Than)**

The `$gt` operator matches documents where the value of a field is **greater than** the specified value.

#### Example:

Find products where the **price** is **greater than** 1000:

```javascript
db.products.find({ "price": { $gt: 1000 } })
```

This will return the following documents:

```json
[
  {
    "name": "Gaming Laptop",
    "category": "Electronics",
    "price": 75000,
    "quantity": 10
  },
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  },
  {
    "name": "Leather Jacket",
    "category": "Clothing",
    "price": 5000,
    "quantity": 30
  }
]
```

---

### 4. **$lt (Less Than)**

The `$lt` operator matches documents where the value of a field is **less than** the specified value.

#### Example:

Find products where the **price** is **less than** 1000:

```javascript
db.products.find({ "price": { $lt: 1000 } })
```

This will return the following documents:

```json
[
  {
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 150,
    "quantity": 50
  },
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  }
]
```

---

### 5. **$gte (Greater Than or Equal)**

The `$gte` operator matches documents where the value of a field is **greater than or equal** to the specified value.

#### Example:

Find products where the **quantity** is **greater than or equal to** 50:

```javascript
db.products.find({ "quantity": { $gte: 50 } })
```

This will return the following documents:

```json
[
  {
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 150,
    "quantity": 50
  },
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  },
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  }
]
```

---

### 6. **$lte (Less Than or Equal)**

The `$lte` operator matches documents where the value of a field is **less than or equal to** the specified value.

#### Example:

Find products where the **price** is **less than or equal to** 1000:

```javascript
db.products.find({ "price": { $lte: 1000 } })
```

This will return the following documents:

```json
[
  {
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 150,
    "quantity": 50
  },
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  }
]
```

---

### 7. **$in**

The `$in` operator matches documents where the value of a field is **in** a specified list of values.

#### Example:

Find products where the **category** is either "Clothing" or "Shoes":

```javascript
db.products.find({ "category": { $in: ["Clothing", "Shoes"] } })
```

This will return the following documents:

```json
[
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  },
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  },
  {
    "name": "Leather Jacket",
    "category": "Clothing",
    "price": 5000,
    "quantity": 30
  }
]
```

---

### 8. **$nin (Not In)**

The `$nin` operator matches documents where the value of a field is **not in** the specified list of values.

#### Example:

Find products where the **category** is **not** "Electronics" or "Shoes":

```javascript
db.products.find({ "category": { $nin: ["Electronics", "Shoes"] } })
```

This will return the following documents:

```json
[
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  },
  {
    "name": "Leather Jacket",
    "category": "Clothing",
    "price": 5000,
    "quantity": 30
  }
]
```

---

### 9. **$regex (Regular Expression)**

The `$regex` operator matches documents where the value of a field matches the specified **regular expression** pattern.

#### Example:

Find products where the **name** contains the word "T-Shirt":

```javascript
db.products.find({ "name": { $regex: "T-Shirt" } })
```

This will return the following document:

```json
[
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  }
]
```

---

### 10. **$exists**

The `$exists` operator in MongoDB is used in queries to check whether a **field exists or not** in a document. It can be used with `true` or `false` values:

- **`$exists: true`** → Matches documents **where the field exists**
- **`$exists: false`** → Matches documents **where the field does NOT exist**

---

### Syntax:

```json
db.collection.find({ "<field>": { "$exists": <true|false> } })
```

---

### Examples:

#### ✅ Find documents where a field exists

```json
db.users.find({ "email": { "$exists": true } })
```

🔹 This finds all users who **have** an `"email"` field.

#### ✅ Find documents where a field does NOT exist

```json
db.users.find({ "phoneNumber": { "$exists": false } })
```

🔹 This finds all users who **do not** have a `"phoneNumber"` field.

---

### Use Case:

Imagine you're working on a user database where some users have provided their **phone numbers** and some haven't. You can use `$exists` to filter users:

- **Find users who provided phone numbers:**
    
    ```json
    db.users.find({ "phone": { "$exists": true } })
    ```
    
- **Find users who did NOT provide phone numbers:**
    
    ```json
    db.users.find({ "phone": { "$exists": false } })
    ```
    

Would you like an example combining `$exists` with other operators? 🚀

---

### 11. **$and**

The `$and` operator is used to match documents that satisfy **multiple conditions** (all must be true).

#### Example:

Find products where **price** is greater than 2000 and **quantity** is greater than 50:

```javascript
db.products.find({
  $and: [
    { "price": { $gt: 2000 } },
    { "quantity": { $gt: 50 } }
  ]
})
```

This will return the following document:

```json
[
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  }
]

```

---

### 12. **$or**

The `$or` operator is used to match documents that satisfy **at least one condition**.

#### Example:

Find products where the **category** is "Clothing" or the **quantity** is greater than 50:

```javascript
db.products.find({
  $or: [
    { "category": { $eq: "Clothing" } },
    { "quantity": { $gt: 50 } }
  ]
})
```

This will return the following documents:

```json
[
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  },
  {
    "name": "Leather Jacket",
    "category": "Clothing",
    "price": 5000,
    "quantity": 30
  },
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  }
]

```

---

### 13. **$not**

The `$not` operator is used to match documents where the field does **not match** the specified condition.

#### Example:

Find products where the **quantity** is **not** equal to 0:

```javascript
db.products.find({ "quantity": { $not: { $eq: 0 } } })
```

This will return all documents since none of the products have a quantity of 0.

---
### **14. $type

In MongoDB, the `$type` operator is used to query documents based on the BSON data type of a field. It allows you to find documents where a field has a specific data type.

### Syntax:

```json
{ field: { $type: <data type> } }
```

### Example:

If you want to find documents where the field `age` is stored as a string (`"string"` type), you can use:

```json
db.collection.find({ age: { $type: "string" } })
```

### Supported Data Types:

The `$type` operator supports both string aliases and numeric type codes. Some commonly used types are:

|Numeric Code|String Alias|Description|
|---|---|---|
|1|"double"|Floating-point numbers|
|2|"string"|Strings|
|3|"object"|Embedded documents|
|4|"array"|Arrays|
|5|"binData"|Binary data|
|8|"bool"|Boolean (true/false)|
|9|"date"|Date|
|10|"null"|Null values|
|16|"int"|32-bit integer|
|18|"long"|64-bit integer|
|19|"decimal"|Decimal128|

### Querying Multiple Types:

You can also check for multiple types using an array:

```json
db.collection.find({ age: { $type: ["int", "double"] } })
```

This will return documents where `age` is either an integer or a double.

### **15. $mod


The `$mod` operator in MongoDB is used to **find numbers that follow a specific division rule**. It helps check if a number is **divisible** by another number or if it gives a particular remainder when divided.

---

#### **How Does `$mod` Work?**

Think of it like this:

```text
number % divisor == remainder
```

- `%` means **remainder after division**.
- `$mod: [divisor, remainder]` checks if a number gives the expected remainder when divided.

---

#### **Simple Example: Finding Even Numbers**

Imagine we have a **students collection** with marks:

```json
[
  { "name": "Alice", "marks": 20 },
  { "name": "Bob", "marks": 25 },
  { "name": "Charlie", "marks": 30 },
  { "name": "David", "marks": 35 }
]
```

If we want to **find students whose marks are even**, we use `$mod` like this:

```javascript
db.students.find({ "marks": { $mod: [2, 0] } })
```

**Explanation:**

- `2` → We divide the number by **2** (to check even numbers).
- `0` → We only select numbers with a **remainder of 0** (even numbers).

**Output:**

```json
[
  { "name": "Alice", "marks": 20 },
  { "name": "Charlie", "marks": 30 }
]
```

Alice and Charlie are in the result because **20 and 30 are even numbers**.

---

#### **Example: Finding Numbers Divisible by 5**

If we want to find students whose marks are **divisible by 5**, we use:

```javascript
db.students.find({ "marks": { $mod: [5, 0] } })
```

- This will return **Bob (25), Charlie (30), and David (35)** since they are all multiples of 5.

---

#### **Final Thoughts**

- `$mod` is used to check divisibility.
- **Use cases:** Find even/odd numbers, filter based on cycles (like weekly events, rotations, etc.).
- **Formula:** `{ field: { $mod: [divisor, remainder] } }`




# **Logical query operators

MongoDB provides logical query operators that allow you to combine multiple conditions in a single query. These operators include `$and`, `$or`, `$not`, and `$nor`. Let's go through these operators with examples to understand how they work.

### Logical Query Operators in MongoDB

### 1. **$and**

The `$and` operator is used to match documents that satisfy **all** the conditions in the array. Every condition must be true for the document to be included in the result.

#### Example:

We want to find products where:

- The **price** is greater than 2000, and
- The **quantity** is greater than 50.

```javascript
db.products.find({
  $and: [
    { "price": { $gt: 2000 } },
    { "quantity": { $gt: 50 } }
  ]
})
```

### Correct Query Result:

- **Running Shoes** has a price of 3500 and quantity 100, so it meets both conditions.
- **Leather Jacket** has a price of 5000 but a quantity of 30, so it does not meet both conditions.

The returned documents will be:

```json
[
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  }
]
```

---

### 2. **$or**

The `$or` operator matches documents that satisfy **at least one** of the conditions in the array. A document only needs to meet one condition to be included in the result.

#### Example:

We want to find products where:

- The **category** is **"Clothing"**, or
- The **quantity** is greater than 50.

```javascript
db.products.find({
  $or: [
    { "category": { $eq: "Clothing" } },
    { "quantity": { $gt: 50 } }
  ]
})
```

### Query Result:

- **Cotton T-Shirt** and **Leather Jacket** belong to the "Clothing" category, so they meet the first condition.
- **Running Shoes** has a quantity of 100, which is greater than 50, so it meets the second condition.

The returned documents will be:

```json
[
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  },
  {
    "name": "Leather Jacket",
    "category": "Clothing",
    "price": 5000,
    "quantity": 30
  },
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  }
]
```

---

### 3. **$not**

The `$not` operator is used to negate a condition. It matches documents where the specified condition is **not** true.

#### Example:

We want to find products where the **quantity** is **not** 0 (i.e., quantity is greater than 0).

```javascript
db.products.find({ "quantity": { $not: { $eq: 0 } } })
```

### Query Result:

- Since all products in our example have quantities greater than 0, they will all be returned.

The returned documents will be:

```json
[
  {
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 150,
    "quantity": 50
  },
  {
    "name": "Gaming Laptop",
    "category": "Electronics",
    "price": 75000,
    "quantity": 10
  },
  {
    "name": "Running Shoes",
    "category": "Shoes",
    "price": 3500,
    "quantity": 100
  },
  {
    "name": "Cotton T-Shirt",
    "category": "Clothing",
    "price": 500,
    "quantity": 200
  },
  {
    "name": "Leather Jacket",
    "category": "Clothing",
    "price": 5000,
    "quantity": 30
  }
]
```

---

### 4. **$nor**

The `$nor` operator is used to find documents that do **not** satisfy any of the conditions. It is essentially the opposite of `$or`. If a document matches any of the conditions, it is excluded from the result.

#### Example:

We want to find products where:

- The **category** is **not** "Clothing", and
- The **price** is **not** greater than 5000.

```javascript
db.products.find({
  $nor: [
    { "category": { $eq: "Clothing" } },
    { "price": { $gt: 5000 } }
  ]
})
```

### Query Result:

- **Wireless Mouse** and **Gaming Laptop** have a category that is not "Clothing" and price less than or equal to 5000, so they will be included in the result.
- **Running Shoes** and **Leather Jacket** either have the category "Clothing" or a price greater than 5000, so they will be excluded.

The returned documents will be:

```json
[
  {
    "name": "Wireless Mouse",
    "category": "Electronics",
    "price": 150,
    "quantity": 50
  },
  {
    "name": "Gaming Laptop",
    "category": "Electronics",
    "price": 75000,
    "quantity": 10
  }
]
```

---

### Summary of Logical Operators:

- **$and**: Returns documents that satisfy **all** the conditions.
- **$or**: Returns documents that satisfy **at least one** condition.
- **$not**: Negates the given condition and returns documents that don't meet the specified condition.
- **$nor**: Returns documents that do **not** satisfy any of the conditions.

These logical operators help you combine multiple conditions and build more complex queries in MongoDB.

# **Indexing

![[Pasted image 20250121044825.png]] 

![[Pasted image 20250121044907.png]]

![[Pasted image 20250121044927.png]]
![[Pasted image 20250121045256.png]]
![[Pasted image 20250121045327.png]]

![[Pasted image 20250121050209.png]]

![[Pasted image 20250121050249.png]]
![[Pasted image 20250121050317.png]]


## **MongoDB Indexing**

### **1️⃣ What is Indexing?**

Indexing in MongoDB improves the **speed and efficiency** of queries by reducing the amount of data the database needs to scan. Without an index, MongoDB must scan **every document** in a collection to find a match, which can be slow for large datasets.

### **2️⃣ Types of Indexes in MongoDB**

1. **Single Field Index** (`{ field: 1 }` or `{ field: -1 }`)
    - Index on a **single field** in ascending (`1`) or descending (`-1`) order.
    - ✅ **Example:**
        
        ```js
        db.users.createIndex({ name: 1 });
        ```
        
2. **Compound Index** (`{ field1: 1, field2: -1 }`)
    - Index that includes **multiple fields** for optimized queries.
    - ✅ **Example:**
        
        ```js
        db.orders.createIndex({ customerId: 1, orderDate: -1 });
        ```
        
3. **Multikey Index** (For Arrays)
    - Indexes array fields, creating separate entries for each value in the array.
    - ✅ **Example:**
        
        ```js
        db.products.createIndex({ tags: 1 });
        ```
        
4. **Text Index** (`{ field: "text" }`)
    - Supports **full-text search** on string fields.
    - ✅ **Example:**
        
        ```js
        db.articles.createIndex({ content: "text" });
        ```
        
5. **Hashed Index** (`{ field: "hashed" }`)
    - Used for **sharding** to distribute data evenly.
    - ✅ **Example:**
        
        ```js
        db.users.createIndex({ userId: "hashed" });
        ```
        
6. **Wildcard Index** (`{ "$**": 1 }`)
    - Indexes **all fields** dynamically (useful for unknown schemas).
    - ✅ **Example:**
        
        ```js
        db.logs.createIndex({ "$**": 1 });
        ```
        

### **3️⃣ Checking and Dropping Indexes**

- **Check existing indexes:**
    
    ```js
    db.collection.getIndexes();
    ```
    
- **Drop a specific index:**
    
    ```js
    db.collection.dropIndex("index_name");
    ```
    
- **Drop all indexes:**
    
    ```js
    db.collection.dropIndexes();
    ```
    

### **4️⃣ When to Use Indexing?**

✅ **Use indexes when:**

- Querying large datasets frequently
- Sorting and filtering results
- Searching inside arrays or text fields
- Optimizing read-heavy applications

⚠️ **Avoid over-indexing:**

- Indexes take **extra storage**.
- **Too many indexes** slow down writes (inserts, updates, deletes).

### **5️⃣ Performance Check**

- **Use `explain()` to analyze query performance:**
    
    ```js
    db.users.find({ name: "John" }).explain("executionStats");
    ```
    

Indexing is a **key optimization** technique in MongoDB that helps speed up queries.


# **What is Aggregation in MongoDB?**

Aggregation in MongoDB is a process used to analyze, process, and transform large amounts of data efficiently. It allows you to perform operations like filtering, grouping, sorting, and calculations on your data, similar to SQL queries but optimized for NoSQL databases. Aggregation is useful for generating reports, analytics, and data summarization.

---

### **Aggregation Methods in MongoDB**

#### **1. Aggregation Pipeline (Most Common & Efficient)**

The **Aggregation Pipeline** processes data in stages, where each stage applies a specific operation and passes the modified data to the next stage. This makes it an efficient and scalable method.

📌 **Example:** Find the total sales amount for each customer.

```json
db.orders.aggregate([
  { "$match": { "status": "shipped" } },  // Filters orders with status "shipped"
  { "$group": { "_id": "$customerId", "totalSpent": { "$sum": "$amount" } } } // Groups by customerId & sums total spent
])
```

**Common Aggregation Pipeline Stages:**

- `$match` – Filters documents based on conditions (like `WHERE` in SQL).
- `$group` – Groups documents and performs calculations (like `GROUP BY` in SQL).
- `$sort` – Sorts the documents based on a field.
- `$project` – Selects specific fields to display.
- `$limit` – Limits the number of results.
- **`$count`** – Returns the total number of documents
- `$skip` – Skips a specified number of results.
-  **`$unwind`** – Deconstructs arrays into multiple documents
- **`$lookup`** – Performs a left join with another collection
- **`$facet`** – Runs multiple aggregations in a single stage
- **`$bucket`** – Groups data into specified ranges
- **`$addFields`** – Adds new fields to documents
- **`$merge`** – Writes aggregation results to another collection

---

## **`$match` in MongoDB**

`$match` is an **aggregation pipeline stage** in MongoDB that **filters documents** based on specified conditions. It works similarly to the **`find()`** query but is used within the **aggregation pipeline** to filter data before further processing.

---

### **Syntax:**

```json
{ $match: { <query conditions> } }
```

- The conditions follow standard MongoDB query syntax (same as in `find()`).

---

### **Example Usage:**

#### **1. Basic Filtering**

Filter employees with a salary greater than `50000`:

```json
db.employees.aggregate([
  { $match: { salary: { $gt: 50000 } } }
]);
```

**Equivalent to:**

```json
db.employees.find({ salary: { $gt: 50000 } });
```

---

#### **2. Filtering Based on Multiple Conditions**

Find employees who work in the `"IT"` department and have a salary above `60000`:

```json
db.employees.aggregate([
  { 
    $match: { 
      department: "IT", 
      salary: { $gt: 60000 } 
    } 
  }
]);
```

---

#### **3. Using `$match` with Logical Operators**

Find employees who either work in `"HR"` or have a salary greater than `70000`:

```json
db.employees.aggregate([
  { 
    $match: { 
      $or: [ 
        { department: "HR" }, 
        { salary: { $gt: 70000 } } 
      ] 
    } 
  }
]);
```

---

#### **4. Using `$match` in an Aggregation Pipeline**

If we have an aggregation pipeline where we first **filter** employees and then **group** them by department:

```json
db.employees.aggregate([
  { $match: { salary: { $gt: 50000 } } },  // Step 1: Filter employees
  { $group: { _id: "$department", totalEmployees: { $sum: 1 } } }  // Step 2: Group by department
]);
```

Here, `$match` **filters** the documents **before** `$group`, improving performance.

---

### **Key Benefits of `$match`**

✅ Filters data early in the pipeline, making queries more efficient.  
✅ Supports **complex conditions** with logical operators (`$and`, `$or`, `$in`, etc.).  
✅ Works **faster** than filtering later in the pipeline since fewer documents are passed forward.

Would you like more examples or details? 🚀




## **`$group` in MongoDB**

`$group` is an **aggregation pipeline stage** in MongoDB that is used to **group documents** based on a specified field and perform operations like sum, count, average, etc. on each group.

---

### **Syntax:**

```json
{
  $group: {
    _id: <expression>,    // The field to group by
    <newField>: { <accumulator>: <expression> },
    ...
  }
}
```

- **`_id`** → Specifies the field by which documents are grouped.
- **`<newField>`** → The output field name for aggregated results.
- **`<accumulator>`** → Functions that compute values (e.g., `$sum`, `$avg`, `$max`).

---

### **Example Usage:**

#### **1. Group by a Field and Count**

Find the number of employees in each department:

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",      // Grouping by department
      totalEmployees: { $sum: 1 }  // Counting employees in each group
    }
  }
]);
```

**Output:**

```json
[
  { "_id": "IT", "totalEmployees": 10 },
  { "_id": "HR", "totalEmployees": 5 },
  { "_id": "Sales", "totalEmployees": 7 }
]
```

---

#### **2. Calculate Total Salary per Department**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      totalSalary: { $sum: "$salary" }  // Summing up salaries per department
    }
  }
]);
```

---

#### **3. Find Average Salary per Department**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      avgSalary: { $avg: "$salary" }  // Calculating average salary
    }
  }
]);
```

---

#### **4. Get Maximum and Minimum Salary per Department**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      maxSalary: { $max: "$salary" },
      minSalary: { $min: "$salary" }
    }
  }
]);
```

---

#### **5. Group All Documents and Compute Total Employees**

```json
db.employees.aggregate([
  {
    $group: {
      _id: null,  // Groups all documents together
      totalEmployees: { $sum: 1 }
    }
  }
]);
```

**Output:**

```json
[
  { "_id": null, "totalEmployees": 22 }
]
```

---

### **Common Accumulator Operators Used with `$group`**

- **`$sum`** → Adds up values in a group.
- **`$avg`** → Computes the average.
- **`$min`** → Finds the minimum value.
- **`$max`** → Finds the maximum value.
- **`$push`** → Collects values into an array.
- **`$addToSet`** → Collects distinct values into an array.
- **`$first`** → Gets the first document in the group.
- **`$last`** → Gets the last document in the group.

---

### **Key Takeaways**

✅ **Used for grouping documents** based on a field.  
✅ **Performs calculations** like sum, count, average, min, max.  
✅ **Efficient** for data analysis and reporting.

## **`$sort` in MongoDB**

`$sort` is an **aggregation pipeline stage** in MongoDB that sorts documents **in ascending or descending order** based on one or more fields. It works similarly to the `sort()` method in `find()` queries but is used within an **aggregation pipeline**.

---

### **Syntax:**

```json
{ $sort: { <field1>: <order>, <field2>: <order>, ... } }
```

- **`<field>`** → The field to sort by.
- **`<order>`** → Sorting order:
    - `1` → **Ascending order (smallest to largest)**
    - `-1` → **Descending order (largest to smallest)**

---

### **Example Usage:**

#### **1. Sorting Employees by Salary (Ascending)**

```json
db.employees.aggregate([
  { $sort: { salary: 1 } }  // Sorts salaries from lowest to highest
]);
```

#### **2. Sorting Employees by Salary (Descending)**

```json
db.employees.aggregate([
  { $sort: { salary: -1 } }  // Sorts salaries from highest to lowest
]);
```

#### **3. Sorting by Multiple Fields**

Sort employees by **department (A-Z)** and then **salary (highest to lowest)**:

```json
db.employees.aggregate([
  { $sort: { department: 1, salary: -1 } }
]);
```

- First, it sorts **departments alphabetically (`1`)**.
- Then, within each department, it sorts **salaries from highest to lowest (`-1`)**.

---

### **4. Using `$sort` After Grouping**

Sort departments by **total salary (highest first)**:

```json
db.employees.aggregate([
  { $group: { _id: "$department", totalSalary: { $sum: "$salary" } } },
  { $sort: { totalSalary: -1 } }
]);
```

- **First, `$group` calculates total salary per department.**
- **Then, `$sort` orders them from highest to lowest.**

---

### **Key Takeaways**

✅ **Sorts documents efficiently** within an aggregation pipeline.  
✅ **Can be used with multiple fields** for complex sorting logic.  
✅ **Improves performance** when sorting is done early in the pipeline.


## **`$project` in MongoDB**

`$project` is an **aggregation pipeline stage** in MongoDB that **modifies the structure of documents** by including, excluding, or computing new fields. It is similar to selecting specific fields in a `find()` query but is used in **aggregation pipelines**.

---

### **Syntax:**

```json
{ 
  $project: { 
    <field1>: <include/exclude>, 
    <field2>: <include/exclude>, 
    <newField>: <expression> 
  } 
}
```

- **`1`** → Includes the field.
- **`0`** → Excludes the field.
- **`<expression>`** → Can transform or compute new values.

---

### **Example Usage:**

#### **1. Selecting Specific Fields**

Return only `name` and `salary`, excluding `_id`:

```json
db.employees.aggregate([
  { 
    $project: { 
      _id: 0, 
      name: 1, 
      salary: 1 
    } 
  }
]);
```

**Output:**

```json
[
  { "name": "Alice", "salary": 50000 },
  { "name": "Bob", "salary": 60000 }
]
```

---

#### **2. Adding a New Computed Field**

Calculate annual salary (`salary * 12`):

```json
db.employees.aggregate([
  { 
    $project: { 
      name: 1, 
      salary: 1, 
      annualSalary: { $multiply: ["$salary", 12] } 
    } 
  }
]);
```

**Output:**

```json
[
  { "name": "Alice", "salary": 50000, "annualSalary": 600000 },
  { "name": "Bob", "salary": 60000, "annualSalary": 720000 }
]
```

---

#### **3. Renaming a Field**

Rename `salary` to `monthlySalary`:

```json
db.employees.aggregate([
  { 
    $project: { 
      name: 1, 
      monthlySalary: "$salary" 
    } 
  }
]);
```

**Output:**

```json
[
  { "name": "Alice", "monthlySalary": 50000 },
  { "name": "Bob", "monthlySalary": 60000 }
]
```

---

#### **4. Excluding a Field**

Exclude `salary` but keep other fields:

```json
db.employees.aggregate([
  { 
    $project: { 
      salary: 0 
    } 
  }
]);
```

---

### **5. Combining `$project` with `$match`**

Filter employees with a salary greater than `50000` and show only `name`:

```json
db.employees.aggregate([
  { $match: { salary: { $gt: 50000 } } },
  { $project: { _id: 0, name: 1 } }
]);
```

---

### **Key Takeaways**

✅ **Used to include/exclude fields** in the output.  
✅ **Can compute new fields** based on existing data.  
✅ **Improves performance** by reducing unnecessary data transfer.

## **`$limit` and `$skip` 

### **1️⃣ `$limit` – Restrict the Number of Documents**

- **`$limit`** is used to **restrict** the number of documents returned in the aggregation result.
- It helps in **pagination** and **performance optimization** by reducing the number of processed documents.

### **🛠 Syntax:**

```javascript
db.collection.aggregate([
  { $limit: 5 }
])
```

✅ Returns only **5 documents** from the collection.

---

### **2️⃣ `$skip` – Skip a Certain Number of Documents**

- **`$skip`** is used to **bypass** a specific number of documents in the pipeline.
- It is often used for **pagination** when combined with `$limit`.

### **🛠 Syntax:**

```javascript
db.collection.aggregate([
  { $skip: 10 }
])
```

✅ Skips the **first 10 documents** and returns the rest.

---

### **📚 Real-World Use Case: Pagination**

Imagine you have an **e-commerce website** displaying products. You want to implement **pagination** where each page shows **10 products**.

### **🔍 Query: Fetch Page 3 (Products 21-30)**

```javascript
db.products.aggregate([
  { $skip: 20 },  // Skip first 20 products (Page 1 & 2)
  { $limit: 10 }  // Show only 10 products (Page 3)
])
```

✅ This will **skip** the first **20** documents and **return the next 10**, effectively displaying **Page 3**.

---

### **🛍️ Use Case Scenarios**

|**Use Case**|**How `$limit` & `$skip` Help?**|
|---|---|
|📜 **News Website**|Show only the **latest 10 articles**|
|🎬 **Movie Database**|**Paginate** through movie lists|
|🏬 **E-commerce**|Load **10 products per page**|
|🎓 **Student Records**|Display **top 5 highest-scoring students**|

---

### **🎯 Summary**

|**Operator**|**Function**|
|---|---|
|`$limit`|Restricts the number of results|
|`$skip`|Skips a certain number of documents|
|**Combined Use**|Used for **pagination & performance**|

Using **`$skip` and `$limit` together** makes pagination easy and efficient! 🚀 Let me know if you need more examples. 🔥
## **`$count` in MongoDB**

`$count` is an **aggregation pipeline stage** that **counts the number of documents** in a pipeline and returns the result as a single document.

---

### **Syntax:**

```json
{ $count: "<field_name>" }
```

- `"<field_name>"` → The name of the field that will store the count result.

---

### **Example 1: Count All Documents in a Collection**

```json
db.employees.aggregate([
  { $count: "totalEmployees" }
]);
```

**Output:**

```json
[
  { "totalEmployees": 50 }  // The collection has 50 documents
]
```

---

### **Example 2: Count Employees with Salary Greater Than 50,000**

```json
db.employees.aggregate([
  { $match: { salary: { $gt: 50000 } } },
  { $count: "highSalaryEmployees" }
]);
```

**Output:**

```json
[
  { "highSalaryEmployees": 20 }
]
```

✅ First, `$match` filters employees with `salary > 50000`.  
✅ Then, `$count` returns the total **number of matching documents**.

---

### **Alternative Using `$group`**

You can also count documents using `$group`:

```json
db.employees.aggregate([
  {
    $group: {
      _id: null,
      totalEmployees: { $sum: 1 }
    }
  }
]);
```

**Output:**

```json
[
  { "totalEmployees": 50 }
]
```

⚡ `$count` is simpler and **more efficient** when you just need the total count.

---

### **Key Takeaways:**

✅ **Counts documents** in an aggregation pipeline.  
✅ **Used after `$match`** to count filtered results.  
✅ **More efficient** than `$group` for counting.

## **`$unwind` in MongoDB**

`$unwind` is an **aggregation pipeline stage** that **splits an array field into multiple documents**. Each element of the array **becomes a separate document**, making it easier to work with embedded arrays.

---

### **Syntax:**

```json
{ $unwind: "<arrayField>" }
```

- **`"<arrayField>"`** → The array field that needs to be expanded.

---

### **Example 1: Expanding an Array Field**

#### **Sample Collection (`employees`)**

```json
[
  { "_id": 1, "name": "Alice", "skills": ["MongoDB", "Node.js", "React"] },
  { "_id": 2, "name": "Bob", "skills": ["Python", "Django"] }
]
```

#### **Aggregation Query:**

```json
db.employees.aggregate([
  { $unwind: "$skills" }
]);
```

#### **Output:**

```json
[
  { "_id": 1, "name": "Alice", "skills": "MongoDB" },
  { "_id": 1, "name": "Alice", "skills": "Node.js" },
  { "_id": 1, "name": "Alice", "skills": "React" },
  { "_id": 2, "name": "Bob", "skills": "Python" },
  { "_id": 2, "name": "Bob", "skills": "Django" }
]
```

✅ The array `skills` is **flattened**, creating **separate documents** for each skill.

---

### **Example 2: Using `$unwind` with `$group`**

Count the number of times each skill appears:

```json
db.employees.aggregate([
  { $unwind: "$skills" },
  { $group: { _id: "$skills", count: { $sum: 1 } } }
]);
```

**Output:**

```json
[
  { "_id": "MongoDB", "count": 1 },
  { "_id": "Node.js", "count": 1 },
  { "_id": "React", "count": 1 },
  { "_id": "Python", "count": 1 },
  { "_id": "Django", "count": 1 }
]
```

✅ **Splits the array and counts each unique skill.**

---

### **Example 3: Using `$unwind` with Missing or Empty Fields**

When you use `$unwind` on an **array field**, it **breaks the array into multiple documents**.  
But what happens if the array **is missing or empty**?

- **By default**: MongoDB **removes** documents that **do not have the array field**.
- **To keep those documents**, use `{ preserveNullAndEmptyArrays: true }`.

---

### **Example Scenario**

#### **Original Data (`employees` Collection):**

```json
[
  { "_id": 1, "name": "Alice", "skills": ["MongoDB", "Node.js"] },
  { "_id": 2, "name": "Bob", "skills": [] },   // Empty array
  { "_id": 3, "name": "Charlie" }              // No "skills" field
]
```

#### **Query Without `preserveNullAndEmptyArrays`**

```json
db.employees.aggregate([
  { $unwind: "$skills" }
]);
```

💡 **What happens?**

- The **"skills" field is unwound**, creating **separate documents for each skill**.
- **Bob and Charlie disappear** because Bob has an empty array, and Charlie **does not have the "skills" field**.

**Output:**

```json
[
  { "_id": 1, "name": "Alice", "skills": "MongoDB" },
  { "_id": 1, "name": "Alice", "skills": "Node.js" }
]
```

❌ Bob and Charlie are **missing** in the result.

---

#### **Query With `preserveNullAndEmptyArrays: true`**

```json
db.employees.aggregate([
  { $unwind: { path: "$skills", preserveNullAndEmptyArrays: true } }
]);
```

💡 **What happens now?**

- If `skills` is missing or an empty array, **MongoDB keeps the document** but sets `"skills": null`.

**Output:**

```json
[
  { "_id": 1, "name": "Alice", "skills": "MongoDB" },
  { "_id": 1, "name": "Alice", "skills": "Node.js" },
  { "_id": 2, "name": "Bob", "skills": null },    // Empty array → Null
  { "_id": 3, "name": "Charlie", "skills": null } // No skills → Null
]
```

✅ Now **Bob and Charlie are included** in the results, with `skills: null`.

---


### **Key Takeaways:**

✅ **Expands array fields** into multiple documents.  
✅ **Helps with grouping, filtering, and counting array elements.**  
✅ **Use `preserveNullAndEmptyArrays: true`** to keep documents without the field.


## **`$addFields` in MongoDB**

`$addFields` is an **aggregation pipeline stage** that **adds new fields** to documents or **modifies existing fields**. It allows you to create new fields based on expressions or values derived from other fields.

---

### **Syntax:**

```json
{ $addFields: { <newField>: <expression> } }
```

- `<newField>` → The name of the new field to be added.
- `<expression>` → A value, field reference, or operation to compute the new field's value.

---

### **Example 1: Adding a New Field**

#### Add a field `fullName` by combining `firstName` and `lastName`.

```json
db.employees.aggregate([
  {
    $addFields: {
      fullName: { $concat: ["$firstName", " ", "$lastName"] }
    }
  }
]);
```

**Output:**

```json
[
  { "_id": 1, "firstName": "Alice", "lastName": "Smith", "fullName": "Alice Smith" },
  { "_id": 2, "firstName": "Bob", "lastName": "Johnson", "fullName": "Bob Johnson" }
]
```

✅ A new field `fullName` is added by combining `firstName` and `lastName`.

---

### **Example 2: Modifying an Existing Field**

#### Increase the `salary` by 10%.

```json
db.employees.aggregate([
  {
    $addFields: {
      salary: { $multiply: ["$salary", 1.1] }
    }
  }
]);
```

**Output:**

```json
[
  { "_id": 1, "name": "Alice", "salary": 55000 },
  { "_id": 2, "name": "Bob", "salary": 66000 }
]
```

✅ The `salary` field is **increased by 10%**.

---

### **Example 3: Using `$addFields` with Complex Expressions**

#### Add a new field `netSalary` by calculating `salary - taxAmount`.

```json
db.employees.aggregate([
  {
    $addFields: {
      netSalary: { $subtract: ["$salary", "$taxAmount"] }
    }
  }
]);
```

**Output:**

```json
[
  { "_id": 1, "name": "Alice", "salary": 50000, "taxAmount": 5000, "netSalary": 45000 },
  { "_id": 2, "name": "Bob", "salary": 60000, "taxAmount": 6000, "netSalary": 54000 }
]
```

✅ A new field `netSalary` is calculated by subtracting `taxAmount` from `salary`.

---

### **Example 4: Adding an Array Field**

#### Add a field `address` as an array of city and country.

```json
db.employees.aggregate([
  {
    $addFields: {
      address: ["$city", "$country"]
    }
  }
]);
```

**Output:**

```json
[
  { "_id": 1, "name": "Alice", "city": "New York", "country": "USA", "address": ["New York", "USA"] },
  { "_id": 2, "name": "Bob", "city": "London", "country": "UK", "address": ["London", "UK"] }
]
```

✅ The `address` field is created as an array combining `city` and `country`.

---

### **Key Takeaways:**

✅ **`$addFields`** adds new fields or **modifies existing fields**.  
✅ Supports **complex expressions** to calculate new field values.  
✅ Can **combine or transform data** from existing fields into new fields.

## **`$facet` in MongoDB Aggregation?**

The **`$facet`** stage in MongoDB's aggregation pipeline allows you to **run multiple queries (sub-pipelines) in parallel** and return their results **in a single document**.

---

### **Why Use `$facet`?**

- Instead of running multiple queries separately, **`$facet`** allows you to do it in **one aggregation pipeline**.
- Useful when you need **different types of results** from the same dataset (e.g., top 5 restaurants, average scores, total count).
- Each sub-pipeline in **`$facet`** runs **independently** but on the **same input data**.

---

### **Example 1: Using `$facet` to Get Multiple Results in One Query**

Let's say we have a **restaurants** collection:

```json
{
  "name": "The Country Cafe",
  "borough": "Manhattan",
  "cuisine": "Turkish",
  "grades": [
    { "grade": "A", "score": 9 },
    { "grade": "A", "score": 13 },
    { "grade": "B", "score": 15 },
    { "grade": "A", "score": 11 }
  ]
}
```

Now, we want to:

1. Find the **top 5 restaurants with the most "A" grades**.
2. Find the **average score of all restaurants**.
3. Get the **total number of restaurants**.

Instead of running **three separate queries**, we can use **`$facet`**:

```javascript
db.restaurants.aggregate([
  {
    $facet: {
      top5Restaurants: [
        { $unwind: "$grades" },
        { $match: { "grades.grade": "A" } },
        { $group: { _id: "$name", countA: { $sum: 1 } } },
        { $sort: { countA: -1 } },
        { $limit: 5 }
      ],
      averageScore: [
        { $unwind: "$grades" },
        { $group: { _id: null, avgScore: { $avg: "$grades.score" } } },
        { $project: { _id: 0, avgScore: 1 } }
      ],
      totalRestaurants: [
        { $group: { _id: null, count: { $sum: 1 } } },
        { $project: { _id: 0, count: 1 } }
      ]
    }
  }
]);
```

---

### **Breaking Down the `$facet` Query**

|**Sub-Pipeline**|**What It Does**|
|---|---|
|`top5Restaurants`|Finds **top 5 restaurants** with most "A" grades.|
|`averageScore`|Calculates **average score** of all restaurants.|
|`totalRestaurants`|Counts **total number of restaurants**.|

---

### **Expected Output**

```json
[
  {
    "top5Restaurants": [
      { "_id": "Morris Park Bake Shop", "countA": 10 },
      { "_id": "The Country Cafe", "countA": 7 },
      { "_id": "Pasta Paradise", "countA": 6 },
      { "_id": "Kebab House", "countA": 5 },
      { "_id": "Spicy Corner", "countA": 5 }
    ],
    "averageScore": [
      { "avgScore": 8.7 }
    ],
    "totalRestaurants": [
      { "count": 1200 }
    ]
  }
]
```

---

### **Example 2: Using `$facet` for Pagination**

Let's say you have a **restaurants listing page**, and you want:

- **First 10 restaurants for Page 1**.
- **Total number of restaurants** (for pagination).

Instead of making **two queries**, we can use **`$facet`**:

```javascript
db.restaurants.aggregate([
  {
    $facet: {
      paginatedResults: [
        { $sort: { name: 1 } }, // Sort by name
        { $skip: 0 },           // Skip 0 for page 1 (change for other pages)
        { $limit: 10 }          // Get 10 results per page
      ],
      totalCount: [
        { $group: { _id: null, count: { $sum: 1 } } },
        { $project: { _id: 0, count: 1 } }
      ]
    }
  }
]);
```

### **Expected Output**

```json
[
  {
    "paginatedResults": [
      { "name": "ABC Cafe", "borough": "Manhattan", "cuisine": "Italian" },
      { "name": "Best Pizza", "borough": "Brooklyn", "cuisine": "Pizza" },
      { "name": "Burger House", "borough": "Queens", "cuisine": "Burgers" }
    ],
    "totalCount": [
      { "count": 5000 }
    ]
  }
]
```

Now, the frontend can **display the first 10 restaurants** and **show total restaurants for pagination**.

---

### **Key Points About `$facet`**

✔ Runs **multiple queries in parallel** on the **same dataset**.  
✔ Each sub-pipeline works **independently**.  
✔ Returns results in **one document**, making it easy to use in applications.  
✔ Best for **pagination, analytics, dashboards**, and multi-result queries.

## **`$lookup` Explained for Beginners**

MongoDB’s **`$lookup`** is used to **join two collections** based on a **common field**, just like **SQL JOIN**. It allows you to fetch **related documents from another collection** and merge them into your result.

---

### **🛠 Basic Syntax of `$lookup`**

```javascript
db.collection.aggregate([
  {
    $lookup: {
      from: "other_collection",  // The collection you want to join
      localField: "field_in_current_collection",  // Field in current collection
      foreignField: "field_in_other_collection",  // Matching field in other collection
      as: "new_field_name"  // The name for the joined data (stored as an array)
    }
  }
]);
```

✔️ The **`localField`** in the **current collection** is matched with the **`foreignField`** in the **other collection**.  
✔️ The results from **`other_collection`** will be stored in an **array** under `new_field_name`.

---

### **🛍️ Real-World Example: Orders & Customers**

👉 Imagine an **E-commerce platform** where:

- `customers` collection stores customer details.
- `orders` collection stores order details, with a **reference to a customer ID**.

### **🔹 `customers` Collection**

```json
{ "_id": 1, "name": "Rahul Sharma", "email": "rahul@example.com" }
{ "_id": 2, "name": "Priya Singh", "email": "priya@example.com" }
```

### **🔹 `orders` Collection**

```json
{ "_id": 101, "customer_id": 1, "product": "iPhone 15", "amount": 80000 }
{ "_id": 102, "customer_id": 2, "product": "MacBook Pro", "amount": 200000 }
```

### **🔍 Query: Fetch Orders with Customer Details**

```javascript
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",  // Collection to join
      localField: "customer_id",  // Field in `orders`
      foreignField: "_id",  // Matching field in `customers`
      as: "customerDetails"  // New field to store joined data
    }
  }
]);
```

### **✅ Output: Orders with Customer Information**

```json
{
  "_id": 101,
  "customer_id": 1,
  "product": "iPhone 15",
  "amount": 80000,
  "customerDetails": [
    {
      "_id": 1,
      "name": "Rahul Sharma",
      "email": "rahul@example.com"
    }
  ]
}
```

✔️ Each order now includes **customer details** without needing multiple queries!

---

### **🚀 More Real-World Use Cases**

|**Industry**|**Use Case**|
|---|---|
|🏬 **E-Commerce**|Fetching **orders with customer details**|
|🎓 **Education**|Linking **students with their enrolled courses**|
|🏥 **Healthcare**|Fetching **patients with their medical records**|
|🏢 **HR Systems**|Connecting **employees with their department details**|
|🎬 **Movie Database**|Fetching **movies with cast & director details**|

---


---

### **🎯 Summary: Why Use `$lookup`?**

✅ **Works like SQL JOIN** → Merges related data from two collections  
✅ **Avoids multiple queries** → Fetches all related data in **one query**  
✅ **Flexible & powerful** → Supports **nested documents & filtering**  
✅ **Best for referenced data** → Ideal for **users, orders, products, courses, etc.**

---

### **🚀 Final Thoughts**

MongoDB’s **`$lookup`** is a game-changer for projects that need **relational-style queries** while keeping MongoDB’s **flexibility & performance**. Whether you’re building an **e-commerce store, job portal, or movie database**, `$lookup` simplifies queries and improves efficiency.




##  **`$bucket` in MongoDB 

The `$bucket` stage in MongoDB’s **aggregation pipeline** is used to group documents into **fixed-size ranges**, similar to how you might sort objects into different bins.

---

### **📌 What Does `$bucket` Do?**

- It **categorizes documents** based on a numeric field.
- It **divides data into defined ranges (buckets)**.
- It **counts** how many documents fall into each bucket (or computes additional statistics).

💡 **Think of it like sorting students into grade categories based on their scores!** 🎓

---

### **🛠 Basic Syntax of `$bucket`**

```js
db.collection.aggregate([
  {
    $bucket: {
      groupBy: "$field",      // Field to group by (must be a number)
      boundaries: [0, 50, 75, 100],  // Defines bucket ranges
      default: "Unknown",     // Optional: Where to put values outside the ranges
      output: { count: { $sum: 1 } }  // Count documents in each bucket
    }
  }
]);
```

- **`groupBy`** → The field you are grouping by (must be numeric).
- **`boundaries`** → Defines the bucket ranges.
- **`default`** → Where to place values that don’t fit in the given boundaries.
- **`output`** → Specifies what to calculate for each bucket (e.g., count, average, sum).

---

### **🎓 Example: Categorizing Student Scores**

Imagine we have a collection of **students** with their exam scores:

### **📌 Sample Data**

```js
db.students.insertMany([
  { name: "Alice", score: 45 },
  { name: "Bob", score: 60 },
  { name: "Charlie", score: 80 },
  { name: "David", score: 95 },
  { name: "Eve", score: 30 },
  { name: "Frank", score: 100 }
]);
```

### **🛠 Query Using `$bucket`**

```js
db.students.aggregate([
  {
    $bucket: {
      groupBy: "$score",  
      boundaries: [0, 50, 75, 100],  
      default: "Unknown",  
      output: { count: { $sum: 1 } }
    }
  }
]);
```

### **📌 Expected Output**

```js
[
  { "_id": 0, "count": 2 },     // 2 students scored between 0-49
  { "_id": 50, "count": 1 },    // 1 student scored between 50-74
  { "_id": 75, "count": 2 },    // 2 students scored between 75-99
  { "_id": "Unknown", "count": 1 }  // 1 student (100) falls outside the defined range
]
```

### **💡 Explanation**

- **Alice (45) and Eve (30)** → Placed in **0-49 bucket** (count = 2).
- **Bob (60)** → Placed in **50-74 bucket** (count = 1).
- **Charlie (80) and David (95)** → Placed in **75-99 bucket** (count = 2).
- **Frank (100)** → Does not fit into the defined boundaries, so it goes into **"Unknown"**.

---

### **🛍 Real-World Example: Categorizing Product Prices**

Imagine an **e-commerce store** where products have different prices. You want to group them into price categories:

### **📌 Sample Data**

```js
db.products.insertMany([
  { name: "Phone", price: 250 },
  { name: "Laptop", price: 1200 },
  { name: "Headphones", price: 80 },
  { name: "Smartwatch", price: 200 },
  { name: "TV", price: 700 },
  { name: "Monitor", price: 300 }
]);
```

### **🛠 Query Using `$bucket`**

```js
db.products.aggregate([
  {
    $bucket: {
      groupBy: "$price",  
      boundaries: [0, 100, 500, 1000, 2000],  
      default: "Expensive",  
      output: { count: { $sum: 1 } }
    }
  }
]);
```

### **📌 Expected Output**

```js
[
  { "_id": 0, "count": 1 },       // 1 product priced between $0-$99
  { "_id": 100, "count": 2 },     // 2 products priced between $100-$499
  { "_id": 500, "count": 1 },     // 1 product priced between $500-$999
  { "_id": 1000, "count": 1 },    // 1 product priced between $1000-$1999
  { "_id": "Expensive", "count": 1 }  // 1 product is above $2000
]
```

### **💡 Explanation**

- **Headphones ($80)** → Goes into **0-99** bucket.
- **Phone ($250) and Smartwatch ($200)** → Go into **100-499** bucket.
- **TV ($700)** → Goes into **500-999** bucket.
- **Laptop ($1200)** → Goes into **1000-1999** bucket.
- **Monitor ($300)** → Also in **100-499** bucket.

---

### **🆚 Difference Between `$bucket` and `$bucketAuto`**

- `$bucket` → You **manually define** the ranges (`boundaries`).
- `$bucketAuto` → MongoDB **automatically calculates** even-sized ranges based on the data.

---

### **✅ When to Use `$bucket`?**

- When you **need to group numeric values into predefined ranges**.
- When **analyzing data distributions** (e.g., salary ranges, age groups, product pricing).
- When performing **categorization** based on numeric fields.

---

### **🔹 Final Summary**

- `$bucket` is used in **aggregation** to **group numbers into fixed ranges**.
- It’s like **sorting items into bins** (e.g., student grades, product prices).
- You **define the boundaries** manually.
- **Great for summarizing and analyzing numeric data!**

Let me know if you need more examples! 🚀
# **Accumulator operator

An **accumulator** in MongoDB refers to a special operator used in aggregation pipelines to perform calculations or accumulate values over a set of documents. Accumulators are used within stages like `$group` to summarize or aggregate data.

In simple terms, an accumulator collects and processes values across multiple documents to return a single result or a group of results. For example, it can sum numbers, find averages, count items, or even collect values into an array.

### Common Accumulator Operators in MongoDB:

1. **`$sum`**: Adds up all the values.
    
    - Example: Calculate the total sales in a group of documents.
2. **`$avg`**: Computes the average of the values.
    
    - Example: Find the average age in a group.
3. **`$max`**: Returns the maximum value.
    
    - Example: Find the highest salary.
4. **`$min`**: Returns the minimum value.
    
    - Example: Find the lowest salary.
5. **`$first`**: Returns the first value in a group.
    
    - Example: Retrieve the first entry based on a sorted field.
6. **`$last`**: Returns the last value in a group.
    
    - Example: Get the last item added to a collection.
7. **`$push`**: Collects values into an array.
    
    - Example: Create an array of all the names in a group.
8. **`$addToSet`**: Collects values into an array but removes duplicates.
    
    - Example: Collect distinct items into an array.
9. **`$stdDevPop`** and **`$stdDevSamp`**: Calculates the population or sample standard deviation.
    
## **`$sum` in MongoDB Aggregation**

`$sum` is an **aggregation operator** used to **calculate the sum of numeric values** in a dataset. It is commonly used in the **`$group`** stage to add up values from multiple documents.

---

### **1. Using `$sum` in `$group`**

You can use `$sum` to add values across multiple documents **grouped by a specific field**.

### **Example: Total Salary by Department**

#### **Sample Data (`employees` Collection)**

```json
[
  { "_id": 1, "name": "Alice", "department": "IT", "salary": 50000 },
  { "_id": 2, "name": "Bob", "department": "HR", "salary": 40000 },
  { "_id": 3, "name": "Charlie", "department": "IT", "salary": 60000 },
  { "_id": 4, "name": "David", "department": "HR", "salary": 45000 }
]
```

#### **Aggregation Query**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department", 
      totalSalary: { $sum: "$salary" }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "totalSalary": 110000 },
  { "_id": "HR", "totalSalary": 85000 }
]
```

✅ The total salary is grouped by `department` and summed up.

---

### **2. Counting Documents with `$sum: 1`**

You can use `$sum: 1` to count the number of documents in each group.

### **Example: Count Employees in Each Department**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      employeeCount: { $sum: 1 }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "employeeCount": 2 },
  { "_id": "HR", "employeeCount": 2 }
]
```

✅ `$sum: 1` counts the number of employees in each department.

---

### **3. Using `$sum` in `$project`**

You can also use `$sum` inside the **`$project`** stage to sum up an **array of numbers** inside a document.

### **Example: Calculate Total Marks of a Student**

#### **Sample Data (`students` Collection)**

```json
[
  { "_id": 1, "name": "Alice", "marks": [85, 90, 80] },
  { "_id": 2, "name": "Bob", "marks": [70, 75, 80] }
]
```

#### **Aggregation Query**

```json
db.students.aggregate([
  {
    $project: {
      name: 1,
      totalMarks: { $sum: "$marks" }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": 1, "name": "Alice", "totalMarks": 255 },
  { "_id": 2, "name": "Bob", "totalMarks": 225 }
]
```

✅ The `marks` array is summed up for each student.

---

### **Key Takeaways**

✅ **`$sum`** adds up numeric values in documents.  
✅ Used in **`$group`** to sum values across multiple documents.  
✅ Used in **`$project`** to sum values inside an array.  
✅ **`$sum: 1`** can be used for **counting documents** in a group.

## **`$avg` in MongoDB Aggregation**

`$avg` is an **aggregation operator** that calculates the **average (mean)** of numeric values in a dataset. It is commonly used in the **`$group`** stage to compute the average of a field across multiple documents.

---

### **1. Using `$avg` in `$group`**

You can use `$avg` to find the **average value** of a field when grouping documents.

### **Example: Average Salary by Department**

#### **Sample Data (`employees` Collection)**

```json
[
  { "_id": 1, "name": "Alice", "department": "IT", "salary": 50000 },
  { "_id": 2, "name": "Bob", "department": "HR", "salary": 40000 },
  { "_id": 3, "name": "Charlie", "department": "IT", "salary": 60000 },
  { "_id": 4, "name": "David", "department": "HR", "salary": 45000 }
]
```

#### **Aggregation Query**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department", 
      avgSalary: { $avg: "$salary" }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "avgSalary": 55000 },
  { "_id": "HR", "avgSalary": 42500 }
]
```

✅ The **average salary** is calculated for each `department`.

---

### **2. Using `$avg` in `$project`**

You can also use `$avg` inside **`$project`** to calculate the **average of an array** in a document.

### **Example: Calculate Average Marks of Students**

#### **Sample Data (`students` Collection)**

```json
[
  { "_id": 1, "name": "Alice", "marks": [85, 90, 80] },
  { "_id": 2, "name": "Bob", "marks": [70, 75, 80] }
]
```

#### **Aggregation Query**

```json
db.students.aggregate([
  {
    $project: {
      name: 1,
      avgMarks: { $avg: "$marks" }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": 1, "name": "Alice", "avgMarks": 85 },
  { "_id": 2, "name": "Bob", "avgMarks": 75 }
]
```

✅ The **average of the `marks` array** is calculated for each student.

---

### **Key Takeaways**

✅ **`$avg`** calculates the **mean value** of numeric fields.  
✅ Used in **`$group`** to find the **average across multiple documents**.  
✅ Used in **`$project`** to compute the **average of an array** in a single document.


## **`$max` and `$min` in MongoDB Aggregation**

`$max` and `$min` are **aggregation operators** used to find the **highest** (`$max`) and **lowest** (`$min`) values of a numeric field in a dataset. They are commonly used in the **`$group`** stage to determine extreme values.

---

### **1. Using `$max` in `$group`**

Finds the **maximum** value of a field in a group.

### **Example: Find Highest Salary in Each Department**

#### **Sample Data (`employees` Collection)**

```json
[
  { "_id": 1, "name": "Alice", "department": "IT", "salary": 50000 },
  { "_id": 2, "name": "Bob", "department": "HR", "salary": 40000 },
  { "_id": 3, "name": "Charlie", "department": "IT", "salary": 60000 },
  { "_id": 4, "name": "David", "department": "HR", "salary": 45000 }
]
```

#### **Aggregation Query**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department", 
      highestSalary: { $max: "$salary" }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "highestSalary": 60000 },
  { "_id": "HR", "highestSalary": 45000 }
]
```

✅ The **maximum salary** is found for each department.

---

### **2. Using `$min` in `$group`**

Finds the **minimum** value of a field in a group.

### **Example: Find Lowest Salary in Each Department**

#### **Aggregation Query**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      lowestSalary: { $min: "$salary" }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "lowestSalary": 50000 },
  { "_id": "HR", "lowestSalary": 40000 }
]
```

✅ The **minimum salary** is found for each department.

---

###
**3. Using `$max` and `$min` in `$project`**

You can also use `$max` and `$min` inside **`$project`** to find the **highest and lowest values in an array** inside a document.

### **Example: Find Highest and Lowest Marks of Students**

#### **Sample Data (`students` Collection)**

```json
[
  { "_id": 1, "name": "Alice", "marks": [85, 90, 80] },
  { "_id": 2, "name": "Bob", "marks": [70, 75, 80] }
]
```

#### **Aggregation Query**

```json
db.students.aggregate([
  {
    $project: {
      name: 1,
      highestMark: { $max: "$marks" },
      lowestMark: { $min: "$marks" }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": 1, "name": "Alice", "highestMark": 90, "lowestMark": 80 },
  { "_id": 2, "name": "Bob", "highestMark": 80, "lowestMark": 70 }
]
```

✅ The **highest and lowest marks** are found for each student.

---

### **Key Takeaways**

✅ **`$max`** finds the **highest value** of a field.  
✅ **`$min`** finds the **lowest value** of a field.  
✅ Used in **`$group`** to find **max/min values across multiple documents**.  
✅ Used in **`$project`** to find **max/min values inside an array**.

## **`$first` and `$last` in MongoDB Aggregation**

`$first` and `$last` are **aggregation operators** used in the **`$group`** stage to retrieve the **first** and **last** document in each group **based on the natural order of documents in MongoDB**.

- **`$first`** → Returns the **first document's value** in each group.
- **`$last`** → Returns the **last document's value** in each group.

---

### **1. Using `$first` and `$last` in `$group`**

These operators are useful when **grouping data by a field** and you want to get the first or last value.

### **Example: Get First and Last Employee in Each Department**

#### **Sample Data (`employees` Collection)**

```json
[
  { "_id": 1, "name": "Alice", "department": "IT", "joined": "2020-01-10" },
  { "_id": 2, "name": "Bob", "department": "HR", "joined": "2021-05-15" },
  { "_id": 3, "name": "Charlie", "department": "IT", "joined": "2022-07-20" },
  { "_id": 4, "name": "David", "department": "HR", "joined": "2023-03-25" }
]
```

#### **Aggregation Query**

```json
db.employees.aggregate([
  { $sort: { joined: 1 } },  // Sort by joining date (oldest to newest)
  {
    $group: {
      _id: "$department",
      firstEmployee: { $first: "$name" },  // First employee in each department
      lastEmployee: { $last: "$name" }    // Last employee in each department
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "firstEmployee": "Alice", "lastEmployee": "Charlie" },
  { "_id": "HR", "firstEmployee": "Bob", "lastEmployee": "David" }
]
```

✅ **`$first` gets the earliest employee** in each department, and **`$last` gets the most recent**.

---

### **2. `$first` and `$last` Without Sorting**

If you **don’t use `$sort`**, MongoDB will return the first and last document based on its **natural order in storage** (which may not be predictable).

To **ensure accuracy**, always use **`$sort`** before `$group` if order matters.

---

###
**Key Takeaways**

✅ **`$first`** → Returns the **first document's value** in a group.  
✅ **`$last`** → Returns the **last document's value** in a group.  
✅ Used in **`$group`** to retrieve first/last values **after sorting**.  
✅ Always **use `$sort` before `$group`** to ensure correct ordering.

## **`$push` in MongoDB Aggregation**

`$push` is an **aggregation operator** used in the **`$group`** stage to **create an array of values** from multiple documents in a group. It collects all values of a specified field and stores them in an array.

---

### **1. Using `$push` in `$group`**

### **Example: Group Employees by Department and Collect Names**

#### **Sample Data (`employees` Collection)**

```json
[
  { "_id": 1, "name": "Alice", "department": "IT" },
  { "_id": 2, "name": "Bob", "department": "HR" },
  { "_id": 3, "name": "Charlie", "department": "IT" },
  { "_id": 4, "name": "David", "department": "HR" }
]
```

#### **Aggregation Query**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      employees: { $push: "$name" }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "employees": ["Alice", "Charlie"] },
  { "_id": "HR", "employees": ["Bob", "David"] }
]
```

✅ **`$push` creates an array** of employee names for each department.

---

### **2. Using `$push` to Collect Multiple Fields**

You can **store entire objects** inside the array instead of just a single field.

### **Example: Store Employee Names & IDs Together**

#### **Aggregation Query**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      employees: { $push: { id: "$_id", name: "$name" } }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "employees": [ { "id": 1, "name": "Alice" }, { "id": 3, "name": "Charlie" } ] },
  { "_id": "HR", "employees": [ { "id": 2, "name": "Bob" }, { "id": 4, "name": "David" } ] }
]
```

✅ **`$push` can store objects** instead of just single values.

---

### **Key Takeaways**

✅ **`$push`** collects field values into an **array** when grouping documents.  
✅ Used in **`$group`** to gather values from multiple documents.  
✅ Can **store objects** (not just single values).  
✅ Does **not remove duplicates** (use `$addToSet` if you want unique values).

## **`$addToSet` in MongoDB Aggregation**

`$addToSet` is an **aggregation operator** used in the **`$group`** stage to **create an array** of **unique values** from multiple documents. It works similarly to `$push`, but it ensures that **duplicate values** are automatically removed, so the array contains only distinct values.

---

### **1. Using `$addToSet` in `$group`**

### **Example: Group Employees by Department and Collect Unique Skills**

#### **Sample Data (`employees` Collection)**

```json
[
  { "_id": 1, "name": "Alice", "department": "IT", "skills": ["Java", "Python"] },
  { "_id": 2, "name": "Bob", "department": "HR", "skills": ["Recruitment", "Communication"] },
  { "_id": 3, "name": "Charlie", "department": "IT", "skills": ["Python", "JavaScript"] },
  { "_id": 4, "name": "David", "department": "HR", "skills": ["Communication", "Management"] }
]
```

#### **Aggregation Query**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      uniqueSkills: { $addToSet: { $arrayElemAt: ["$skills", 0] } }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "uniqueSkills": ["Java", "Python", "JavaScript"] },
  { "_id": "HR", "uniqueSkills": ["Recruitment", "Communication", "Management"] }
]
```

✅ **`$addToSet` creates an array** with **unique skills** for each department.

---

### **2. Using `$addToSet` to Collect Multiple Fields**

You can use `$addToSet` to **create an array of unique values** of an object, rather than just a single field.

### **Example: Store Unique Employee Names with Skills**

#### **Aggregation Query**

```json
db.employees.aggregate([
  {
    $group: {
      _id: "$department",
      uniqueEmployees: { 
        $addToSet: { name: "$name", skills: "$skills" } 
      }
    }
  }
]);
```

#### **Output**

```json
[
  { "_id": "IT", "uniqueEmployees": [ { "name": "Alice", "skills": ["Java", "Python"] }, { "name": "Charlie", "skills": ["Python", "JavaScript"] } ] },
  { "_id": "HR", "uniqueEmployees": [ { "name": "Bob", "skills": ["Recruitment", "Communication"] }, { "name": "David", "skills": ["Communication", "Management"] } ] }
]
```

✅ **`$addToSet` ensures only unique combinations** of employee names and skills are added to the array.

---

### **Key Takeaways**

✅ **`$addToSet`** adds unique values (removes duplicates) to an array.  
✅ Used in **`$group`** to ensure uniqueness within the resulting array.  
✅ Works similar to **`$push`**, but without duplicates.  
✅ Can store **objects** and **arrays** with unique values.

# **Types of Joins in Databases (Simple Explanation for Beginners)

Joins are used in databases to **combine data from two tables** based on a common column. Think of it like merging two lists where the common information connects them.

Let’s take an **example** of two tables:

#### **Table 1: Customers**

|CustomerID|Name|
|---|---|
|1|Alice|
|2|Bob|
|3|Charlie|

#### **Table 2: Orders**

|OrderID|CustomerID|Product|
|---|---|---|
|101|1|Laptop|
|102|3|Phone|
|103|4|Tablet|

---

## **1. INNER JOIN (Only Matching Data)**

- Returns only the **matching rows** from both tables.
- If a customer **doesn’t have an order**, they won’t be included.
- If an order **doesn’t have a matching customer**, it won’t be included.

#### **Query:**

```sql
SELECT Customers.Name, Orders.Product
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

#### **Result:**

|Name|Product|
|---|---|
|Alice|Laptop|
|Charlie|Phone|

✅ **Bob is missing because he has no orders.**  
✅ **The order with CustomerID = 4 is missing because no such customer exists.**

---

## **2. LEFT JOIN (All Customers + Matching Orders)**

- Returns **all customers** from the `Customers` table.
- If a customer **doesn’t have an order**, it still appears, but with `NULL` for the product.

#### **Query:**

```sql
SELECT Customers.Name, Orders.Product
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

#### **Result:**

|Name|Product|
|---|---|
|Alice|Laptop|
|Bob|NULL|
|Charlie|Phone|

✅ **Bob is included but has no product (NULL) because he has no orders.**  
✅ **The order with CustomerID = 4 is still missing because no such customer exists.**

---

## **3. RIGHT JOIN (All Orders + Matching Customers)**

- Returns **all orders** from the `Orders` table.
- If an order has **no matching customer**, the customer name is `NULL`.

#### **Query:**

```sql
SELECT Customers.Name, Orders.Product
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

#### **Result:**

|Name|Product|
|---|---|
|Alice|Laptop|
|Charlie|Phone|
|NULL|Tablet|

✅ **The order with CustomerID = 4 is included, but there is no customer (NULL).**  
✅ **Bob is missing because he has no orders.**

---

## **4. FULL OUTER JOIN (All Customers + All Orders)**

- Returns **all customers and all orders**, even if they don’t match.
- If there’s no matching order, product is `NULL`.
- If there’s no matching customer, name is `NULL`.

#### **Query:**

```sql
SELECT Customers.Name, Orders.Product
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

#### **Result:**

|Name|Product|
|---|---|
|Alice|Laptop|
|Bob|NULL|
|Charlie|Phone|
|NULL|Tablet|

✅ **Bob is included but has NULL in the product column.**  
✅ **The order with CustomerID = 4 is included but has NULL in the name column.**

---

## **5. CROSS JOIN (All Possible Combinations)**

- Returns **every possible combination** of customers and orders.
- It **doesn’t care about matching columns**; it just **pairs every row with every other row**.

#### **Query:**

```sql
SELECT Customers.Name, Orders.Product
FROM Customers
CROSS JOIN Orders;
```

#### **Result:**

|Name|Product|
|---|---|
|Alice|Laptop|
|Alice|Phone|
|Alice|Tablet|
|Bob|Laptop|
|Bob|Phone|
|Bob|Tablet|
|Charlie|Laptop|
|Charlie|Phone|
|Charlie|Tablet|

✅ **Every customer is matched with every product, even if they didn’t order it.**

---

### **Summary (Simple Explanation)**

|**Join Type**|**What it Does**|**Includes Unmatched?**|
|---|---|---|
|**INNER JOIN**|Only customers **who have orders**|❌ No|
|**LEFT JOIN**|**All customers**, even if they don’t have orders|✅ Yes (Customers without orders)|
|**RIGHT JOIN**|**All orders**, even if they don’t have a customer|✅ Yes (Orders without customers)|
|**FULL OUTER JOIN**|**All customers & all orders**, even if they don’t match|✅ Yes (Both sides)|
|**CROSS JOIN**|Every possible combination|❌ No matching required|

---

### **Which Join Should You Use?**

- **Use INNER JOIN** when you only need **matching** data.
- **Use LEFT JOIN** when you need **all customers, even those with no orders**.
- **Use RIGHT JOIN** when you need **all orders, even those without a customer**.
- **Use FULL OUTER JOIN** when you need **everything from both tables**.
- **Use CROSS JOIN** when you need **every possible combination**.

### [note:-
### **Understanding Which Table is Joined from Where**

In SQL joins, we always have **two tables**, and we specify which one is the **"left table"** and which one is the **"right table"** in the `JOIN` statement.

#### **General Syntax of a JOIN:**



```sql
SELECT columns 
FROM LeftTable
JOIN_TYPE RightTable ON LeftTable.common_column = RightTable.common_column;

```

- **Left Table:** The table mentioned **first** in the `FROM` clause.
- **Right Table:** The table mentioned **after** the `JOIN` keyword.



# **Aggregation Pipeline Stages in MongoDB


11. **`$bucketAuto`** – Automatically distributes data into equal-sized buckets
12. 
13. **`$set`** – Alias for `$addFields`
14. **`$unset`** – Removes fields from documents
15. **`$replaceRoot`** – Replaces the root document with a specified sub-document
16. **`$replaceWith`** – Alias for `$replaceRoot`
17. 
18. **`$out`** – Saves results to a collection
19. 
20. **`$sample`** – Randomly selects a specified number of documents
21. **`$redact`** – Restricts data access at the document level
22. **`$geoNear`** – Finds documents based on geospatial proximity