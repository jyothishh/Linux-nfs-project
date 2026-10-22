# NFS Client Configuration — Ubuntu

## 1. Objective

Configure an Ubuntu Linux machine to mount and access a shared directory exported by a RHEL NFS server.

## 2. Environment

| Component            | Configuration     |
| -------------------- | ----------------- |
| Operating System     | Ubuntu 22.04      |
| Client Role          | NFS Client        |
| NFS Server Directory | `/nfs_share`      |
| Client Mount Point   | `/mnt/nfs1-client`|
| Client Utilities     | `nfs-common`      |

## 3. Install NFS Client Utilities

```bash
sudo apt update
sudo apt install nfs-common -y
```

## 4. Create the Mount Point

```bash
sudo mkdir -p /mnt/nfs_share
```

## 5. Mount the Shared Directory

Replace the server IP if necessary:

```bash
sudo mount -t nfs 192.168.1.32:/nfs_share /mnt/nfs_share
```

Verify the mount:

```bash
findmnt /mnt/nfs_share
```

## 6. Test File Sharing

Create a test file:

```bash
sudo touch /mnt/nfs_share/test-from-ubuntu.txt
```

Verify that the file exists:

```bash
ls -l /mnt/nfs_share
```

On the RHEL server, verify the same file:

```bash
ls -l /nfs_share
```

The file should be visible on both systems if the mount and file operation succeed.

## 7. Configure Persistent Mounting

Back up the filesystem configuration:

```bash
sudo cp /etc/fstab /etc/fstab.backup
```

Edit the file:

```bash
sudo nano /etc/fstab
```

Add an appropriate entry:

```text
192.168.1.32:/nfs_share /mnt/nfs_share nfs defaults,_netdev 0 0
```

Validate the configuration:

```bash
sudo mount -a
findmnt /mnt/nfs_share
```

Replace the example IP with the actual server address.

## 8. Validation Results

Record the actual results:

* [ ] NFS client utilities installed.
* [ ] Shared directory mounted.
* [ ] File-sharing test successful.
* [ ] Persistent mount configuration validated.
* [ ] Permissions verified.

## 9. Evidence

Screenshots of the client mount, file-sharing test, and persistent mount validation are stored in the `screenshots/` directory.
