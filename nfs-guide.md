## NFS - Network File System in Linux

NFS (Network File System) allows you to share directories and files with others over a network.

---

# 📦 1. Install NFS Packages

### On the NFS server:
```bash
sudo yum install nfs-utils -y     # RHEL/CentOS
sudo apt install nfs-kernel-server -y  # Ubuntu/Debian


# On the NFS client:

sudo yum install nfs-utils -y
sudo apt install nfs-common -y

# 📁 2. Configure NFS Server

Create a shared directory:

sudo mkdir -p /srv/nfs/shared
sudo chown nobody:nogroup /srv/nfs/shared

# Add export rule in /etc/exports:

echo "/srv/nfs/shared 192.168.1.0/24(rw,sync,no_subtree_check)" | sudo tee -a /etc/exports

# Export and enable NFS service:

sudo exportfs -rav
sudo systemctl enable --now nfs-server

## 🔗 3. Mount NFS Share on Client

Create a mount point:

sudo mkdir -p /mnt/nfs_shared

# Mount the share:

sudo mount 192.168.1.100:/srv/nfs/shared /mnt/nfs_shared

Replace 192.168.1.100 with the actual IP of the NFS server.

# Make it permanent by adding to /etc/fstab:

192.168.1.100:/srv/nfs/shared  /mnt/nfs_shared  nfs  defaults  0  0

## ✅ Summary

| Action               | Command or File                   |
| -------------------- | --------------------------------- |
| Install NFS          | `nfs-utils` / `nfs-kernel-server` |
| Shared directory     | `/srv/nfs/shared`                 |
| Export configuration | `/etc/exports`                    |
| Start service        | `systemctl start nfs-server`      |
| Export manually      | `exportfs -rav`                   |
| Client mount         | `mount server:/path /mount/point` |
| Persistent mount     | Add to `/etc/fstab`               |
