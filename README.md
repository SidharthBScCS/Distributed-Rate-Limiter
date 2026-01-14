# Distributed Rate Limiter

A scalable and distributed rate limiting system designed to protect APIs from overload, abuse, and unfair usage while ensuring consistent performance across multiple servers.

---

## Introduction

In today’s digital world, almost every service we use—shopping platforms, banking apps, streaming services, travel portals, or even simple login systems—relies heavily on APIs. These APIs often experience unpredictable traffic patterns. For example, during flash sales or peak hours, thousands of users may hit the same endpoint simultaneously.

If a system is not prepared to handle such traffic spikes, it can lead to performance degradation or complete downtime.

To prevent this, modern systems use **Rate Limiting**—a mechanism that controls how many requests a client can make within a specific time window.  
The **Distributed Rate Limiter System** acts as a smart traffic controller that ensures APIs remain **fast, secure, and fair**, even under heavy load.

This system is designed to:
- Prevent server crashes  
- Protect against misuse and abuse  
- Maintain stable performance in high-traffic environments  

---

## Problem Statement

The system addresses the following challenges:

- **API Overload**  
  Excessive concurrent requests can slow down servers or cause downtime.

- **Misuse or Attacks**  
  Bots or malicious clients may spam APIs, leading to service disruption.

- **Unfair Usage**  
  Without limits, some users may consume disproportionate resources.

- **Cost Increase**  
  High API usage can unexpectedly increase cloud infrastructure costs.

- **Distributed System Complexity**  
  Enforcing consistent rate limits across multiple servers is difficult without a centralized mechanism.

---

##  Objectives

The key objectives of this project are:

- Build a fast and reliable rate limiting engine  
- Support multiple rate limiting strategies:
  - Token Bucket  
  - Sliding Window  
  - Fixed Window  
- Ensure consistent rate limits across distributed servers  
- Provide an admin dashboard for real-time monitoring  
- Make configuration simple and developer-friendly  

---

## Workflow of the System

The **Distributed Rate Limiter System** follows a workflow similar to modern API gateways.

- **Incoming Request**  
  A client sends a request to an application (e.g., login, fetch data, place an order).

- **Application Calls Rate Limiter**  
  Before processing the request, the application sends the client’s **API key / IP address** to the Rate Limiter Service.

- **Check Rate Limits (Core Logic)**  
  The Rate Limiter evaluates:
  - Number of requests already made by the client  
  - Whether the configured limit is exceeded  
  - Which algorithm is applied  
    *(Token Bucket, Sliding Window, Fixed Window, etc.)*

- **Redis-Based Decision**  
  Redis is used as a centralized store to maintain consistency:
  - Atomic counter/token updates  
  - Key expiration using TTL  
  - Shared state across distributed servers  

- **Allow or Deny Decision**  
  - **ALLOW** → Request is within the limit  
  - **DENY** → Rate limit exceeded  

- **Application Processes or Blocks Request**  
  - Allowed → Request reaches the main service  
  - Denied → Client receives `HTTP 429 (Too Many Requests)`  

- **Logging and Analytics**  
  Every request decision is logged for:
  - Monitoring  
  - Traffic analysis  
  - Alerts  
  - Usage reports  

- **Dashboard Display**  
  Administrators can view:
  - Live traffic  
  - Rate limit violations  
  - High-load endpoints  
  - API key / IP usage  
  - Configured rate limit rules  

This workflow ensures **system stability**, **fair usage**, and **high performance** with minimal latency.

---

## Scope of the Project

### Covered
- Distributed rate limiting algorithms  
- Centralized rule configuration  
- Admin monitoring dashboard  
- API-based integration  
- Logging and analytics  

### Not Covered
- Full authentication system  
- Payment or subscription management  
- AI-based anomaly detection *(future extension)*  

---

## Technology Stack

- **Backend:** Java 17, Spring Boot  
- **Distributed Store:** Redis  
- **Configuration Storage:** PostgreSQL  
- **Frontend:** HTML, CSS, JavaScript, Thymeleaf  
- **Deployment:** Docker  
- **Monitoring:** Prometheus, Grafana  

---

## Conclusion

The **Distributed Rate Limiter System** is a modern, production-oriented solution built for today’s high-traffic applications. It effectively protects APIs from overload, enforces fair usage, and ensures consistent performance across distributed environments.

With its clean architecture, Redis-backed consistency, and monitoring dashboard, this project demonstrates strong **backend engineering** and **distributed systems** fundamentals—making it not just an academic project, but an industry-relevant solution.

---
