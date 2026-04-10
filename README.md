# db-in-a-box

# 🐳 Lab 24: Docker and Databases - Running a MySQL Container

## 📌 Overview

This repository demonstrates how to deploy and manage a MySQL database using Docker. It covers containerization, networking, data persistence, backup/restore strategies, and client-server interaction.

This lab is designed for DevOps engineers and students learning containerized database management.

---

## 🎯 Objectives

By completing this lab, you will:

* Pull and run a MySQL Docker image
* Configure MySQL container with custom networking
* Initialize database with custom schema
* Implement persistent storage using Docker volumes
* Perform backup and restore operations
* Connect using MySQL client container
* Apply best practices for containerized databases

---

## 🧰 Prerequisites

Before starting, ensure you have:

* Basic knowledge of Docker (containers, images, volumes)
* Familiarity with Linux CLI
* Basic understanding of SQL
* Networking fundamentals

---

## ⚙️ Lab Setup

The lab environment includes:

* Docker Engine (latest)
* Docker Compose
* Linux environment (Al Nafi cloud machine)
* Text editors (nano/vim)

---

## 🚀 Steps Performed

### 🔹 1. MySQL Container Deployment

* Pulled official MySQL image
* Ran container with environment variables
* Verified container logs and status

---

### 🔹 2. Custom Docker Networking

* Created isolated Docker network
* Attached MySQL container to custom network
* Verified network connectivity

---

### 🔹 3. Database Initialization

* Created SQL schema:

  * `employees` table
  * `departments` table
  * `employee_summary` view
* Inserted sample data
* Executed schema inside container

---

### 🔹 4. Data Persistence (Volumes)

* Mounted host directory to container
* Ensured data survives container restart
* Tested persistence by recreating container

---

### 🔹 5. Backup & Restore

* Created full and partial backups using `mysqldump`
* Stored backups in host directory
* Restored database in a new container
* Verified restored data integrity

---

### 🔹 6. MySQL Client Container

* Connected to database using client container
* Executed SQL queries
* Tested user permissions

---

### 🔹 7. Monitoring Script

* Created Bash script to monitor:

  * Container status
  * Active connections
  * Database size
  * Table row counts

---

## 📂 Project Structure

```
mysql-lab/
│
├── sql-scripts/
│   └── init-schema.sql
│
├── mysql-data/
│
├── backups/
│
└── monitor-db.sh
```

---

## 🛠️ Key Commands

### Run MySQL Container

```bash
docker run --name mysql-server \
  -e MYSQL_ROOT_PASSWORD=SecurePass123 \
  -d mysql:8.0
```

### Backup Database

```bash
docker exec mysql-container mysqldump -u root -p database > backup.sql
```

### Restore Database

```bash
docker exec -i mysql-container mysql -u root -p database < backup.sql
```

---

## ⚠️ Troubleshooting

### Container Not Starting

* Check logs:

```bash
docker logs <container>
```

### Port Conflict

```bash
netstat -tlnp | grep 3306
```

### Permission Issues

```bash
sudo chown -R 999:999 ~/mysql-lab/mysql-data/
```

---

## 🔐 Best Practices

* Use Docker volumes for persistent data
* Never hardcode passwords in production
* Use environment variables or secrets
* Enable backups regularly
* Isolate containers using custom networks
* Monitor database health

---

## 📊 Why This Lab Matters

This lab teaches real-world DevOps skills:

* Containerized database deployment
* Data persistence strategies
* Disaster recovery planning
* Secure and scalable architecture

---

## 🔮 Future Improvements

* Use Docker Compose for multi-container setup
* Implement MySQL replication
* Deploy on Kubernetes (StatefulSets)
* Add monitoring tools (Prometheus, Grafana)

---

## 🧹 Cleanup

```bash
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
docker network rm mysql-network
```

---

## 🙌 Conclusion

This lab provides hands-on experience with running and managing MySQL in Docker, covering deployment, persistence, backup, and monitoring — essential skills for modern DevOps engineers.

---

## 👨‍💻 Author

**Zohaib Ahmed**
DevOps & Cloud Enthusiast 🚀

---
