# Serving Local Networks
- Linux servers are also commonly used in local network environments to provie simple network services. This section walks through the most common services ysed on local networks.
## File Servers
- The sharing of files has become a necessity in any business environment. Allowing multiple employees to create and edit files in a common folder can greatly improve collaboration efforts in any project.
- There are two basic methods for sharing files in a local network environment:
  - Peer-to-peer
  - Client-server
### Peer-to-peer
- In this method of file sharing, one workstations enables another workstation to access files stored locally on its hard drive.
- This method allows collaboration between two employees on a small local network but becomes somewhat difficult if you need to share data between more than two people.
### Client-server
- The client-server method of file sharing utilizes a centralized file server for sharing files that multiple clients can access and modify as needed.
- However, with the centralized file server, an administrator must control who has access to which files and folders, protecting them from unauthorized access.
## Common server software packages used for sharing files
### The Network File System (NFS) 
- This protocol is used to share folders in a network environment. With NFS, a Linux system can share a portion of its virtual directory on the network to allow access by clients as well as other servers.
- In Linux, the software package used to accomplish this is nfs-utils.
- The nfs-utils package provides the driver to support NFS as well as the underlying client and server software to both share local folders on the network and connect to remote folders shared by other linux systems on the local network.
- Using nfs-utils, the linux system can mount remotely shared NFS folders almost as easily as if they were on a local hard drive partition.
### Samba
- The Samba software package was created to allow linux systems to interact with Windows clients and servers.
- With Samba, the Linux system can act either as a client, connecting to Windows server shared folders, or as a server, allowing Windows workstations to connect to shared folders on the Linux system.
- Samba does take some work in configuring the correct parameters to manage access to the shared folders.
## Print Servers
- The ability to share network printers has become a requirement for most offices and has also become popular in many home environments. 
- The standard Linux print sharing software package is called the Common Unix Printing System (CUPS).
- The CUPS software allows a Linux system to connect to any printer resource, either loccally or via a network, using a common application interface that operates over a dedicated printer drivers.
- The key to CUPS is the printer driver and the use of Internet Printing Protocol (IPP). The CUPS system also allows you to share a locally attached printer with other Linux systems.
## Network Resource Servers
- Running a local network requires quite a few different resources to keep clients and servers in sync. Linux provides a few different service packages that network administrators can use to make their lives easier.
### IP Addresses
- Every device on a local network must have a unique IP address to interact with other devices on the network. To help simplify this, developers have created the Dynamic Host Configuration Protocol (DHCP).
- A central DHCP server keeps track of the IP addresses assigned, ensuring that no two clients receive the same IP address.
- The most popular Linux DHCP server package is maintained by the Internet Systems Consortium (ISC) and is called DHCPd.
  - Once you have the DHCPd server running on your network, you'll need to tell your Linux clients to use it to obtain their network addresses.  This requires DHCP client software packages.
  - For Linux DHCP clients, there are three popular packages that you can use
    - dhclient
    - dhcpcd
    - pump
-  Most Debian and Red hat based distributions use the dhclient package and even install it by default when a network card is detected during the installation process.
## Logging
- Linux maintains log files that record various key details about the system as it runs. The log files are normally stored locally in the /var/log directory.
- In network environment it can come in handy to have Linux servers store their system logs on a remote logging server.
- A remote logging server provides a safe backup of the original log files, plus a safe place to store logs in case of a system crash or a break-in by an attacker.
- There are two main logging packages used in Linux, and which one system uses depends on the startup software it uses.
  - rsyslogd: The SysVinit and Upstart utilizes the journald service for both local and remote logging of system information.
  - journald: The Systemd system utilizes the journald service for both local and remote logging of system information.
- Both rsyslogd and journald use configuration files that allow you to define just how data is logged and what clients the server accepts log messages from.
## Name Servers
- DNS maps IP addresses to a host naming scheme on networks. A DNS server acts as a directory lookup to find the names of servers on the local network.
- Linux servers use the BIND software package to provide DNS naming services. The main program in BIND is named, the server daemon that runs on Linux servers and resolves hostnames to IP addresses for clients on the local network.
- This allows clients to point to only one DNS name server and be able to resolve any IP address on the Internet.
## Network Management
- The Simple Network Management Protocol (SNMP) provides a way for an administrator to query remote network devices and servers to obtain information about their configuration, status, and even perforance.
- SNMP operates in a simple client/server paradigm.
- Network devices and servers run an SNMP server service that listens for requests from SNMP client packages. The SNMP client sends requests for data from the SNMP server.
- The SNMP standards have changed over the years
  - SNMPv1: provided for only simple password authentication of clients and passed all data as individual plaintext records.
  - SNMPv2: Implemented basic level of security and provided for the bulk transmission of monitoring data to help reduce the network traffic required to monitor devices.
  - SNMPv3: current version, utilizes both strong authentication and data encryption capabilities and provides a more streamlined management system.
- The most popular SNMP software package in Linux is the open source net-snmp package. This has SNMPv3 compatibility, allows you securely monitor all aspects of a Linux server remotely.
## Time
- For many network applications to work correctly, both servers and clients need to have their internal clocks coordinated with the same time.
- The Network Time Protocol (NTP) accomplishes this, it allows servers and clients to synchronize on the same time source across multiple networks, adding or subtracting fractions of a second as needed to stay in sync.
- For Linux systems, the ntpd program synchronizes a Linux system with remote NTP servers on the Internet.
- It's common to have a single Linux server use ntpd to synchronize with a remote time standard server and then have all other servers and clients on the local network sync their times to the local linux server. 
