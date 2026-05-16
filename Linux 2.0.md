
---

## 🧠 Complete Linux Foundation Masterlist (Cybersecurity Focused)

### 1. File Operations
```
ls, ls -R, ls -a, ls -al
cd <dir>, cd ..
pwd
cat > file, cat file, cat file1 file2 > file3
touch file
rm file
cp source dest, cp -r source dest (directory copy)
mv source dest
find / -name filename
file filename
less filename, head filename, tail filename
lsof
du -h --max-depth=1
parted /dev/sdX
stat filename
strings filename
xxd filename
truncate -s size filename
shred -u filename
```

### 2. Directory Operations
```
mkdir dir
rmdir dir
cp -r source dest
mv olddir newdir
find / -type d -name dirname
tree
rm -rf dir
```

### 3. User & Group Administration (NEW)
```
useradd, usermod, userdel, passwd, chage
groupadd, groupmod, groupdel, gpasswd
id, groups, whoami, w, last, lastb, faillock
visudo, sudo -l, su
```

### 4. File Permissions & Attributes
```
chmod octal file
chown owner file
chgrp group file
chmod -R octal dir
chown -R owner dir
setfacl -m u:user:rwx file
setfacl -d (default ACL)
getfacl file         # view ACLs
chattr +i/-i/a file  # immutable, append-only
lsattr file
```

### 5. SELinux / AppArmor (Mandatory Access Control) (NEW)
```
getenforce, setenforce, sestatus
semanage, restorecon, chcon, audit2allow
aa-status, aa-enforce, aa-complain, aa-logprof
```

### 6. Process Operations
```
ps, top, htop
kill PID, pkill name, killall name
bg, fg, fg n
nice -n value cmd, renice +n PID
strace -p PID, ltrace -p PID
&>file, 1>file, 2>file
```

### 7. Advanced Process Analysis (NEW)
```
fuser, pgrep, pidof
ls -l /proc/PID/exe, cat /proc/PID/maps, ls -l /proc/PID/fd
```

### 8. Service Management (systemd) (NEW)
```
systemctl start/stop/enable/disable/mask/status service
systemctl list-units, systemctl list-unit-files
systemctl daemon-reload, systemd-analyze
```

### 9. System Info & Monitoring
```
date, cal, uptime, w, whoami
uname -a, free -m, lscpu, lsmem, dmidecode
iostat, vmstat, sar, dstat, iotop, perf
```

### 10. Kernel Module Management (NEW)
```
lsmod, modinfo, modprobe, rmmod, insmod, depmod
```

### 11. Boot Process & Recovery (NEW)
```
chroot /mnt, grub-mkconfig, update-grub
systemctl rescue, systemctl emergency
kernel boot parameters: break, init=/bin/bash (conceptual)
```

### 12. Disk Usage & Filesystem Management
```
df -h, df -i, du -sh, du -h --max-depth=1
lsblk, blkid
hdparm -Tt /dev/sda
dd if=/dev/zero of=... bs=8k count=256k (speed test)
mount, umount, findmnt, losetup
mkfs.ext4, fsck, tune2fs, dumpe2fs, xfs_info
fdisk, gdisk
```

### 13. Mounting & Filesystem Operations (already combined above)
```
mount /dev/sdX1 /mnt
umount /mnt
findmnt
losetup -f image.img               (loop device setup)
mkfs.ext4 /dev/sdX1
mkfs.xfs /dev/sdX1
fsck /dev/sdX1
tune2fs -l /dev/sdX1               (ext4 info)
dumpe2fs /dev/sdX1
xfs_info /mnt
fdisk /dev/sdX, gdisk /dev/sdX
parted /dev/sdX                    (already in file ops, but here for partitioning)
mount -o remount,rw /
mount -t ntfs /dev/sdX1 /mnt
blkid /dev/sdX1                    (UUID)
```

### 14. Archives and Compression
```
tar -cf, tar -xf
tar -zcvf, tar -zxvf
tar -jcvf, tar -jxvf
gzip, gzip -d, zip -r, unzip
7z a, 7z x
```

### 15. Search & Find (Extended)
```
locate, whereis, which
find / -mtime -n
find / -perm -4000
find / -user root -perm -4000
find / -nouser
find / -size +10M -exec ls -lh {} \;
```

### 16. Text Processing (Extended)
```
grep pattern file, grep -r pattern dir, command | grep pattern
echo, sed 's/old/new/g', sed -i, diff, wc
awk, cut -d':' -f1 /etc/passwd
sort, uniq, tee
jq (JSON parsing)
tr, column, paste  # added for log parsing
```

### 17. Networking (Basic & Advanced)
```
ping, whois, dig, nslookup, host, resolvectl
ss, ip addr, ip link, ip route, arp, ip neighbor
ssh user@host, scp, wget, curl
traceroute, mtr
nmap
tcpdump -i eth0, tcpdump -w file.pcap, tcpdump -r file.pcap
tshark (if installed)
nc host port, nc -e /bin/bash (for reverse shells), ncat --ssl
```

### 18. Firewall Rule Manipulation (NEW)
```
iptables -A/-D/-I/-F/-P, iptables-save, iptables-restore
nft add rule, nft list ruleset, nft flush ruleset
ufw allow/deny/delete, ufw enable/disable
```

### 19. SSH Key Management & Hardening (NEW)
```
ssh-keygen, ssh-copy-id, ssh-agent, ssh-add
cat ~/.ssh/config, sudo nano /etc/ssh/sshd_config
ssh-keyscan
```

### 20. Encryption, Hashing & Encoding (NEW)
```
md5sum, sha256sum, sha512sum, base64
openssl enc -aes-256-cbc, openssl s_client
gpg --gen-key, gpg --encrypt, gpg --decrypt
```

### 21. Security-Specific Tools
```
auditctl, ausearch -f filename
fail2ban-client status
clamscan -r /path
chkrootkit, rkhunter --check
hashcat, hydra, metasploit (launch)
openssl x509 -in cert.pem -text
```

### 22. Binary Analysis & Reverse Engineering (NEW)
```
objdump, readelf, nm, ldd, size
gdb
```
(Already have strings, xxd in File Operations – use together.)

### 23. Forensic & Data Recovery Basics (NEW)
```
dd if=/dev/sda of=image.dd bs=4M status=progress
ddrescue
foremost, testdisk, extundelete, bulk_extractor
```

### 24. Package Installations & Querying (Extended)
```
sudo apt update/upgrade/install/remove/purge
sudo dnf update/install/remove
sudo pacman -Syu/-S/-R
sudo snap install/remove
dpkg -l, dpkg -S, dpkg -L
rpm -qa, rpm -qf
apt-cache show, apt-file search
```

### 25. Python pip (unchanged)
```
pip install, pip uninstall, pip freeze, pip install -r, pip list, pip show, pip install --user
```

### 26. Version Control (Git)
```
git init, clone, add, commit -m, status, pull, push
git branch, branch <name>, checkout, merge, stash, stash apply
git log, reset, rm, rebase, revert, cherry-pick, diff, blame
```

### 27. Environment Variables
```
env, echo $VAR, export VAR=value, alias name='cmd', echo $PATH
export PATH=$PATH:/new/path, unset VAR, source ~/.bashrc
```

### 28. Job Scheduling (Cron & Alternatives) (Extended)
```
crontab -l, -e, -r
@reboot command
cat /etc/crontab
at, batch, systemctl list-timers, systemd-run
systemctl status cron  (or crond)
```

### 29. Shell Scripting (Extended)
```
#!/bin/bash
$0..$9, ${10}, ${11}
if [ condition ]; then ... fi
for i in {1..10}; do ... done
while [ condition ]; do ... done
function name() { ... }, case, trap, read
$? (exit code)
test conditions: -f, -d, -z, -n, -eq, -gt
set -e, -u, -x
getopts, shift
```

### 30. System Hardening (sysctl) (NEW)
```
sysctl -a, sysctl -w net.ipv4.ip_forward=0
/etc/sysctl.conf (e.g., kernel.randomize_va_space=2)
```

### 31. Logging and Auditing (Extended)
```
journalctl, journalctl -u service
tail -f /var/log/syslog, tail -f /var/log/auth.log
logrotate
grep "error" /var/log/syslog, grep -i "failed" /var/log/auth.log
```

### 32. Others (Terminal Productivity)
```
command1 ; command2
command1 && command2
command1 || command2
command &
history, watch command
tmux, screen
```

---
