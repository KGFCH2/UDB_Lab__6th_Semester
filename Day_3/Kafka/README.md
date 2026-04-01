# Apache Kafka (Windows) ⚡

**Adamas University** | 6th Semester | **Babin Bid**

This project runs a Kafka broker in Docker and sends sample IoT events from `producer.py`.

## 👨‍💻 Author Profile

* **Name:** Babin Bid
* **LinkedIn:** [Babin Bid](https://www.linkedin.com/in/babinbid123/)
* **GitHub:** [@KGFCH2](https://github.com/KGFCH2)
* **University:** Adamas University

## 🚀 What Runs Here

* 🐳 Kafka broker runs in Docker from `docker-compose.yml`.
* 🐍 Python producer sends JSON messages to topic `iot_sensor_data`.
* 🚫 No MongoDB setup is included in this run flow.

## ✅ Prerequisites

* 🐳 Docker Desktop (running)
* 🐍 Python 3.x
* 📦 pip

## 📦 Install Python Dependency

Run once in this folder:

```powershell
python -m pip install kafka-python
```

## ▶️ Minimal Kafka Broker Activation

Run these commands in order to start and verify the Kafka broker:

```powershell
cd Kafka
docker compose up -d broker
docker ps --filter "name=kafka"
```

Optional readiness check:

```powershell
docker logs --tail 30 kafka
```

**📋 Expected Output:**

After `docker compose up -d broker`:

* 🔄 No immediate output (runs in background).

After `docker ps --filter "name=kafka"`:

```text

CONTAINER ID   IMAGE                 COMMAND                  CREATED      STATUS          PORTS                                         NAMES
a9fd71be4e4c   apache/kafka:latest   "/__cacert_entrypoin…"   6 days ago   Up 30 seconds   0.0.0.0:9092->9092/tcp, [::]:9092->9092/tcp   kafka
```

After `docker logs --tail 30 kafka` (📝 sample startup logs):

```text

kafka  | [2026-03-24 18:46:33,648] INFO Created log for partition __consumer_offsets-43 in /tmp/kafka-logs/__consumer_offsets-43 with properties {cleanup.policy=compact, compression.type="producer", segment.bytes=104857600} (kafka.log.LogManager)
kafka  | [2026-03-24 18:46:33,648] INFO [Partition __consumer_offsets-43 broker=1] No checkpointed highwatermark is found for partition __consumer_offsets-43 (kafka.cluster.Partition)
kafka  | [2026-03-24 18:46:33,649] INFO [Partition __consumer_offsets-43 broker=1] Log loaded for partition __consumer_offsets-43 with initial high watermark 0 (kafka.cluster.Partition)
...
kafka  | [2026-03-24 18:46:34,403] INFO [GroupCoordinator id=1 topic=__consumer_offsets partition=36] Dynamic member with unknown member id joins group iot-mongo-consumer in Empty state. Created a new member id kafka-python-2.3.0-4023663f-c164-46f6-b0f2-df1a85afab40 and requesting the member to rejoin with this id. (org.apache.kafka.coordinator.group.GroupMetadataManager)
```

Broker is active when:

* ✅ Container `kafka` shows `Up` in `docker ps`.
* 📊 Logs show normal `INFO` startup lines (like `__consumer_offsets` loading) without crash/restart loops.

```powershell
docker ps
```

Expected running container:

* Name: `kafka`
* Image: `apache/kafka:latest`
* Port mapping: `0.0.0.0:9092->9092/tcp`

## 📤 Run Producer

In a new terminal (same folder):

```powershell
python producer.py
```

**📋 Expected output pattern:**

```text
Producer started. Sending data to topic: iot_sensor_data
Sent to Kafka: {...}
Sent to Kafka: {...}
```

## 🛑 Stop Services

If running producer, press `Ctrl + C` in that terminal.

Stop Kafka compose service:

```powershell
docker compose down
```

## 🧠 Docker + Kafka Logic (Accurate to This Setup)

`docker-compose.yml` starts one Kafka container in KRaft combined mode (broker + controller in one node).

* 🔧 `KAFKA_PROCESS_ROLES=broker,controller`: single container handles both roles.
* 🔗 `KAFKA_LISTENERS=PLAINTEXT://:9092,CONTROLLER://:9093`: broker/client traffic on `9092`, controller traffic on `9093`.
* 🌐 `KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9092`: clients on host machine connect to `localhost:9092`.
* 👥 `KAFKA_CONTROLLER_QUORUM_VOTERS=1@localhost:9093`: one-node controller quorum.
* 🔄 Replication settings are set to `1` for single-node local development.

This means the producer can publish directly to `localhost:9092` without extra cluster setup.

*Created with ❤️ by **Babin Bid** | Adamas University*
