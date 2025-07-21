# Scale Up Infrastructure

![Diagram](https://imgur.com/WJ7lrKL.png)

## Explanation

### Why Each New Element Is Added

- 1 additional server: This helps distribute load, increase redundancy, and reduce single points of failure. It allows you to offload specific components (like database or application logic) to their own machine.
- 1 new load balancer configured as a cluster with the existing one: Load balancers are now in an active-active or active-passive cluster to eliminate the single point of failure from having just one. This ensures that if one load balancer fails, the other takes over.
- Split components across their own dedicated servers:
  - Web Server: Now runs on its own dedicated machine. This allows it to handle static files and HTTP requests without being impacted by backend processes.
  - Application Server: Moved to a separate server to isolate business logic and dynamic processing from other services.
  - Database Server: Now resides on its own machine to improve performance and reliability. This avoids resource contention with the web and app servers.

### Application Server vs Web Server

- Web Server:
  - Handles HTTP requests from clients (like browsers).
  - Serves static files such as HTML, CSS, images, and JavaScript.
  - Example: Nginx.

- Application Server:
  - Processes dynamic content and runs backend application logic.
  - Handles requests passed from the web server and returns responses (like database queries, computations, user actions).
  - Examples: Gunicorn (for Python apps), Node.js, PHP-FPM.

Separating the application server from the web server allows each to be optimized for their specific tasks, improves scalability, and makes the infrastructure easier to maintain.

### Summary

This scaled-up infrastructure is more robust and production-ready. It adds redundancy through load balancer clustering, improves performance by isolating services, and makes scaling individual components much easier.

