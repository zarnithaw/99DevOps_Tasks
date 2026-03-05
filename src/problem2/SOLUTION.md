
![HA Architecture](HA%20Diagram%20on%20AWS.jpg)


## Overview

The system is designed on AWS to support **500 requests per second** with **p99 latency under 100ms**, while remaining highly available and scalable.

## Key Components

### 1. Application Load Balancer (ALB)

Distributes traffic across multiple Availability Zones and performs health checks to ensure high availability.

**Alternative –** API Gateway

---

### 2. EC2 Auto Scaling Groups

Auto Scaling allows horizontal scaling and automatic replacement of failed instances.

**Alternative –** Amazon ECS

---

### 3. Redis (ElastiCache)

Used for frequently accessed data in memory to reduce database load and achieve low latency.

**Alternative –** Amazon ElastiCache for Memcached

---

### 4. Aurora PostgreSQL (Multi-AZ)

Stores users, orders, and trades. Provides automatic failover and high availability.

**Alternative –** Amazon RDS for PostgreSQL

---

### 5. NAT Gateway (per AZ)

Allows private instances to access the internet securely.

**Alternative –** NAT Instance

---

### 6. Internet Gateway

Allows external users to access the application hosted inside the VPC.

**Alternative –** Amazon CloudFront



## How the Architecture Scales

### 1. Scale the Web Tier (EC2 Auto Scaling)

When traffic increases:

- AWS automatically launches more EC2 instances
- The load balancer distributes traffic to them

---

### 2. Scale the Application Tier

If more trading requests arrive:

- New EC2 instances are added
- Processing load is distributed

---

### 3. Scale the Database

For higher traffic:

- Add Read Replicas
