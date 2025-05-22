# LVM - Logical Volume Management in Linux

LVM (Logical Volume Manager) is a flexible and powerful way to manage disk space. It allows for dynamic resizing, snapshotting, and easy extension of partitions.

---

## 🧱 LVM Structure

1. **PV (Physical Volume)** – Physical disk or partition (e.g., /dev/sdb1)
2. **VG (Volume Group)** – Group of PVs combined into one pool
3. **LV (Logical Volume)** – Logical partition created from VG

---

## 🛠️ Step-by-Step LVM Setup

### 1. Create Physical Volume (PV)
```bash
sudo pvcreate /dev/sdb1
```

### 2. Create Volume Group (VG)
```bash
sudo vgcreate myvg /dev/sdb1
```

### 3. Create Logical Volume (LV)
```bash
sudo lvcreate -L 5G -n mylv myvg
```

---

## 🧾 Format and Mount the Logical Volume

### Format as ext4
```bash
sudo mkfs.ext4 /dev/myvg/mylv
```

### Create mount point and mount
```bash
sudo mkdir /mnt/mylv
sudo mount /dev/myvg/mylv /mnt/mylv
```

### Make it permanent
Add to `/etc/fstab`:
```fstab
/dev/myvg/mylv  /mnt/mylv  ext4  defaults  0  0
```

---

## ➕ Extend Logical Volume

### Extend the size
```bash
sudo lvextend -L +2G /dev/myvg/mylv
```

### Resize filesystem
```bash
sudo resize2fs /dev/myvg/mylv
```

---

## ❌ Remove LVM Components (Carefully)

### Unmount and remove LV
```bash
sudo umount /mnt/mylv
sudo lvremove /dev/myvg/mylv
```

### Remove VG
```bash
sudo vgremove myvg
```

### Remove PV
```bash
sudo pvremove /dev/sdb1
```

---

## 🔍 LVM Monitoring Commands

```bash
lsblk             # Show devices and LVM structure
pvs               # List physical volumes
vgs               # List volume groups
lvs               # List logical volumes
```

---

## ✅ Summary

| Command         | Description                        |
|----------------|------------------------------------|
| `pvcreate`      | Create a physical volume           |
| `vgcreate`      | Create a volume group              |
| `lvcreate`      | Create a logical volume            |
| `lvextend`      | Extend an LV                       |
| `mkfs.ext4`     | Format the logical volume          |
| `mount`         | Mount the LV                       |
| `resize2fs`     | Resize the filesystem              |
| `pvs`, `vgs`, `lvs` | Display LVM structures        |
