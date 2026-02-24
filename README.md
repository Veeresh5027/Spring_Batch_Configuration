# 🚀 Spring Batch: Customer Data ETL Pipeline

A high-performance Data Migration engine built with **Spring Boot 3.2+** and **Spring Batch 5**. This project demonstrates the **ETL (Extract, Transform, Load)** pattern, specifically designed to process a large-scale `data.csv` file and persist it into a **MySQL** database with built-in transaction management.

---

## 📌 Project Overview
This project solves the challenge of migrating bulk records without crashing system memory. It implements **Chunk-Oriented Processing**, where data is read, transformed, and written in small, manageable blocks (Chunks).



### 🛠 Technical Architecture
The job follows a strictly decoupled architecture:
1. **Reader (Extract):** `FlatFileItemReader` reads `data.csv` using a `DelimitedLineTokenizer`. It maps CSV headers to the `Customer` entity.
2. **Processor (Transform):** A custom `ItemProcessor` that acts as a business logic filter or transformer (e.g., data validation or cleaning).
3. **Writer (Load):** `RepositoryItemWriter` which uses Spring Data JPA to save entities to the MySQL database in bulk.

---

## 🏗 Key Features & Logic
* **Chunk-Oriented Processing:** Configured with a chunk size of **10**, ensuring atomic transactions and high throughput.
* **Spring Batch Metadata:** Automatically creates and manages `BATCH_JOB_INSTANCE`, `BATCH_STEP_EXECUTION`, and other tables to track job state.
* **Fault Tolerance:** Built to handle large datasets; if the job is interrupted, the metadata allows it to be restarted from the last successful chunk.
* **Modern Configuration:** Uses the latest Spring Batch 5.x `JobBuilder` and `StepBuilder` APIs.

---

## 📂 Repository Structure
* **`config/`**: Contains `CustomerBatchConfig` where the Job and Step beans are defined.
* **`entity/`**: The `Customer` JPA entity representing the target database schema.
* **`processor/`**: Custom logic to transform or filter data during the batch process.
* **`resources/data.csv`**: The primary data source containing customer records.

---

## 🛠 Tech Stack
| Category | Technology |
| :--- | :--- |
| **Java Version** | Java 17+ |
| **Framework** | Spring Boot 3.x, Spring Batch 5.x |
| **Database** | MySQL 8.0 |
| **ORM** | Spring Data JPA |
| **Build Tool** | Maven |

---

## 🚀 Setup & Execution

### 1. Database & Environment Setup
Create your MySQL database and update `src/main/resources/application.properties` with your credentials:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/your_db_name
spring.datasource.username=your_username
spring.datasource.password=your_password

# Required for Spring Batch 5+ to manage metadata tables
spring.batch.jdbc.initialize-schema=always
spring.jpa.hibernate.ddl-auto=update

# Clone the repository
git clone [https://github.com/Veeresh5027/Spring_Batch_Configuration.git](https://github.com/Veeresh5027/Spring_Batch_Configuration.git)

# Navigate to the project directory
cd Spring_Batch_Configuration

# Build the project and download dependencies
mvn clean install

# Run the Spring Boot Application
mvn spring-boot:run
