# Real-Time Ad Streaming with Kafka, Spark, and Confluent Cloud

This project demonstrates a **real-time data streaming pipeline** using:
- **Kafka (Confluent Cloud)** for event streaming  
- **Avro Schema Registry** for message serialization/deserialization  
- **Producer** that publishes ad events from a CSV file  
- **Consumer** that reads and deserializes Kafka events  
- **Apache Spark Structured Streaming** that processes events in real-time  

---

## 🚀 Project Overview

The pipeline consists of three main components:

1. **Producer (`producer.py`)**  
   - Reads **`mock_data.csv`**  
   - Serializes records using **Avro schema** from **Confluent Schema Registry**  
   - Publishes messages to **Kafka topic (`ad_topic`)**

2. **Consumer (`consumer.py`)**  
   - Subscribes to **Kafka topic (`ad_topic`)**  
   - Uses **Avro deserializer** to read and print consumed messages  

3. **Spark Stream Processor (`stream_ads.py`)**  
   - Reads messages from **Kafka in real-time**  
   - Decodes **Avro-encoded messages** using **Schema Registry**  
   - Outputs data to the **console** (can be extended to DB, dashboard, etc.)  

---

## 🛠️ Project Structure

- **producer.py** → Kafka producer publishing events from CSV  
- **consumer.py** → Kafka consumer reading Avro messages  
- **stream_ads.py** → Spark Structured Streaming job  
- **mock_data.csv** → Sample dataset  
- **mock_data_schema.json** → Avro schema for ad events  
- **requirements.txt** → Python dependencies  
- **README.md** → Project documentation  

---

## ⚙️ Setup & Installation

### **1. Clone the repository**
```bash
git clone https://github.com/jgarij/spark-ad-streaming.git

cd spark-ad-streaming

### 2. Install Dependencies
```bash
pip install -r requirements.txt

3. Configure Environment Variables
Create a .env file in the root directory and add the following:

confluent_kafka_id=your_kafka_api_key
confluent_kafka_secret_key=your_kafka_api_secret
confluence_schema_id=your_schema_registry_key
confluence_schema_secret=your_schema_registry_secret

▶️ Running the Project
Run Producer
python producer.py

Run Consumer
python consumer.py

Run Spark Streaming Job

Submit with Spark (make sure Spark is installed and configured):

spark-submit --packages org.apache.spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.3.0,org.apache.spark:spark-avro_2.12:3.5.0 stream_ads.py
