# NFS Server Configuration — RHEL

## 1. Objective

Configure a Red Hat Enterprise Linux (RHEL) machine as an NFS server to provide shared directory access to an Ubuntu client over a local network.

## 2. Environment

| Component          | Configuration  |
| ------------------ | -------------- |
| Operating System   | RHEL 10        |
| Server Role        | NFS Server     |
| Shared Directory   | `/nfs-share`   |
| Configuration File | `/etc/exports` |
| NFS Utilities      | `nfs-utils`    |

## 3. Install NFS Utilities

Install the required package:

```bash
sudo dnf install nfs-utils -y
```

Verify the installation:

```bash
rpm -q nfs-utils
```

## 4. Create the Shared Directory

```bash
sudo mkdir -p /nfs_share
```

Verify the directory:

```bash
ls -ld /nfs_share
```

## 5. Configure NFS Exports

Edit the configuration file:

```bash
sudo nano /etc/exports
```

Example export entry:

```text
/nfs_share 10.161.177.138(rw,sync,root_squash,no_subtree_check)
```

Replace the client IP address with the actual Ubuntu client IP.

### Export options

* `rw`: Requests read/write access to the exported directory.
* `sync`: Requests synchronous handling of changes before acknowledging them.
* `root_squash`: Maps remote root access to an unprivileged identity.
* `no_subtree_check`: Disables subtree checking.

## 6. Apply the Configuration

```bash
sudo exportfs -rav
```

Verify the exported directory:

```bash
sudo exportfs -v
```

## 7. Start and Enable NFS

```bash
sudo systemctl enable --now nfs-server
```

Check the service:

```bash
sudo systemctl status nfs-server --no-pager
```

## 8. Validation Results

Record the actual results after testing:

* [ ] NFS utilities installed successfully.
* [ ] Shared directory created.
* [ ] Export configuration applied.
* [ ] NFS service running successfully.
* [ ] Export visible in `exportfs -v`.

## 9. Evidence

Screenshots are stored in the project's `screenshots/` directory.

Relevant evidence:

* NFS package installation.
* NFS service status.
* Export configuration.
* Export verification.
