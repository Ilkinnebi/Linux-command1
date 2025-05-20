# Users, Permissions and Advanced Permissions in Linux

## 👤 User Management

### Add a new user
```bash
sudo useradd username
sudo passwd username
```

### Modify user
```bash
sudo usermod -aG groupname username  # Add to group
```

### Show user info
```bash
id username
whoami
```

---

## 🔒 File Permissions

### View file permissions
```bash
ls -l filename
```

### chmod – Change permissions
```bash
chmod 755 file      # rwxr-xr-x
chmod u+x script.sh # Add execute to user
```

### chown – Change owner
```bash
chown user:group file
```

### umask – Default permission mask
```bash
umask                # Show current
umask 022            # Set default
```

---

## 🛡️ Special Permissions

### Sticky Bit (+t)
- Only file owner can delete files in the directory.

```bash
chmod +t /shared
```

### SetUID (+s on user)
- Runs a file with the owner's privileges.

```bash
chmod u+s /path/to/file
```

### SetGID (+s on group)
- New files inherit group from the directory.

```bash
chmod g+s /shared/folder
```

---

## 🎯 ACL (Access Control Lists)

### View ACL
```bash
getfacl file
```

### Set ACL
```bash
setfacl -m u:username:rwx file
```

### Remove ACL
```bash
setfacl -x u:username file
```

### Default ACL for new files in a directory
```bash
setfacl -d -m u:username:rw /some/folder
```
