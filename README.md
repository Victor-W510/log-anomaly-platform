

#  Log Anomaly Detection Platform
 
> A distributed end-to-end log anomaly detection system built with Spring Boot and a Python-based ML service. It simulates log generation, processes incoming data, and uses machine learning to detect anomalies in system behavior. The entire system is containerized with Docker for easy setup and scalability.


---

- **Log Collector Service (Spring Boot)**
  - Generates logs
  - Stores logs in MySQL
  - Simulates normal & anomalous behavior
- **ML Service (Python)**
  - Reads logs from database
  - Performs feature engineering
  - Runs anomaly detection model
  - Sends alerts to Discord
- **Database**
  - MySQL for persistent storage
- **Infrastructure**
  - Docker + Docker Compose

---
 
##  Getting Started
 
### 1. Clone repositories
 
```bash
mkdir log-anomaly
cd log-anomaly
 
git clone https://github.com/Victor-W510/log-anomaly-ml-service.git
git clone https://github.com/Victor-W510/log-anomaly-collector.git
git clone https://github.com/Victor-W510/log-anomaly-platform.git
```
 
### 2. Configure Docker
 
Update `docker-compose.yml`:
- MySQL password
- Database name
---
 
### 3. Alerts (Discord Integration)
 
**Setup**
1. Create a Discord server
2. Go to **Server Settings → Integrations → Webhooks**
3. Create a webhook and copy the URL
**Configuration**

 
---
 
### 4. Configure environment variables
 
Copy `.env.example` → `.env` in each service:
 
**ML Service:**
```env
DISCORD_WEBHOOK_URL=your_webhook
DB_HOST=mysql
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=your_db
```

> [!NOTE]
> Add the webhook URL in your `.env` file in the ML service:
```env
DISCORD_WEBHOOK_URL=your_webhook_url
```
 
**Collector Service:**
```env
DB_URL=jdbc:mysql://mysql:3306/your_db
DB_USERNAME=root
DB_PASSWORD=your_password
```
 
---
 
### 5. Build collector service
 
```bash
cd log-anomaly-collector
./gradlew build
```
 
### 6. Start with Docker Compose
 
```bash
cd ../log-anomaly-platform
docker compose up --build
```
 
**Detached mode:**
```bash
docker compose up -d --build
```
 
**Stop:**
```bash
docker compose down
```
 
---
<img width="1808" height="576" alt="BYNBv" src="https://github.com/user-attachments/assets/589e8f80-ccc5-4cb7-aad6-28511e9682d5" />

 
##  Tech Stack
 
**Backend**
- Java 21
- Spring Boot
- Gradle
**ML**
- Python
- Pandas
- NumPy
- Scikit-learn
**Infra**
- Docker
- Docker Compose
- MySQL

---

## Learning Goals

This project was built to gain hands-on experience with designing and implementing an end-to-end system for log generation, processing, and anomaly detection.

Key focus areas include:

- Designing a distributed system with multiple services (Spring Boot backend, ML service, and database)
- Building a machine learning pipeline for anomaly detection on log data
- Working with real-time log simulation and data ingestion
- Applying feature engineering techniques to transform raw log data into model-ready inputs
- Using containerization with Docker and Docker Compose to orchestrate the full system
- Exploring basic observability concepts through structured logging and data flow tracking

---
 
## 📄 License
 
This project is for educational purposes.


