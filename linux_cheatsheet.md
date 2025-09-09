# 🐧 Linux Administration Cheatsheet

Quick reference for essential Linux system administration commands.

---

## 📂 File and Directory Management
```bash
ls -l            # List files with details
ls -a            # Show hidden files
pwd              # Show current directory
cd /path/to/dir  # Change directory
mkdir newdir     # Create a directory
rmdir olddir     # Remove empty directory
rm -rf dir       # Remove directory and contents
cp file1 file2   # Copy file
mv file1 file2   # Move/Rename file
find / -name xyz # Search for file
```

---

## 👤 User Management
```bash
whoami                 # Show current user
id                     # Show user ID and group ID
adduser username       # Add a new user
passwd username        # Set password
usermod -aG group user # Add user to group
deluser username       # Remove user
groups                 # Show groups
su - username          # Switch user
```

---

## 🔑 Permissions
```bash
ls -l              # View permissions
chmod 755 file     # Change permissions (rwxr-xr-x)
chown user:group file  # Change ownership
umask              # Show default permissions mask
```

---

## ⚙️ Process Management
```bash
ps aux             # Show all processes
top                # Monitor processes live
htop               # Interactive process viewer (if installed)
kill -9 <pid>      # Kill process by PID
pkill processname  # Kill by process name
jobs               # Show background jobs
fg %1              # Bring job to foreground
bg %1              # Resume job in background
```

---

## 💾 Disk and Filesystem
```bash
df -h              # Show disk usage
du -sh *           # Show folder sizes in current dir
mount              # Show mounted filesystems
mount /dev/sdb1 /mnt # Mount drive
umount /mnt        # Unmount drive
lsblk              # List block devices
fdisk -l           # Show disk partitions
```

---

## 📡 Networking
```bash
ip a               # Show IP addresses
ip route           # Show routing table
ping google.com    # Test connectivity
curl ifconfig.me   # Show public IP
netstat -tulnp     # Show open ports
ss -tulwn          # Show listening ports
scp file user@host:/path  # Secure copy
rsync -avz src dst # Sync files
ssh user@host      # Connect via SSH
```

---

## 📦 Package Management

### Debian/Ubuntu (APT)
```bash
apt update
apt upgrade
apt install pkg
apt remove pkg
```

### RHEL/CentOS (YUM/DNF)
```bash
yum update
yum install pkg
yum remove pkg

# On newer systems:
dnf update
dnf install pkg
dnf remove pkg
```

### Arch Linux (Pacman)
```bash
pacman -Syu
pacman -S pkg
pacman -R pkg
```

---

## 🖥️ System Monitoring
```bash
uptime            # Show system uptime
free -h           # Show memory usage
vmstat 1          # Show CPU/memory stats
iostat            # Show disk I/O stats
dmesg | less      # Show kernel messages
journalctl -xe    # Show logs (systemd)
```

---

## 🔐 Services and Systemctl
```bash
systemctl status service   # Check service status
systemctl start service    # Start service
systemctl stop service     # Stop service
systemctl restart service  # Restart service
systemctl enable service   # Enable service at boot
systemctl disable service  # Disable service at boot
systemctl list-units --type=service --state=running
```

---

## ⏰ Scheduling Tasks
```bash
crontab -e             # Edit cron jobs
crontab -l             # List cron jobs

# Example (run script daily at 2am)
0 2 * * * /path/to/script.sh
```

---

## 🧹 Useful Cleanup
```bash
history             # Show command history
history -c          # Clear history
du -sh *            # Find large folders
apt autoremove      # Remove unused packages (Debian/Ubuntu)
journalctl --vacuum-time=7d  # Remove old logs
```

---

✅ This cheatsheet covers essential Linux administration tasks for daily operations.
