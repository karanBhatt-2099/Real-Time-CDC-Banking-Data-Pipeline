#  Banking Modern Data Stack


![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=for-the-badge&logo=snowflake&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=for-the-badge&logo=dbt&logoColor=white)
![Airflow](https://img.shields.io/badge/Airflow-017CEE?style=for-the-badge&logo=apacheairflow&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-000000?style=for-the-badge&logo=apachekafka&logoColor=white)
![Debezium](https://img.shields.io/badge/Debezium-161616?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

---

#  Project Overview

This project demonstrates an **end-to-end Modern Data Stack pipeline for a Banking domain**.

It simulates customer, account, and transaction data, streams changes in real time, transforms them into analytics-ready models, and visualizes insights following industry best practices in **CDC, Data Warehousing, DBT, Airflow, and CI/CD**.

---

## Pipeline Flow

```text
PostgreSQL
      │
      ▼
Kafka + Debezium (CDC)
      │
      ▼
MinIO (S3 Storage)
      │
      ▼
Airflow Orchestration
      │
      ▼
Snowflake Warehouse
(Bronze → Silver → Gold)
      │
      ▼
DBT Transformations
(Facts, Dimensions, Snapshots)
      │
      ▼
Power BI Dashboard
```

---

#  Tech Stack

| Layer | Technology |
|---------|------------|
| Source OLTP | PostgreSQL |
| Data Simulation | Python + Faker |
| Streaming | Apache Kafka |
| CDC | Debezium |
| Object Storage | MinIO (S3 Compatible) |
| Orchestration | Apache Airflow |
| Data Warehouse | Snowflake |
| Transformations | DBT |
| Visualization | Power BI |
| Containerization | Docker |
| CI/CD | GitHub Actions |

---

# ✅ Key Features

-  PostgreSQL OLTP source system with ACID guarantees
-  Synthetic banking dataset (customers, accounts, transactions)
-  Change Data Capture (CDC) using Kafka + Debezium
-  Bronze → Silver → Gold architecture in Snowflake
-  DBT staging, dimensions, facts, and snapshots
-  SCD Type-2 history tracking
-  Airflow DAG orchestration
-  Dockerized infrastructure
-  Automated CI/CD using GitHub Actions
-  Analytics-ready business models

---

# 📂 Repository Structure

```text
banking-modern-datastack/
│
├── .github/
│   └── workflows/
│       ├── ci.yml
│       └── cd.yml
│
├── banking_dbt/
│   ├── models/
│   │   ├── staging/
│   │   ├── marts/
│   │   └── sources.yml
│   ├── snapshots/
│   └── dbt_project.yml
│
├── consumer/
│   └── kafka_to_minio.py
│
├── data-generator/
│   └── faker_generator.py
│
├── docker/
│   └── dags/
│       ├── minio_to_snowflake.py
│       └── scd_snapshots.py
│
├── kafka-debezium/
│   └── generate_and_post_connector.py
│
├── postgres/
│   └── schema.sql
│
├── docker-compose.yml
├── dockerfile-airflow.dockerfile
├── requirements.txt
└── README.md
```

---

# ⚙️ Step-by-Step Implementation

## 1️⃣ Data Simulation

- Generated synthetic banking data using **Faker**
- Created:
  - Customers
  - Accounts
  - Transactions
- Loaded data into PostgreSQL
- Configurable via `config.yaml`

---

## 2️⃣ Kafka + Debezium CDC

- Configured Kafka Connect
- Captured PostgreSQL WAL changes
- Streamed change events in real time
- Persisted raw events into MinIO

---

## 3️⃣ Airflow Orchestration

Airflow DAGs automate:

- MinIO → Snowflake ingestion
- Incremental loads
- Snapshot execution
- Data quality workflows

---

## 4️⃣ Snowflake Warehouse

Implemented a Medallion architecture:

### 🥉 Bronze Layer
Raw CDC events

### 🥈 Silver Layer
Cleaned and standardized data

### 🥇 Gold Layer
Business-ready analytical models

---

## 5️⃣ DBT Transformations

### Staging Models
Clean source tables

### Fact Models
- Fact Transactions

### Dimension Models
- Dim Customers
- Dim Accounts

### Snapshots
SCD Type-2 history tracking for accounts and customers.

---

## 6️⃣ CI/CD with GitHub Actions

### CI Pipeline

- Lint checks
- dbt compile
- dbt tests

### CD Pipeline

- Deploy Airflow DAGs
- Execute DBT models
- Production-ready workflows

---

# 📊 Final Deliverables

 End-to-end CDC pipeline from PostgreSQL → Snowflake

 Bronze → Silver → Gold warehouse architecture

 DBT models (Facts, Dimensions, Snapshots)

 Airflow orchestration

 Synthetic banking dataset

 Dockerized environment

 CI/CD workflows with GitHub Actions

 Power BI dashboards for analytics

---

#  Modern Data Stack Flow

```text
PostgreSQL
     ↓
Kafka + Debezium
     ↓
MinIO (S3)
     ↓
Airflow
     ↓
Snowflake
(Bronze → Silver → Gold)
     ↓
DBT
     ↓
Power BI
```

---
