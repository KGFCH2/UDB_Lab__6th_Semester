# 📘 Experiment: Neo4j CRUD Operations

## Aim

To perform CRUD (Create, Read, Update, Delete) operations in Neo4j database and establish relationships between nodes.

## Theoretical Concepts

Neo4j is a graph database that stores data in the form of nodes, relationships, and properties.

- **Node** → Represents entities (Author, Book, Reader)
- **Relationship** → Connects nodes (WROTE, READS)
- **Cypher Query Language (CQL)** → Used to interact with Neo4j

CRUD operations:

- **Create** → Insert nodes and relationships
- **Read** → Retrieve data
- **Update** → Modify existing data
- **Delete** → Remove nodes or relationships

## Equipment Required

- Neo4j Desktop / Neo4j Browser
- Computer System

## Procedure

### Step 1: Create Nodes

```text
CREATE (a:Author {name: "Babin", age: 20})
CREATE (b:Book {title: "AI Basics", price: 500})
CREATE (r:Reader {name: "Rahul"})
```

### Step 2: Create Relationships

```text
MATCH (a:Author {name: "Babin"}), (b:Book {title: "AI Basics"})
CREATE (a)-[:WROTE]->(b)
MATCH (r:Reader {name: "Rahul"}), (b:Book {title: "AI Basics"})
CREATE (r)-[:READS]->(b)
```

### Step 3: Read Data

```text
MATCH (n)
RETURN n
MATCH (a:Author)-[r]->(b:Book)
RETURN a, r, b
```

### Step 4: Update Data

```text
MATCH (a:Author {name: "Babin"})
SET a.age = 21
RETURN a
```

### Step 5: Delete Relationship

```text
MATCH (a:Author)-[r:WROTE]->(b:Book)
DELETE r
```

### Step 6: Delete Node

```text
MATCH (a:Author {name: "Babin"})
DETACH DELETE a
```

### Step 7: Cyclic Relationship

```text
MATCH (a:Author), (b:Book), (r:Reader)
CREATE (a)-[:WRITES]->(b),
       (b)-[:READ_BY]->(r),
       (r)-[:FOLLOWS]->(a)
```

## Observation Table

| Operation | Query Used | Result |
| ----------- | ------------ | -------- |
| Create | CREATE nodes | Nodes created |
| Read | MATCH | Data displayed |
| Update | SET | Data modified |
| Delete | DELETE | Data removed |

## Lab Analysis

- Nodes and relationships were successfully created.
- Data retrieval was performed using MATCH queries.
- Existing data was updated using SET.
- Relationships and nodes were deleted using DELETE and DETACH DELETE.
- A cyclic relationship was established among nodes.

## Conclusion

CRUD operations in Neo4j were successfully implemented using Cypher Query Language. The experiment demonstrates how graph databases efficiently manage interconnected data.
