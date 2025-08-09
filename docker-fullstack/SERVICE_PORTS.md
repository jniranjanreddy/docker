# 🌐 Complete Service Port Map

Here's a comprehensive list of all services running in your infrastructure and their ports:

## 📊 **Monitoring & Observability Stack**

| Service | Port | URL | Purpose |
|---------|------|-----|---------|
| **Grafana** | 3000 | http://localhost:3000 | 📈 Dashboards & Visualization |
| **Prometheus** | 9090 | http://localhost:9090 | 📊 Metrics Collection |
| **Alertmanager** | 9093 | http://localhost:9093 | 🚨 Alert Management |
| **Loki** | 3100 | http://localhost:3100 | 📝 Log Aggregation |
| **Node Exporter** | 9100 | http://localhost:9100 | 💻 System Metrics |
| **Blackbox Exporter** | 9115 | http://localhost:9115 | 🔍 Endpoint Monitoring |
| **cAdvisor** | 8081 | http://localhost:8081 | 🐳 Container Metrics |

## 📋 **ELK Stack (Log Analytics)**

| Service | Port | URL | Purpose |
|---------|------|-----|---------|
| **Kibana** | 5601 | http://localhost:5601 | 🔍 Log Visualization |
| **Elasticsearch** | 9200 | http://localhost:9200 | 🗃️ Search & Analytics |
| **Elasticsearch (Transport)** | 9300 | - | 🔗 Internal Communication |
| **Logstash** | 5044 | - | 📥 Log Processing (Beats) |
| **Logstash** | 5000 | - | 📥 Log Processing (TCP/UDP) |
| **Logstash** | 9600 | - | 📊 Logstash Monitoring |

## 🔍 **Distributed Tracing**

| Service | Port | URL | Purpose |
|---------|------|-----|---------|
| **Jaeger UI** | 16686 | http://localhost:16686 | 🕸️ Trace Visualization |
| **Jaeger Collector (HTTP)** | 14268 | - | 📡 Span Collection |
| **Jaeger Collector (gRPC)** | 14250 | - | 📡 High-perf Collection |
| **Jaeger Agent (UDP)** | 6831 | - | 📡 Agent UDP |
| **Jaeger Agent (UDP)** | 6832 | - | 📡 Agent UDP |

## 🤖 **AI/ML Platform**

| Service | Port | URL | Purpose |
|---------|------|-----|---------|
| **Jupyter Lab** | 8888 | http://localhost:8888 | 🚀 AI Development (token: ai-learning-2024) |
| **MLflow** | 5001 | http://localhost:5001 | 🧪 ML Experiment Tracking |
| **TensorBoard** | 6006 | http://localhost:6006 | 📈 Neural Network Visualization |

## 🌊 **Data Streaming (Kafka)**

| Service | Port | URL | Purpose |
|---------|------|-----|---------|
| **Kafka** | 29092 | - | 🌊 External Kafka Access |
| **Kafka (Internal)** | 9092 | - | 🔗 Internal Kafka |
| **Zookeeper** | 2181 | - | 🐘 Kafka Coordination |
| **Kafdrop** | 9000 | http://localhost:9000 | 🔍 Kafka Web UI |

## 🗄️ **Databases**

| Service | Port | URL | Purpose |
|---------|------|-----|---------|
| **PostgreSQL (Airflow)** | - | - | 🐘 Airflow Metadata |
| **PostgreSQL (App)** | 5432 | - | 🐘 Application Database |
| **MySQL** | 3306 | - | 🐬 MySQL Database |
| **MongoDB** | 27018 | - | 🍃 MongoDB Database |
| **MongoDB QA** | 27019 | - | 🍃 MongoDB QA Environment |
| **Redis** | 6379 | - | 🔴 Cache & Message Broker |

## ✈️ **Apache Airflow**

| Service | Port | URL | Purpose |
|---------|------|-----|---------|
| **Airflow Webserver** | 8080 | http://localhost:8080 | ✈️ Workflow Management (admin/admin) |
| **Flower** | 5555 | http://localhost:5555 | 🌸 Celery Task Monitor (--profile flower) |

## 📝 **Log Shipping**

| Service | Port | URL | Purpose |
|---------|------|-----|---------|
| **Promtail** | 9080 | - | 📝 Log Shipping to Loki |

## 🚀 **Quick Access URLs**

### **Main Dashboards:**
- 🎛️ **Grafana**: http://localhost:3000 (admin/admin)
- ✈️ **Airflow**: http://localhost:8080 (airflow/airflow)  
- 🚀 **Jupyter**: http://localhost:8888 (token: ai-learning-2024)
- 🧪 **MLflow**: http://localhost:5001
- 🔍 **Kibana**: http://localhost:5601

### **Monitoring:**
- 📊 **Prometheus**: http://localhost:9090
- 🚨 **Alertmanager**: http://localhost:9093
- 🕸️ **Jaeger**: http://localhost:16686
- 📈 **TensorBoard**: http://localhost:6006

### **Data Tools:**
- 🌊 **Kafdrop**: http://localhost:9000
- 💻 **cAdvisor**: http://localhost:8081

### **Development:**
- 🗃️ **Elasticsearch**: http://localhost:9200
- 📊 **Node Exporter**: http://localhost:9100

## 🔧 **Port Usage Summary**

### **Web UIs (Browser Access):**
- 3000: Grafana
- 3100: Loki  
- 5001: MLflow
- 5601: Kibana
- 6006: TensorBoard
- 8080: Airflow
- 8081: cAdvisor
- 8888: Jupyter
- 9000: Kafdrop
- 9090: Prometheus
- 9093: Alertmanager
- 16686: Jaeger

### **Database Ports:**
- 3306: MySQL
- 5432: PostgreSQL
- 6379: Redis
- 27018: MongoDB
- 27019: MongoDB QA

### **Messaging & Streaming:**
- 2181: Zookeeper
- 9092: Kafka (internal)
- 29092: Kafka (external)

### **Internal Services:**
- 5044: Logstash (Beats)
- 5000: Logstash (TCP/UDP)
- 9100: Node Exporter
- 9115: Blackbox Exporter
- 9200: Elasticsearch
- 9300: Elasticsearch Transport
- 9600: Logstash Monitoring

## 🛠️ **How to Check What's Running:**

```bash
# Check all running containers
docker-compose -f fullstack/all-in-one.yaml ps

# Check specific service logs
docker-compose -f fullstack/all-in-one.yaml logs [service-name]

# Check port usage
netstat -an | findstr ":3000"  # Windows
lsof -i :3000                  # Linux/Mac
```

## 🎯 **Beginner's Recommended Order:**

1. **Start Here**: Grafana (3000) - Overview dashboards
2. **AI Learning**: Jupyter (8888) - Start coding
3. **Data Exploration**: Kafdrop (9000) - See your data streams  
4. **Workflow Management**: Airflow (8080) - Automate tasks
5. **Experiment Tracking**: MLflow (5001) - Track AI models
6. **Advanced Monitoring**: Prometheus (9090) - Detailed metrics

Your infrastructure is now a complete data science and monitoring platform! 🚀