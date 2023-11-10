# Implementing Security
- These days, security is at the top of every system administrator's list of worries. Implementing security is a vital role for every Linux administrator.
- The following sections walk through the server software packages that you may run into as you implement security in Linux servers.
## Authentication Server
- The core security for Linux servers is the standard userid and password assigned to each individual user on the system and stored in either the /etc/passwd (on non-secure legacy systems) or the /etc/shadow file.
- Each Linux server maintians its own list of valid user accounts that have access on that server. 
- There are a few different methods for sharing user account databases across multiple Linux servers on a network.
## NIS
- The Network Information System (NIS) is a directory service that allows both clients and servers to share a common naming directory.
- The NIS naming directory is often used as a common repository for user accounts, hostnames, and even email information on a local network.
- The NIS+ protocol expands on NIS by adding security features. 
- The nis-utils package is an open source project for implementing an NIS and NIS+ directory in a Linux environment. 
## Kerberos
- Kerberos was developed at MIT as a secure authenticiation protocol. It uses symmetric-key cryptography to securely authenticate users with a centralized server database.
- The entire authentication process is encrypted, making it a secure method of logging into a Linux server.
- Many common Linux server applications provide plug-in modules to interface with a kerberos database for authenticating application users.
## LDAP
- Network authentication systems have taken off in the commercial networking world. Microsoft's Active Directory system is one example.
- The lightweight Directory Access Protocol (LDAP) is a simple network authentication service to multiple applications and evices on a local network.
- The most popular and free implementation of LDAP in the Linux world is the OpenLDAP package. OpenLDAP allows you to design a hierarchical database to store objects in your network.
- In the hierarchical database, objects are connected in a treelike fashion to one another.
- The hierarchical databases allows you to group objects by types, such as users and servers, or by location, or both. 
- The OpenLDAP package consists of both client and server programs. The client program allows systems to access an OpenLDAP server to authenticate requesrs made by clients or other network objects.
## Certificate Authority
- A better method of authenticating users is using certificates. A certificate is an encrypted key that implements a two factor authentication method.
- To log into a server, a user must have two things: 
  - Something you possess, such as the certificate file.
  - Something they know, such as a PIN.
- A certificate identifies a specific user on the network. Only one user should have a certificate and know the PIN required to access the certificate.
- However, it's important that the server trusts the certificate as well. For that, you need a certificate authority.
- The OpenSSL package provides standard certificate functions for both servers and clients. You can set up your Linux server to create certificates for clients and then authenticate them for network applications.
## Access Server (SSH)
- Remotely accessing servers in today's environment is risky, logging into a server from a remote location using a plaintext protocol such as Telnet or FTP is not a good idea anymore.
- Instead, you should use a remote access protocol that incorporates encryption around data sent across the network.
- The most popular software package that implements SSH in the Linux environment is the OpenSSH package. The OpenSSH package provides secure Telnet, FTP, and even remote copy feature using SSH. 
- The OpenSSH program also supports a feature called tunneling. With tunneling, you can wrap any type of network transaction with an encryption layer, thus protecting any type of network application even if it's not directly supported by the OpenSSH software.
## Virtual Private Networks
- Remotely connecting to servers on your local network via the internet can be a dangerous thing. Your network traffic takes many hops between many intermediary networks before getting to your servers, providing lots of opportunities for prying eyes to snoop the data. 
- The solution to remotely connecting to resources on a local network is the virtual private network (VPN) protocol.
- The VPN protocol creates a secure point-to-point tunnel between a remote client or server and a VPN server on your local network.
- In Linux, a popular VPN solution is the OpenVPN package. The OpenVPN package runs as a server service on a Linux server on your local network. Remote clients can use OpenVPN to connect with the OpenVPN server to establish connectivity to the server and then, once on the server, gain access to the rest of your local network.
## Proxy Server
- A web proxy server allows you to intercept web requests from local network clients. By intercepting the web requests, you have control of how clients interact with remote web servers.
- By intercepting the web requests, you have control of how clients interact with remote web servers.
- The web proxy server can block websites you don't want your network clients to see, and the server can cache common websites so that future requests for the same pages load faster.
- The most popular web proxy server in Linux is the Squid package. You can configure it to work both as a filter and as a caching server.
## Monitoring
- There are several monitoring tools available in the Linux world. The Nagios software package is quickly becoming a popular tool, especially in cloud linux systems. Nagios uses SNMP to monitor the performance and logs of Linux servers and provide results in a simple graphical window environment.
