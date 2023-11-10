# Serving the Basics
- There are some basic internet services that Linux servers are known to do well and that have become standards across the internet. The three internet services Linux servers provide are as follows:
-   1. Web services
    2. Database services
    3. Email services
- The following section discusses each of thes types of Linux services and how to open source software packages.
## Web Servers  
- The most popular use of Linux servers on the internet is as a web server. The Linux-based web servers host the majority of websites.
- There are multiple programs that you can use to build a Linux web server. These are the most popular ones you'll run into and should know about.
### The Apache Server 
- The Apache web server has become one of the most popular web servers on the internet. It was developed from the first web server software package created by the National Center for Supercomputing Applications (NCSA) at the University of Illinois.
- The Apache web server has become popular due to its modularity. Each advanced feature of the server is built as a plug in module.
- When features are incorporated as modules, the server administrator can pick and choose just which modules a particular server needs for a particular application.
- This helps reduce the amount of memory required to run the Apache server daemons on the system.
### The nginX Server
- The nginX web server was relased in 2004 and designed as an advanced replacement for the Apache web server.
- It has improved performance and provides some additional features, such as working as a web proxy, mail proxy, web page cache, and even load-balancing server.
- The core nginX program has a smaller memory footprint than the larger Apache program, making it ideal for high-volume environments. It's capable of handling over 10,000 simultaneous network client connections.
- One configuration that's becoming popular is to use a combination of the nginX web server as a load-balancing front end to multiple Apache web servers on the backend.
### The lighthttpd Package
- The lighthttpd package provides a lightweight web server to process incoming client requests for a network application.
- The lighthttpd web server is known for low memory usage and low CPU usage, making it ideal for smaller server applications, such as in embedded system.
- It also incorporates a built-in database, allowing for the combination of basic web and database services in a single package.
## Database Servers
- Storing and retrieving data is an important feature for most applications.
- The advent of the relational database allowed applications to quickly store and retrieve data.
- Relational database servers allowed multiple clients to access the same data from a centralized location.
- The structured Query Language (SQL) provides a common method for clients to send requests to the database server and retrieve the data.
- The following sections discuss the three most popular open source database servers you'll encounter when working in the Linux environment.
### The PostgreSQL Server
- The PostgreSQL Server was implemented as a complete object-relational database management system to rival the popular commercial database servers.
- PostgreSQL is known for its advanced database features. It follows the standard atomicity, consistency, isolation, and durability (ACID) guidelines used by commercial databases and supports many of the fancy features you would expect to find in commercial relational database server.
- Such as transactions, updatable views, triggers, foreign keys, functions, and stored procedures.
- The PostgreSQL is very versatile, but with 
