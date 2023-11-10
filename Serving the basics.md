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
- The PostgreSQL is very versatile, but with versatility comes complexity.
### The MySQL Server
- This server started out as a project to create a simple but fast database system. It just offers basic features that performed quickly.
- Because of its focus on speed, the MySQL database server become the de facto database server used in many high-profile internet web applications.
- The combination of a Linux server running the Apache web server and the MySQL database server and utilizing the PHP programming language become knowb as the LAMP platform and can be found in Linux servers all over the world.
- The MySQL database has added features that canrival those found in PostgreSQL and commercial databases.
- The MySQL project was acquired by Sun Microsystems, who was then acquired by Oracle.
### The MangoDB Server
- One of the most popular object-oriented method of storing data is called NoSQL
- NoSQL database doesn't create tables but instead stores data as individual documents. Each NoSQL document can contain different data elements, with each data element being independent from the other data elements in the database.
- MangoDB was released in 2009 as a full NoSQL compliant database management system. It stores data records as individual JavaScript Object Notation (JSON) elements, making each data document independent of others.
- The MongoDB database server supports many relational database features, such as indexes, queries, replication, and even load balancing.
- The MongoDB server installs with a default of no security, be careful when using a MongoDB database for the web applications.
## Mail Servers
- Instead of having one monolithic program that handles all of the pieces required for sending and receiving mail, Linux uses multiple small programs that work together in the processing of email messages.
- Linux email server is normally divided into three separate functions:
 1. The mail transfer agent (MTA)
 2. The mail delivery agent (MDA)
 3. The mail user agent (MUA)
### Mail User Agent (MUA)
- MUA is the program that interacts with end users, allowing them to view and manipulate email messages.
- MUA programs don't usually run on the server side but rather on the client side.
- Graphical applications such as Evolution and K-Mail are popular for reading email in Linux desktop environments. The MTA and MDA functions are found on the Linux server.
### Mail Transfer Agent (MTA)
- The mail transfer agent (MTA) is responsible for handling both incoming and outgoing email messages on the server.
- For each outgoing message, The MTA determines the destination host of the recipient address. If the destination host is a remote mail server, the MTA must establish a communication link with another MTA program on the remote host to transfer the message.
- Here are a few MTA software packages for the Linux environment:
1. sendmail: The sendmail MTA package has many features such as virtual domains, message forwarding, user aliases, mail lists, and host masquerading.
    - Unfortunately, sendmail is very complex to configure correctly. Its large configuration file is sometimes overwhelming for novice mail administrators to handle.
2. Postfix: The Postfix MTA was written as a modular application, using serveral different programs to implement the MTA functionality.
    - One of Postfix's best features is its simplicity, instead of one large complex configuration file, it uses just two small configuration files with plaintext parameters and value names to define the functionality.
3. Exim: The Exim MTA package sticks with the sendmail model of using one large program to handle all the email functions. It attempts to avoid queuing messages as much as possible, instead relying on immediate delivery in most environments.
### The Mail Delivery Agent
- Linux relys on a separate stand alone mail delivery agent (MDA) programs to deliver messages to local users. Because these MDA programs concentrate only on delivering messages to local users, they can add functionality.
- The MDA program receives messages destined for local users from the MTA program and then determines how those messages are to be delivered. Messages can be delivered directly to the local user account or to an alternate location defined by the user, often by incorporating filters.
- There are two common MDA programs used in Linux:
    - Binmail: The binmail program is the most popular MDA program used in Linux. Its name comes from its normal location in the system, /bin/mail. Its popular due to its simplicity, and by default it can read email messages stored in the standard /var/spool/mail directory, or it can be an alternative mailbox.
    - Procmail: The procmail program is popular due to its versatility in creating user-configured recipes that allow a user to direct how the server processes received mail.  
