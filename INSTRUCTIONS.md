# 📖 UDB Lab Instructions & Track Map

**Course:** Unstructured Database Lab | **Author:** Babin Bid

This document explains the organization of the Unstructured Database Lab, covering MongoDB (Mongosh), Apache Kafka, and Neo4j tracks.

---

## 📂 Directory Structure

### 🍃 [Mongosh/](./Mongosh/)

* **Focus:** NoSQL operations and JavaScript-driven automation.
* **Contents:**
  * `Day_1.txt`: Core shell fundamentals, CRUD, and array manipulation logs.
  * `Day_2.txt`: Advanced API integration and real-time watcher implementation.
  * `README.md`: High-level navigation hub for the Mongosh track.

### 🎡 [Kafka/](./Kafka/)

* **Focus:** Event streaming and distributed message queuing.
* **Contents:**
  * `README.md`: Detailed overview of topic management and producer/consumer logic.
  * *Upcoming:* Topic configuration scripts and system logs.

### 🕸️ [Neo4j/](./Neo4j/)

* **Focus:** Graph database operations and Cypher query language.
* **Contents:**
  * `README.md`: High-level navigation hub for the Neo4j track.
  * `CRUD_Operations.md`: Detailed experiment on Create, Read, Update, Delete operations and relationship management.

---

## 🛠️ Usage Instructions

### MongoDB (Mongosh)

1. **Launch:** Type `mongosh` in your terminal to enter the interactive shell.
2. **Scripts:** Use the copy-pasteable snippets from the `Day_x.txt` files directly into the shell.
3. **APIs:** For Day 2 scripts, ensure active internet connectivity to fetch data from the REST API endpoints.

### Apache Kafka

1. **Services:** Ensure Zookeeper and Kafka Broker are active.
2. **Commands:** Use the CLI tools like `kafka-topics.sh` for administrative tasks and console producers for message ingestion.

### Neo4j

1. **Launch:** Open Neo4j Desktop or access Neo4j Browser at `http://localhost:7474`.
2. **Queries:** Execute Cypher commands in the query editor for graph operations.
3. **Browser:** Use the built-in browser interface for visualizing nodes and relationships.

---

Created with ❤️ by **Babin Bid** | Adamas University
