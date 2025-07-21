# Secured and monitored web infrastructure

![Diagram](https://imgur.com/SOHmEUP.png)

## Explanation

### Why Each Additional Element Is Added

- 3 Firewalls: One between the internet and the load balancer, and one in front of each application server. They protect against unauthorized access by filtering incoming and outgoing traffic based on rules.
- SSL Certificate (HTTPS): Encrypts the data transmitted between users and the server, ensuring confidentiality and preventing tampering or interception.
- 3 Monitoring Clients: Installed on each server to collect performance and health data (e.g., using Sumologic, Prometheus, Nagios). This enables real-time monitoring and alerting.

### What Are Firewalls For?

Firewalls are network security systems that monitor and control incoming and outgoing traffic based on rules.  
They protect servers from malicious traffic and unauthorized access, acting as a barrier between trusted and untrusted networks.

### Why Is the Traffic Served Over HTTPS?

HTTPS uses SSL/TLS to encrypt communication between the user and the server.  
It protects data integrity, user privacy, and ensures that the client is communicating with the legitimate server.  
Without HTTPS, sensitive data like passwords and personal info can be intercepted.

### What Is Monitoring Used For?

Monitoring ensures that all infrastructure components are working correctly.  
It helps detect failures, track performance, and respond quickly to incidents.  
It also supports capacity planning and identifying system bottlenecks.

### How the Monitoring Tool Collects Data

Monitoring agents are installed on each server.  
These agents collect metrics like CPU usage, memory, disk I/O, QPS, and latency.  
The data is sent to a central monitoring system (like Sumologic or Prometheus) for analysis and alerting.

### How to Monitor Web Server QPS (Queries Per Second)

Enable access logs in Nginx.  
Use tools like GoAccess, Grafana with Prometheus, or Sumologic to analyze the logs and calculate QPS.  
You can also configure alerts to notify you if QPS exceeds a set threshold.

---

## Issues with This Infrastructure

### SSL Termination at the Load Balancer

SSL termination means that traffic between the load balancer and backend servers is no longer encrypted.  
If someone gains access to the internal network, they can intercept that unencrypted data.  
To prevent this, use end-to-end encryption, re-encrypting traffic from the load balancer to the backend servers.

### Single MySQL Writer

If only one MySQL server handles write operations and it goes down, all write functionality is lost.  
This creates a single point of failure.  
Solutions include automated failover or multi-primary setups, depending on consistency needs.

### Identical Servers (Web, App, DB on the same machine)

Running all components on the same server causes resource competition.  
It also makes scaling difficult because each role can't be independently optimized.  
Best practice is to separate concerns by distributing services across different servers.

---

## Summary

This setup introduces basic layers of security, monitoring, and encrypted traffic, which are important for any production-level system.  
However, it still contains design flaws and limitations that should be addressed before considering it fully reliable and scalable.


