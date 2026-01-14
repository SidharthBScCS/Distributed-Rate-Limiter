# Distributed-Rate-Limiter

## INTRODUCTION
In today’s digital world, almost every service we use—shopping apps, banking, streaming,
travel, or even simple login systems—relies on APIs. These APIs sometimes receive
unpredictable traffic. For example, during a sale, thousands of users may hit an endpoint at
the same moment. If the system cannot handle this load, it may crash.
To prevent such sudden overload or misuse, the industry uses a mechanism called Rate
Limiting. It decides how many requests are allowed within a specific time. Our project, the
Distributed Rate Limiter System, acts as a smart traffic controller that ensures APIs remain
fast, secure, and fair for everyone.
This system is designed to reduce server crashes, protect against abuse, and ensure stable
performance—even when millions of users are accessing the app.

## PROBLEM STATEMENT
Here are the major problems the system addresses:
- **API Overload**
 Too many requests at once slow down servers or cause downtime.
- **Misuse or Attacks**
 Bots or malicious users may spam APIs, leading to failures.
- **Unfair Usage**
 Some users may overuse free plans unless limits are enforced.
- **Cost Increase**
 High API usage increases cloud billing unexpectedly.
- **Distributed System Complexity**
 When apps run on multiple servers, enforcing consistent rate limits becomes difficult.

## OBJECTIVES
The key goals of our system are:
- To build a fast and reliable rate limiting engine.
- To support multiple strategies like Token Bucket, Sliding Window, and Fixed Window.
- To offer an admin dashboard with real-time monitoring.
- To ensure consistent rate limits across distributed servers.
- To make configuration easy for developers and organizations.

## WORKFLOW OF THE SYSTEM

The workflow of the **Distributed Rate Limiter System** is simple, efficient, and closely aligned with how modern API gateways operate.

- **Incoming Request**  
  A client sends a request to an application (e.g., login, fetch items, place an order).

- **Application Calls Rate Limiter**  
  Before processing the request, the main application sends the client’s **API key / IP address** to the Rate Limiter Service via an internal API call.

- **Check Rate Limits (Core Logic)**  
  The Rate Limiter evaluates the request by checking:
  - Number of requests already made by the client  
  - Whether the request exceeds the configured limit  
  - Which rate limiting algorithm is applied  
    *(Token Bucket, Sliding Window, Fixed Window, etc.)*

- **Redis-Based Decision**  
  Since the system is distributed, Redis is used as a centralized store to maintain consistency:
  - Redis increments counters or tokens atomically  
  - Redis manages key expiration using TTL  
  - Redis ensures consistent limits across all servers  

- **Allow or Deny Decision**  
  Based on the Redis evaluation:
  - **ALLOW** → Request is within the allowed limit  
  - **DENY** → Rate limit exceeded  

- **Application Processes or Blocks Request**  
  - If allowed → Request is forwarded to the main service  
  - If denied → Client receives `HTTP 429 (Too Many Requests)`  

- **Logging and Analytics**  
  Every decision is logged for:
  - Monitoring and metrics  
  - Traffic analysis  
  - Alerts  
  - Usage reports  

- **Dashboard Display**  
  Administrators can monitor:
  - Live request traffic  
  - Rate limit violations  
  - High-load endpoints  
  - API key / IP usage  
  - Configured rate limit rules  

This workflow ensures **system stability**, **fair usage**, and **high performance** without introducing significant latency.

## SCOPE OF THE PROJECT
**The project covers:**
- Distributed rate limiting algorithms
- Centralized rule configuration
- Live monitoring dashboard
- API-based integration
- Logging and analytics
**Areas not covered:**
- Full authentication system
- Payment or subscription management
- AI-based anomaly detection (future extension)
**TECHNOLOGY STACK**
- Java 17 / Spring Boot
- Redis for distributed counters
- PostgreSQL for configurations
- HTML/CSS/JS + Thymeleaf for dashboard
- Docker for deployment
- Prometheus + Grafana for monitoring 
