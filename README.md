# Spring_Batch_Configuration
# 🚀 Spring Batch: CSV-to-Database Migration Engine

A high-performance, scalable Data Migration pipeline built with **Spring Boot 3** and **Spring Batch 5**. This project demonstrates the **ETL (Extract, Transform, Load)** pattern, migrating complex datasets from flat-file sources (CSV) into a relational database (MySQL).

---


## 📌 Project Overview
The goal of this project is to automate the migration of large volumes of data while ensuring data integrity and transaction management. It uses **Chunk-Oriented Processing** to handle data efficiently without exhausting system memory.

### Key Technical Highlights:
* **ETL Pipeline:** Robust extraction from CSV, custom transformation logic, and JPA-based loading.
* **Chunk-Based Processing:** Processes data in configurable chunks (e.g., 10 records per transaction) for optimal performance.
* **Automated Schema Management:** Integrated with Spring Data JPA for seamless table mapping and creation.
* **Job Repository:** Tracks job execution metadata (Start time, End time, Status) in the database.

---
