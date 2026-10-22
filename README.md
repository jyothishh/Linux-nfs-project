\# Linux NFS Shared Storage Server



\## Project Overview



This project demonstrates the setup of a Network File System (NFS) server on Red Hat Enterprise Linux (RHEL) and its configuration for remote access from an Ubuntu client.



The objective is to understand Linux server administration, network file sharing, filesystem permissions, service management, and persistent mounts.



\## Architecture



\* \*\*NFS Server:\*\* Red Hat Enterprise Linux (RHEL)

\* \*\*NFS Client:\*\* Ubuntu Linux

\* \*\*Shared Directory:\*\* `/nfs-share`

\* \*\*Client Mount Point:\*\* `/mnt/nfs1-client`

\* \*\*Protocol:\*\* Network File System (NFS)



See the `architecture/` directory for the project architecture diagram, if included.



\## Technologies Used



\* Red Hat Enterprise Linux

\* Ubuntu Linux

\* Network File System (NFS)

\* Linux command line

\* systemd

\* Linux filesystem permissions

\* Git and GitHub



\## Implementation Steps



1\. Install NFS utilities on the RHEL server.

2\. Create the shared directory.

3\. Configure the NFS export.

4\. Start and enable the NFS service.

5\. Install NFS client utilities on Ubuntu.

6\. Mount the remote shared directory.

7\. Test file access between the client and server.

8\. Configure a persistent mount using `/etc/fstab`, if required.

9\. Document configuration, validation, and troubleshooting.



\## Key Linux Commands



Check the NFS server service:



```bash

sudo systemctl status nfs-server

```



Display exported directories:



```bash

sudo exportfs -v

```



Mount the shared directory on Ubuntu:



```bash

sudo mount -t nfs SERVER\_IP:/nfs-share /mnt/nfs1-client

```



Verify the mounted filesystem:



```bash

findmnt /mnt/nfs-share

```



Replace `SERVER\_IP` with the actual IP address of your NFS server.



\## Repository Structure



```text

Linux-nfs-project/

├── README.md

├── docs/

│   ├── server-setup.md

│   ├── client-setup.md

│   ├── troubleshooting.md

│   └── security.md

├── screenshots/

└── architecture/

```



The structure above is the intended layout; include only files and directories that actually exist in your repository.



\## Skills Demonstrated



\* Linux server configuration

\* NFS installation and configuration

\* Linux service management

\* Network file sharing

\* Filesystem permissions and ownership

\* Persistent filesystem mounts

\* Basic troubleshooting

\* Technical documentation

\* Git and GitHub



\## Validation and Evidence



Add screenshots documenting the actual implementation, including:



\* NFS server service status

\* NFS export configuration

\* Exported directory details

\* Client mount verification

\* File-sharing tests

\* Filesystem permissions

\* Persistent mount configuration, if implemented



Only mark a test as successful after verifying it in your lab.



\## Learning Outcomes



This project provides hands-on practice with Linux storage sharing and server administration. The concepts are relevant to Linux administration, cloud support, and shared-storage services such as Amazon EFS.



\## Author



Jyothish J.



