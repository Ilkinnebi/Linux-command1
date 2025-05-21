# YUM, Process Management, and Networking in Linux

## 📦 YUM Package Manager

### Install a package
```bash
sudo yum install package-name
```

### Remove a package
```bash
sudo yum remove package-name
```

### Update all packages
```bash
sudo yum update -y
```

### List all available packages
```bash
yum list available
```

### Clean cache
```bash
sudo yum clean all
```

---

## ⚙️ Process Management

### View running processes
```bash
ps aux
top
htop        # Interactive process viewer
```

### Kill a process
```bash
kill PID
kill -9 PID   # Force kill
```

### Background & foreground
```bash
command &     # Run in background
fg            # Bring to foreground
jobs          # Show background jobs
```

### nice & renice (set process priority)
```bash
nice -n 10 command
renice -n 5 PID
```

### Manage services with systemd
```bash
systemctl start servicename
systemctl stop servicename
systemctl status servicename
```

---

## 🌐 Networking Commands

### Show IP address
```bash
ip a
```

### Test connectivity
```bash
ping 8.8.8.8
```

### Show open ports and connections
```bash
ss -tuln
netstat -tuln   # ifconfig/net-tools package needed
```

### DNS resolution
```bash
nslookup domain.com
```

### Routing and trace
```bash
traceroute domain.com
```

### Manage network with NetworkManager
```bash
nmcli device status
nmcli con show
nmcli con up id "Wired connection 1"
```
