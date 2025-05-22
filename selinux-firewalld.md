# SELinux and Firewalld in Linux

This guide covers basic usage and configuration of SELinux (Security-Enhanced Linux) and firewalld (dynamic firewall manager).

---

## 🔐 SELinux (Security-Enhanced Linux)

SELinux is a security module that provides access control policies.

### Check current mode
```bash
getenforce
```

### Change SELinux mode temporarily
```bash
sudo setenforce 0   # permissive
sudo setenforce 1   # enforcing
```

### Change SELinux mode permanently
Edit the config file:
```bash
sudo vim /etc/selinux/config
```

Set the value:
```conf
SELINUX=permissive   # or enforcing / disabled
```

---

### View SELinux status and context
```bash
sestatus
ls -Z /path/to/file
```

---

## 🔥 Firewalld - Dynamic Firewall Management

### Check firewall status
```bash
sudo systemctl status firewalld
```

### Start and enable firewalld
```bash
sudo systemctl enable --now firewalld
```

---

## 🌐 Manage Services and Ports

### List active zones
```bash
firewall-cmd --get-active-zones
```

### List allowed services
```bash
firewall-cmd --list-all
```

### Add a service (e.g. HTTP)
```bash
sudo firewall-cmd --add-service=http
```

### Add port
```bash
sudo firewall-cmd --add-port=8080/tcp
```

### Make changes permanent
```bash
sudo firewall-cmd --runtime-to-permanent
```

Or directly add with `--permanent` and reload:
```bash
sudo firewall-cmd --add-service=https --permanent
sudo firewall-cmd --reload
```

---

### Remove service or port
```bash
sudo firewall-cmd --remove-service=http --permanent
sudo firewall-cmd --remove-port=8080/tcp --permanent
sudo firewall-cmd --reload
```

---

## ✅ Summary

| Command                          | Description                           |
|----------------------------------|---------------------------------------|
| `getenforce`                     | Show SELinux mode                     |
| `setenforce`                     | Set SELinux mode temporarily          |
| `/etc/selinux/config`           | Set SELinux mode permanently          |
| `firewall-cmd --list-all`        | Show current firewall config          |
| `--add-service=http`             | Open service port                     |
| `--add-port=8080/tcp`            | Open custom port                      |
| `--reload`                       | Apply firewall changes                |
