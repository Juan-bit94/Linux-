# Introduction to Services 
## Overview
- Linux has thrived in the server market. For IT professionals, it is important to know how linux servers work and what server software packages are popular these days.
- The popularity of Linux servers has much to do with their versatility, performance, and cost.
- This file will expand on how Linux servers operate and covers the most common server software packages that can be installed and run in Linux.
## What is a Linux server?
- Let me explain what I mean by a Linux server and show how a Linux server differes from a Linux desktop.
- The difference between a linux desktop and server is which programs they primarily run and how they run on the system.
- Linux servers primarily operate without any human interaction. There's no one sitting at a desktop launching applications.
- The server runs programs that provide shared resources (called services) to multiple users (clients), normally in a network environment.
- Many services run all the time, even when no clients are actively using them. And they seldom rely on a GUI, instead they use a Linux shell's command line interface (CLI) to interact with a server asministrator.
- Often the administrator connects to the server from a remote client to perform any work with the services. 
- Since there's little interaction with a human operator, servers must know how to launch the programs that provide the services to clients on their own. 
- How the server runs those services can differ from server to server and service to service.
## Launching Services
### There are two primary ways Linux servers rub service programs
- As a background process, running at all times and listening for requests.
- As a process spawned by a parent program that listens for the requests. 
## What are daemons?
- When a Linux service program runs continually as a background process, it's called a daemon.
- Linux servers often utilize scipts to launch service daemons as soon as the server boots up.
- Linux daemon programs often end with the letter d to indicate they're daemon processes.
- For example, a mysqld daemon program listens for network connections from clients. When the daemon receives a request from a client, it processes the request and returns data to the client via the same network channel. 
- The more services a Linux server supports, the more daemons it must have running in the background, waiting for client requests.
- Each daemon requires memory resources on the server, even when it's just listening for clients.
## What are Super-servers?
- Super-servers are programs that listen for network connections for several different applications. 
- When the super-server recives a request for a service from a client, it spawns the appropriate service program.
- The internet daemon (inetd) application was the original super server program. The inetd program ran as a daemon, it listens for specific requests from clients and launching the appropriate service program when needed.
- The inetd program uses the /etc/inetd.conf configuration file to allow you to define the services for which it handles requests.
