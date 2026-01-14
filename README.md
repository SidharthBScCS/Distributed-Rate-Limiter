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
