## 📄 samba-centos

# Samba on CentOS - Share Files with Windows

This guide explains how to install and configure Samba on CentOS to share a folder with Windows clients.

---

## 📦 1. Install Samba Packages

```bash
sudo yum install samba samba-client samba-common -y

## 📁 2. Create Shared Directory

sudo mkdir -p /srv/samba/shared
sudo chown -R nobody:nogroup /srv/samba/shared
sudo chmod -R 0775 /srv/samba/shared

nobody:nogroup allows guest access without a specific Linux user

## 🛠️ 3. Configure Samba Share

Open the main config file:

sudo nano /etc/samba/smb.conf

Add this to the end of the file:

[Shared]
   path = /srv/samba/shared
   browseable = yes
   read only = no
   guest ok = yes

## 🔄 4. Enable and Start Samba Services

sudo systemctl enable --now smb
sudo systemctl enable --now nmb

## 🔑 5. Create Samba User (optional)

If you want user authentication:

sudo smbpasswd -a yourlinuxuser

## 🔥 6. Open Firewall for Samba

sudo firewall-cmd --permanent --add-service=samba
sudo firewall-cmd --reload

## 💻 7. Access from Windows

On Windows File Explorer, go to:

\\<CentOS-IP>\Shared

Example

\\192.168.1.100\Shared

## ✅ Summary

| Step             | Command / File                     |
| ---------------- | ---------------------------------- |
| Install Samba    | `yum install samba samba-client`   |
| Shared Folder    | `/srv/samba/shared`                |
| Config File      | `/etc/samba/smb.conf`              |
| Restart Services | `systemctl enable --now smb nmb`   |
| Allow Firewall   | `firewall-cmd --add-service=samba` |
| Access from Win  | `\\CentOS-IP\Shared`               |
