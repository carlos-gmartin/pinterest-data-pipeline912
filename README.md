# pinterest-data-pipeline912

**Pinterest Data Processing with Kafka and AWS RDS**  
A project that focuses on processing Pinterest data, using Kafka to stream various data types (posts, geolocation, and user data), and storing the data in AWS RDS for further analysis.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Installation Instructions](#installation-instructions)
3. [Usage Instructions](#usage-instructions)
4. [File Structure](#file-structure)
5. [License](#license)

---

## Project Overview

### What it does:
This project involves setting up a **Kafka** producer to stream Pinterest data, including **posts**, **geolocation**, and **user** data, and using **AWS RDS** for persistent storage. The data streams are ingested using Kafka topics, which are then processed and stored in an RDS database for further analysis.

### Aim of the project:
- To understand the basics of stream processing with Kafka.
- To set up **Kafka topics** for different types of data (posts, geolocation, user).
- To connect to **AWS RDS** and perform SQL operations to retrieve and process data.
- To work with **AWS MSK** (Managed Streaming for Apache Kafka) for Kafka deployment.

### What I learned:
- Setting up Kafka with AWS MSK for managed Kafka services.
- Working with **Kafka topics** to manage different types of data.
- Integrating **Python** with **SQLAlchemy** to interact with a MySQL database.
- Using **AWS services** to deploy and manage infrastructure for the project.
- Managing data streams with Kafka, simulating the processing of Pinterest data.

---

## Installation Instructions

To run this project locally, follow these steps:

### 1. **Install Kafka and Zookeeper:**
   You must have **Kafka** and **Zookeeper** running locally or use **AWS MSK** for a managed Kafka cluster.
   - Follow [this guide](https://kafka.apache.org/quickstart) to install Kafka on your local machine.
   - Alternatively, use the **Zookeeper** connection string from **AWS MSK** if using managed Kafka.

### 2. **Install Dependencies:**
   You will need Python and some libraries for interacting with the database and Kafka.

   - Install **Python** (if not already installed): [Download Python](https://www.python.org/downloads/)
   - Install the required Python libraries:
     ```bash
     pip install kafka-python sqlalchemy pymysql requests boto3
     ```

### 3. **Set Up AWS RDS:**
   Ensure you have an **AWS RDS MySQL** instance running, with tables for `pinterest_data`, `geolocation_data`, and `user_data`.
   - Update the connection details in the Python script as per your RDS credentials.

### 4. **Configure Zookeeper and Kafka:**
   If you're using AWS MSK, you'll need the **Zookeeper** connection string and **Kafka bootstrap server** string from the AWS MSK Console.

---

## Usage Instructions

### Running Kafka Topics:

To create Kafka topics for the project, use the following commands:

1. **Pinterest Posts Data topic:**
   ```bash
   ./kafka-topics.sh --create \
    <zookeeper file text>
     --replication-factor 3 \
     --partitions 1 \
     --topic <topic_name>.pin
    ```

2. **Pinterest Posts geo topic:**
    ```bash
    ./kafka-topics.sh --create \
    <zookeeper file text>
    --replication-factor 3 \
    --partitions 1 \
    --topic <topic_name>.geo
    ```

3. **Pinterest Posts User topic:**
    ```bash
    ./kafka-topics.sh --create \
    <zookeeper file text>
    --replication-factor 3 \
    --partitions 1 \
    --topic <topic_name>.user
    ```
