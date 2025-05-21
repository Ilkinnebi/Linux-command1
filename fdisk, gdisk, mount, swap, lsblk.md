## 📄 Mövzu: Disks and Partitions (fdisk, gdisk, mount, swap, lsblk)

# Disks and Partitions in Linux

This guide covers basic disk and partition management commands in Linux including fdisk, gdisk, mount, swap and lsblk.

---

## 🔍 View Disks and Partitions

### List block devices
```bash
lsblk

## Show partition and file system info

```bash
fdisk -l
```
## 💽 Partitioning with fdisk (MBR)

```bash
sudo fdisk /dev/sdX
```

Common commands inside fdisk:
m – Help

n – New partition

p – Print partition table

d – Delete partition

w – Write changes and exit

## 📂 Mounting a Filesystem

```bash
sudo mkdir /mnt/mydisk
sudo mount /dev/sdX1 /mnt/mydisk
sudo umount /mnt/mydisk
```
## 🔄 Make Mount Permanent

```bash
/dev/sdX1  /mnt/mydisk  ext4  defaults  0  2
```

## 🔄 Swap Management

Create swap file

```bash
sudo fallocate -l 1G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```
## Enable on boot

Add to /etc/fstab:

```bash
/swapfile none swap sw 0 0
```
## Check swap

```bash
swapon --show
free -h
```

## ✅ Summary

| Command     | Description         |
| ----------- | ------------------- |
| `lsblk`     | List block devices  |
| `fdisk`     | Partition MBR disks |
| `gdisk`     | Partition GPT disks |
| `mount`     | Attach filesystem   |
| `umount`    | Detach filesystem   |
| `fallocate` | Create swap file    |
| `mkswap`    | Make swap format    |
| `swapon`    | Enable swap         |
