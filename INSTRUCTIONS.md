# 📖 UDB Lab Instructions & Track Map

**Course:** Unstructured Database Lab | **Author:** Babin Bid

This document explains the organization of the Unstructured Database Lab, covering MongoDB (Mongosh), Apache Kafka, and Neo4j tracks.

---

## 📂 Directory Structure

### 📅 [Day 1 & 2](./Day_1_&_2/)

* **Technology:** MongoDB (Mongosh)
* **Focus:** NoSQL operations and JavaScript-driven automation.
* **Contents:**
  * `Mongosh/Day_1.txt`: Core shell fundamentals, CRUD, and array manipulation logs.
  * `Mongosh/Day_2.txt`: Advanced API integration and real-time watcher implementation.
  * `Mongosh/README.md`: High-level navigation hub for the Mongosh track.

### 📅 [Day 3](./Day_3/)

* **Technology:** Apache Kafka
* **Focus:** Event streaming and distributed message queuing.
* **Contents:**
  * `Kafka/README.md`: Detailed overview of topic management and producer/consumer logic.
  * `Kafka/consumer.py`: Python consumer implementation.
  * `Kafka/producer.py`: Python producer implementation.
  * `Kafka/docker-compose.yml`: Docker configuration for Kafka broker.

### 📅 [Day 4](./Day_4/)

* **Technology:** Neo4j Graph Database
* **Focus:** Graph database operations and Cypher query language.
* **Contents:**
  * `Neo4j/README.md`: High-level navigation hub for the Neo4j track.
  * `Neo4j/CRUD_Operations.md`: Detailed experiment on Create, Read, Update, Delete operations.

### 📅 [Day 5](./Day_5/README.md)

* **Technology:** MongoDB Advanced Features
* **Focus:** Advanced database concepts including capped collections and indexing.
* **Contents:**
  * `MongoDB/Capped_Collection_Indexing.md`: Detailed experiments on capped collections and various indexing strategies.

---

## 🛠️ Usage Instructions

### Day 1 & 2: MongoDB (Mongosh)

1. **Navigate:** Go to `Day_1_&_2/Mongosh/` folder.
2. **Launch:** Type `mongosh` in your terminal to enter the interactive shell.
3. **Scripts:** Use the copy-pasteable snippets from the `Day_1.txt` and `Day_2.txt` files directly into the shell.
4. **APIs:** For Day 2 scripts, ensure active internet connectivity to fetch data from REST API endpoints.

### Day 3: Apache Kafka

1. **Navigate:** Go to `Day_3/Kafka/` folder.
2. **Services:** Ensure Zookeeper and Kafka Broker are active (use `docker-compose.yml`).
3. **Producer:** Run `producer.py` to send messages to the topic.
4. **Consumer:** Run `consumer.py` to receive and process messages.
5. **Commands:** Use CLI tools like `kafka-topics.sh` for administrative tasks.

### Day 4: Neo4j

1. **Navigate:** Go to `Day_4/Neo4j/` folder.
2. **Launch:** Open Neo4j Desktop or access Neo4j Browser at `http://localhost:7474`.
3. **Queries:** Execute Cypher commands from `CRUD_Operations.md` in the query editor.
4. **Browser:** Use the built-in browser interface for visualizing nodes and relationships.

### Day 5: Advanced Topics

1. **Navigate:** Go to `Day_5/MongoDB/` folder.
2. **Launch:** Type `mongosh` in your terminal to enter the interactive shell.
3. **Scripts:** Execute the shell scripts from `Capped_Collection_Indexing.md` for capped collections and indexing experiments.
4. **Monitor:** Use `db.collection.getIndexes()` to view created indexes and `db.collection.stats()` for collection statistics.

---

Created with ❤️ by **Babin Bid** | Adamas University
