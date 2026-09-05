# FlowSync: Intelligent Real-Time Streaming Analytics

An end-to-end **Data Engineering and AI platform** for processing, validating, storing, and analyzing continuously generated streaming data in real time.

---

##  Overview

**FlowSync** is a real-time streaming analytics platform designed to handle high-volume, continuously generated data with minimal latency.

The system collects raw streaming events from multiple sources such as **IoT devices, application logs, APIs, and transactional systems**. These events are processed and transformed in real time, validated for data quality, stored using scalable storage technologies, and analyzed using machine learning for anomaly detection.

The platform combines **real-time data engineering with AI-based analytics** to convert raw streaming data into clean, reliable, and actionable information.

---

##  Problem Statement

Modern applications continuously generate large amounts of data from APIs, IoT devices, application logs, and operational systems.

Traditional batch-processing systems can introduce significant delays, making it difficult to obtain timely insights. Streaming data can also contain:

* Missing values
* Duplicate records
* Schema inconsistencies
* Malformed inputs
* Unusual or anomalous events

Data is often distributed across different processing, storage, and analytics environments, making real-time monitoring difficult.

**FlowSync addresses these challenges by providing an integrated pipeline for real-time data ingestion, processing, data-quality validation, anomaly detection, storage, API access, and monitoring.**

---

##  Objectives

* Build a low-latency real-time data ingestion pipeline.
* Process continuously generated streaming events.
* Perform automated data-quality validation.
* Detect anomalies and unusual behavioral patterns.
* Store raw and processed data efficiently.
* Provide APIs for accessing processed data and ML results.
* Provide real-time visualization and monitoring.
* Build a scalable and reliable streaming architecture.

---

##  Proposed Solution

FlowSync provides an end-to-end streaming data pipeline consisting of multiple stages.

### 1. Real-Time Data Ingestion

**Apache Kafka** collects continuous events from multiple data sources and acts as the real-time ingestion layer.

### 2. Stream Processing

**Apache Spark Structured Streaming** and **PySpark** process incoming events in real time. The system performs transformations and aggregations while maintaining low processing latency.

### 3. Data Quality

**Great Expectations** validates incoming data by performing schema, consistency, and quality checks. This helps identify invalid and unreliable records before they are used for downstream analytics.

### 4. Hybrid Storage

Processed and raw datasets are stored using:

* **MinIO** – S3-compatible object storage
* **Apache Parquet** – Efficient analytical data storage
* **PostgreSQL** – Structured relational data persistence

### 5. Anomaly Detection

**Scikit-learn** is used to analyze processed streaming data and identify unusual patterns and outliers.

### 6. API Layer

**FastAPI** provides high-performance REST APIs for accessing processed data and machine-learning services.

### 7. Monitoring and Visualization

**Grafana** provides real-time dashboards for monitoring pipeline performance and displaying detected anomalies.

---

##  System Workflow

```text
Data Sources
     │
     ▼
Apache Kafka
     │
     ▼
Spark Structured Streaming
     │
     ▼
Data Quality Validation
(Great Expectations)
     │
     ▼
Data Storage
 ┌───────────────┐
 │     MinIO     │
 │    Parquet    │
 │  PostgreSQL   │
 └───────────────┘
     │
     ▼
Anomaly Detection
   (Scikit-learn)
     │
     ▼
FastAPI
     │
     ▼
Grafana Dashboard
```

### Workflow Explanation

1. Data is continuously generated from IoT devices, APIs, application logs, and transactional systems.
2. Apache Kafka receives and streams these events.
3. Spark Structured Streaming consumes the events and performs real-time processing.
4. Great Expectations validates the quality and consistency of the processed data.
5. Validated data is stored in MinIO, Parquet, and PostgreSQL.
6. Scikit-learn analyzes the processed data and identifies anomalies.
7. FastAPI exposes processed data and machine-learning results.
8. Grafana visualizes real-time system performance and detected anomalies.

###  Workflow Summary

**Collect → Process → Validate → Store → Detect → Serve → Monitor**

---

##  Key Features

*  Real-time event ingestion
*  Continuous stream processing
*  Automated data-quality validation
*  Data cleansing and transformation
*  Hybrid data storage
*  AI-based anomaly detection
*  REST API access
*  Real-time monitoring dashboards
*  Scalable streaming architecture
*  Containerized deployment support

---

## Novelty

The main novelty of FlowSync is its **end-to-end integration of multiple data engineering and AI capabilities into a single real-time streaming platform**.

Instead of focusing only on stream processing, data quality, or anomaly detection, FlowSync combines:

**Real-time ingestion + stream processing + data-quality validation + hybrid storage + anomaly detection + API serving + unified monitoring**

into one integrated pipeline.

The novelty is therefore primarily **architectural and integrative**, rather than introducing a completely new machine-learning algorithm.

---

## Technology Stack

| Category           | Technology                 | Purpose                             |
| ------------------ | -------------------------- | ----------------------------------- |
| Programming        | Python, PySpark            | Pipeline development and processing |
| Data Ingestion     | Apache Kafka               | Real-time event streaming           |
| Stream Processing  | Spark Structured Streaming | Real-time transformation            |
| Data Quality       | Great Expectations         | Validation and quality checks       |
| Data Lake          | MinIO                      | S3-compatible object storage        |
| Analytical Storage | Apache Parquet             | Efficient analytical storage        |
| Database           | PostgreSQL                 | Structured data persistence         |
| Machine Learning   | Scikit-learn               | Anomaly detection                   |
| API                | FastAPI                    | Data and ML services                |
| Monitoring         | Grafana                    | Real-time dashboards                |
| DevOps             | Docker                     | Containerization                    |
| Version Control    | Git                        | Source-code management              |

---

## Architecture

```text
                    ┌──────────────────────┐
                    │     Data Sources     │
                    │ IoT | APIs | Logs    │
                    │ Transaction Systems  │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Apache Kafka      │
                    │  Real-Time Ingestion │
                    └──────────┬───────────┘
                               │
                               ▼
              ┌────────────────────────────────┐
              │ Spark Structured Streaming     │
              │          + PySpark             │
              │ Processing & Transformation    │
              └───────────────┬────────────────┘
                              │
                              ▼
                    ┌──────────────────────┐
                    │  Great Expectations  │
                    │   Data Validation    │
                    └──────────┬───────────┘
                               │
                               ▼
             ┌──────────────────────────────────┐
             │          Hybrid Storage          │
             │                                  │
             │ MinIO | Apache Parquet | PostgreSQL │
             └────────────────┬─────────────────┘
                              │
                              ▼
                    ┌──────────────────────┐
                    │   Scikit-learn       │
                    │ Anomaly Detection    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │       FastAPI        │
                    │      REST APIs       │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │       Grafana        │
                    │ Monitoring & Alerts  │
                    └──────────────────────┘
```

---

## Expected Outcomes

FlowSync is designed to provide:

* Faster processing of continuously generated data.
* Improved data reliability through automated validation.
* Early identification of unusual events.
* Scalable storage for raw and processed datasets.
* Centralized monitoring and visualization.
* Better availability of processed data through APIs.
* Faster insights and improved decision-making.

---

## Future Scope

The platform can be extended with:

* Automated alerting for critical anomalies.
* Advanced machine-learning models.
* Real-time prediction capabilities.
* Cloud-based deployment.
* Automated pipeline scheduling.
* More advanced analytics dashboards.
* Support for additional streaming data sources.

---

##  Team

| Name          | Roll number |
| ------------- | ----------- |
| Y. Nihitha    | 2420090099  |
| S. Harini     | 2420030523  |
| A. Sri Anitha | 2420090117  |

### Project Guide

**Dr. N. Shirisha**
Associate Professor

---

##  Academic Information

**Course:** Fundamentals of Data Engineering
**Course Code:** 24DEA3101
**Academic Year:** 2026–27

---

##  Project Focus

**FlowSync: Intelligent Real-Time Streaming Analytics**

> *Transforming continuous raw streaming events into clean, reliable, and actionable intelligence through real-time data engineering and AI.*
