# Distributed Web Infrastructure

![Diagram](https://imgur.com/a/Y7jvOWP.png)

## Explanation

### Why Each Element Is Added

- Load Balancer (HAProxy): Distributes incoming traffic across multiple servers to prevent overload and ensure availability.
- 2 Web Servers (Nginx): Serve static content and forward dynamic requests to the application servers.
- 2 Application Servers: Run the backend logic to handle requests and respond with processed data.
- 2 Sets of Application Files: Ensures each server is self-contained and can serve independently.
- 2 MySQL Databases: Used in a Primary-Replica configuration for redundancy and scalability.



## Load Balancer Configuration

- Distribution Algorithm: `Round-robin` — it sends incoming requests to each backend server in turn, balancing the load evenly.
- Setup Type: `Active-Active` — both servers handle traffic simultaneously.
  - In Active-Active, all servers are online and process requests at the same time.
  - In Active-Passive, one server handles traffic while the other remains on standby in case of failure.



## Primary-Replica Database Setup

- In a Primary-Replica (also known as Master-Slave) setup:
  - The Primary (master) handles **write** operations (INSERT, UPDATE, DELETE).
  - The Replica (slave) handles **read-only** operations and replicates the primary’s data.
- This setup improves performance and availability. Read traffic can be distributed, and the replica can take over if the primary fails (with additional logic or tools).



## Issues with This Infrastructure

- SPOF (Single Point of Failure):
  - The load balancer itself is a SPOF. If it fails, access to all servers is lost.
- Security Issues:
  - No firewall to protect against unauthorized access.
  - No HTTPS, meaning data transfer is not encrypted.
- Lack of Monitoring:
  - No systems are in place to detect failures, track server load, or notify admins.



## Summary

This setup improves availability, scalability, and performance compared to a single server, but introduces complexity and requires further security and monitoring layers to be production-ready.
