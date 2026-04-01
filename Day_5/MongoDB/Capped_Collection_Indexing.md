# 📘 MongoDB Lab – Capped Collection & Indexing

## 🧪 1. Capped Collection in MongoDB

### 🔹 Capped Collection - Aim

To create and perform operations on a capped collection in MongoDB.

#### 🔹 Capped Collection - Theory

A capped collection is a fixed-size collection that:

- Stores documents in insertion order
- Automatically removes old documents when size limit is reached
- Works like a circular queue

#### 🔹 Capped Collection - Shell Script

```javascript
// Step 1: Switch to database
use cappedDB

// Step 2: Create capped collection
db.createCollection("logs", {
    capped: true,
    size: 5000,
    max: 5
})

// Step 3: Insert documents
db.logs.insertMany([
    { msg: "Log 1" },
    { msg: "Log 2" },
    { msg: "Log 3" },
    { msg: "Log 4" },
    { msg: "Log 5" }
])

// Step 4: Display documents
db.logs.find().pretty()

// Step 5: Insert one more document
db.logs.insertOne({ msg: "Log 6" })

// Step 6: Display updated documents
db.logs.find().pretty()
```

#### 🔹 Capped Collection - Expected Output

```javascript
{ "msg": "Log 2" }
{ "msg": "Log 3" }
{ "msg": "Log 4" }
{ "msg": "Log 5" }
{ "msg": "Log 6" }
```

#### 🔹 Capped Collection - Observation

- Oldest document (Log 1) is removed automatically
- Collection always maintains fixed size (5 documents)

#### 🔹 Capped Collection - Conclusion

Capped collections efficiently manage fixed-size data by automatically overwriting old records.

## 🧪 2. MongoDB Indexing

### 🔹 Indexing - Aim

To create and demonstrate different types of indexes in MongoDB.

#### 🔹 Indexing - Theory

Indexes improve query performance by allowing faster data retrieval.

#### 🔹 Types of Indexes

- Single Field Index
- Compound Index
- Multikey Index
- Text Index
- Hashed Index
- Unique Index
- Sparse Index
- TTL Index

#### 🔹 Indexing - Shell Script

```javascript
// Step 1: Use database
use indexingDB

// Step 2: Insert sample data
db.users.insertMany([
    { name: "Alice", age: 25, city: "Delhi", tags: ["tech", "mongodb"], createdAt: new Date() },
    { name: "Bob", age: 30, city: "Mumbai", tags: ["coding", "node"], createdAt: new Date() },
    { name: "Charlie", age: 28, city: "Kolkata", tags: ["mongodb", "database"], createdAt: new Date() },
    { name: "David", age: 35, city: "Chennai", tags: ["python", "ai"], createdAt: new Date() }
])

// 1. Single Field Index
db.users.createIndex({ name: 1 })

// 2. Compound Index
db.users.createIndex({ age: 1, city: -1 })

// 3. Multikey Index
db.users.createIndex({ tags: 1 })

// 4. Text Index
db.users.createIndex({ name: "text", city: "text" })

// 5. Hashed Index
db.users.createIndex({ name: "hashed" })

// 6. Unique Index
db.users.createIndex({ name: 1 }, { unique: true })

// 7. Sparse Index
db.users.createIndex({ age: 1 }, { sparse: true })

// 8. TTL Index
db.users.createIndex({ createdAt: 1 }, { expireAfterSeconds: 60 })

// View indexes
db.users.getIndexes()

// Drop index example
db.users.dropIndex({ name: 1 })
```

#### 🔹 Indexing - Expected Output

```javascript
[
  { "key": { "_id": 1 }, "name": "_id_" },
  { "key": { "name": 1 }, "name": "name_1" },
  { "key": { "age": 1, "city": -1 }, "name": "age_1_city_-1" },
  { "key": { "tags": 1 }, "name": "tags_1" },
  { "key": { "name": "text", "city": "text" }, "name": "name_text_city_text" },
  { "key": { "name": "hashed" }, "name": "name_hashed" },
  { "key": { "name": 1 }, "name": "name_1_unique", "unique": true },
  { "key": { "age": 1 }, "name": "age_1_sparse", "sparse": true },
  { "key": { "createdAt": 1 }, "name": "createdAt_1", "expireAfterSeconds": 60 }
]
```

#### 🔹 Indexing - Observation

- Various types of indexes created successfully
- Each index serves different query optimization purposes
- TTL index automatically removes documents after specified time

#### 🔹 Indexing - Conclusion

MongoDB indexing significantly improves query performance and provides various indexing strategies for different use cases.
