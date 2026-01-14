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
- API Overload
 Too many requests at once slow down servers or cause downtime.
- Misuse or Attacks
 Bots or malicious users may spam APIs, leading to failures.
- Unfair Usage
 Some users may overuse free plans unless limits are enforced.
- Cost Increase
 High API usage increases cloud billing unexpectedly.
- Distributed System Complexity
 When apps run on multiple servers, enforcing consistent rate limits becomes difficult.

## OBJECTIVES
The key goals of our system are:
- To build a fast and reliable rate limiting engine.
- To support multiple strategies like Token Bucket, Sliding Window, and Fixed Window.
- To offer an admin dashboard with real-time monitoring.
- To ensure consistent rate limits across distributed servers.
- To make configuration easy for developers and organizations.

## WORKFLOW OF THE SYSTEM
The workflow of the Distributed Rate Limiter System is simple, smooth, and close to how
modern API gateways work:
- Incoming Request : A user sends a request to an application (e.g., login, fetch items, etc.).
- Application Calls Rate Limiter : Before processing the request, the main application sends the user’s key/IP to our Rate Limiter Service through an API call.
- Check Rate Limits (Core Logic) The Rate Limiter checks:
       - How many requests the user has already made.
       - Whether the user exceeds the limit.
       - What algorithm is applied (Token Bucket, Sliding Window, etc.).
- Redis-Based Decision : Since this is a Distributed system, Redis stores counters/tokens centrally:
       - Redis increments counters
       - Redis checks expiration
       - Redis ensures correct limits across all servers
- Allow or Deny Based on Redis results:
       - If within limit → system returns **ALLOW**
       - If exceeded → system returns **DENY**
- Application Processes or Blocks : 
       - If allowed → request reaches the main service (like ordering food or viewing items).
       - If denied → user gets a "Too Many Requests" message.
- Logging and Analytics Every decision is logged for:
       - Monitoring
       - Charts
       - Alerts
       - Usage reports
- Dashboard Display Admins can view:
       - Live traffic
       - Violations
       - High-load endpoints
       - API keys
       - Custom limit configurations
This workflow ensures system stability without slowing down applications.
