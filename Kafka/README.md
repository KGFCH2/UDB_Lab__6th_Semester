# Apache Kafka (Windows) ⚡

**Adamas University** | 6th Semester | **Babin Bid**

This project runs a Kafka broker in Docker and sends sample IoT events from `producer.py`.

## 👨‍💻 Author Profile

* **Name:** Babin Bid
* **LinkedIn:** [Babin Bid](https://www.linkedin.com/in/babinbid123/)
* **GitHub:** [@KGFCH2](https://github.com/KGFCH2)
* **University:** Adamas University

## 🚀 What Runs Here

* Kafka broker runs in Docker from `docker-compose.yml`.
* Python producer sends JSON messages to topic `iot_sensor_data`.
* No MongoDB setup is included in this run flow.

## ✅ Prerequisites

* Docker Desktop (running)
* Python 3.x
* pip

## 📦 Install Python Dependency

Run once in this folder:

```powershell
python -m pip install kafka-python
```

## ▶️ Main Run Command

Start Kafka (foreground mode):

```powershell
docker compose up
```

This is the main run command for the Kafka service in this project.

If you prefer detached mode:

```powershell
docker compose up -d
```

## 🔎 Verify Kafka Container

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

Expected output pattern:

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

* `KAFKA_PROCESS_ROLES=broker,controller`: single container handles both roles.
* `KAFKA_LISTENERS=PLAINTEXT://:9092,CONTROLLER://:9093`: broker/client traffic on `9092`, controller traffic on `9093`.
* `KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9092`: clients on host machine connect to `localhost:9092`.
* `KAFKA_CONTROLLER_QUORUM_VOTERS=1@localhost:9093`: one-node controller quorum.
* Replication settings are set to `1` for single-node local development.

This means the producer can publish directly to `localhost:9092` without extra cluster setup.

*Created with ❤️ by **Babin Bid** | Adamas University*
