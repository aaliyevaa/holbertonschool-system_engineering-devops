Simple Web infrastructure 

![Diagram](https://imgur.com/squBNx9.png)

Explanation

What is a server?
A server is a physical or virtual machine that provides resources, data, services, or programs to other computers, known as clients, over a network.

What is the role of the domain name?
A domain name maps a human-readable address (e.g., foobar.com) to the IP address of the server (e.g., 8.8.8.8).

What type of DNS record is 'www' in www.foobar.com?
'www' is a subdomain, typically handled by an **A record** in DNS that maps it to an IP address.

What is the role of the web server?
The web server (Nginx) handles HTTP requests from users, serves static files (HTML, CSS, JS), and forwards requests to the application server.

What is the role of the application server?
It runs the backend application code (e.g., PHP, Python, Node.js) that processes dynamic content and business logic.

What is the role of the database?
The MySQL database stores and retrieves structured data used by the application (e.g., users, posts, transactions).

What is the server using to communicate with the user?
The server communicates with the user's computer using the HTTP/HTTPS protocol over TCP/IP. 


Issues with this Infrastructure

- SPOF (Single Point of Failure)**: If the single server goes down, the entire website becomes inaccessible.
- Downtime during maintenance**: Restarting the web server (e.g., to deploy new code) makes the site temporarily unavailable.
- Scalability: One server cannot handle high traffic loads or growth; it cannot scale horizontally.
