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
- The Network File System (NFS): This protocol is used to share folders in a network environment. With NFS, a Linux system can share a portion of its virtual directory on the network to allow access by clients as well as other servers.
- In Linux, the software package used to accomplish this is nfs-utils.
- The nfs-utils package provides the driver to support NFS as well as the underlying client and server software to both share local folders on the network and connect to remote folders shared by other linux systems on the local network.
- Using nfs-utils, the linux system can mount remotely shared NFS folders almost as easily as if they were on a local hard drive partition. 
