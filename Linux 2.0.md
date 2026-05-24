
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
১. কারখানায় কী কী কাজ চলছে তা দেখার জন্য (ps, top, htop)
ps (Process Status): এটা হলো একটা চটজলদি ফটো তোলার মতো। তুমি কমান্ডটা দিলে ওই মুহূর্তে কারখানায় ঠিক কী কী কাজ চলছে, তার একটা স্থির তালিকা তোমাকে দেখাবে।

top (Table of Processes): এটা কোনো স্থির ছবি না, এটা হলো কারখানার ভেতরের একটা লাইভ সিসিটিভি ক্যামেরা (Live CCTV Camera)। কোন কাজটা করতে সবচেয়ে বেশি শক্তি (CPU) বা জায়গা (RAM) লাগছে, তা এটা লাইভ স্ক্রিনে সেকেন্ডে সেকেন্ডে আপডেট করে দেখায়।

htop: এটা top ক্যামেরার মতোই, তবে এটা দেখতে অনেক রঙিন এবং সুন্দর। কারখানার কোন মেশিন কতটুকু গরম বা ব্যস্ত, তা গ্রাফ দিয়ে খুব সহজে বুঝিয়ে দেয়। এটা চালানো অনেক আরামদায়ক!

২. কোনো দুষ্টু বা আটকে যাওয়া কাজ বন্ধ করার জন্য (kill, pkill, killall)
মাঝে মাঝে কারখানার কোনো মেশিন জ্যাম হয়ে যায় বা কোনো শ্রমিক কথা শোনে না। তখন ম্যানেজার হিসেবে তোমাকে সেই কাজ জোর করে বন্ধ করতে হয়। কারখানার প্রত্যেকটা কাজের একটা নির্দিষ্ট টোকেন নাম্বার থাকে, যেটাকে বলে PID (Process ID)।

kill PID: এটা হলো নির্দিষ্ট টোকেন নাম্বার ধরে ডেকে বলা—"এই যে ১০৫ নাম্বার প্রসেস, তুমি এখনই তোমার কাজ বন্ধ করো!"

pkill name: যদি তুমি টোকেন নাম্বার না জানো, কিন্তু কাজের নাম জানো (যেমন: chrome), তখন তুমি নাম ধরে চিৎকার দিয়ে বলবে—"ক্রোম নামের যে প্রসেসটা আছে, কাজ বন্ধ করো!"

killall name: কারখানায় যদি একই নামের অনেকগুলো কাজ চলতে থাকে (যেমন একই সাথে ৫টা গেমের উইন্ডো খোলা), আর তুমি যদি সবাইকে একবারে থামাতে চাও, তখন বলবে—"কারখানায় যতগুলো chrome নামের কাজ চলছে, সব একবারে বন্ধ করে দাও!"

৩. কাজ সামনে আনা বা পেছনে লুকিয়ে রাখার জন্য (bg, fg)
bg (Background): কোনো কোনো কাজ করতে অনেক সময় লাগে (যেমন বড় একটা ফাইল ডাউনলোড হওয়া)। তুমি তো আর সেই কাজের সামনে ঠায় দাঁড়িয়ে থাকবে না! এই কমান্ড দিলে কাজটা কারখানার পেছনের রুমে (Background-এ) একা একা চলতে থাকে, আর তোমার সামনের টেবিলটা খালি হয়ে যায় অন্য কাজ করার জন্য।

fg (Foreground): পেছনের রুমে যে কাজটা লুকিয়ে চলছিল, সেটাকে আবার তোমার চোখের সামনে মেইন টেবিলে (Foreground-এ) নিয়ে আসার জন্য এটা ব্যবহার করা হয়।

fg n: পেছনের রুমে যদি অনেকগুলো কাজ চলতে থাকে (যেমন ১ নাম্বার কাজ, ২ নাম্বার কাজ), তখন তুমি নির্দিষ্ট করে বলতে পারো—"২ নাম্বার কাজটাকে আমার টেবিলের সামনে নিয়ে এসো।"

৪. কাজের গুরুত্ব বা স্পিড ঠিক করার জন্য (nice, renice)
কারখানায় কোন কাজটা আগে হবে আর কোনটা আস্তে আস্তে করলেও চলবে, তা তুমি ঠিক করতে পারো। এটাকে বলে ভালো মানুষি বা "Nice" ভ্যালু।

nice -n value cmd: কোনো নতুন কাজ শুরু করার সময় তুমি যদি বলো তার নাইস ভ্যালু অনেক বেশি (যেমন +১৯), তার মানে প্রসেসটা খুব "ভদ্র"। সে অন্য সব কাজের জন্য রাস্তা ছেড়ে দেবে এবং নিজে আস্তে আস্তে কাজ করবে। আর নাইস ভ্যালু মাইনাস (যেমন -২০) হলে সে হবে "স্বার্থপর", অন্য সব কাজ থামিয়ে সে সবার আগে দ্রুত নিজের কাজ শেষ করবে।

renice +n PID: একটা কাজ অলরেডি কারখানায় চলছে। মাঝপথে ম্যানেজার হিসেবে তোমার মনে হলো—"আরে, এই কাজটা তো অনেক লেট করছে, এটাকে একটু দ্রুত করা দরকার!" তখন তুমি চলন্ত কাজের টোকেন নাম্বার (PID) ধরে তার স্পিড কম বা বেশি করে দিতে পারো।

৫. কাজের ওপর গোয়েন্দাগিরি করার জন্য (strace, ltrace)
কারখানার কোনো একটা মেশিন ঠিকমতো কাজ করছে না, কিন্তু বাইরে থেকে দেখে তুমি বুঝতে পারছ না ভেতরে কী সমস্যা। তখন তুমি গোয়েন্দা (Detective) নিয়োগ করো।

strace -p PID: এই গোয়েন্দা প্রসেসটার ওপর কড়া নজর রাখে যে সে কম্পিউটার সিস্টেমের মূল ভল্ট বা মেমরির সাথে কী কী আদানপ্রদান করছে (System Calls)। সে ফাইল খুলছে কি না, নাকি নেটওয়ার্ক ব্যবহার করছে—সব খাতায় লিখে তোমাকে দেখাবে।

ltrace -p PID: এই গোয়েন্দা একটু আলাদা। সে দেখে প্রসেসটা তার নিজের বন্ধুদের তৈরি করা ছোট ছোট নিয়ম বা লাইব্রেরি (Library Calls) ঠিকঠাক মতো মেনে চলছে কি না।

৬. কাজের রিপোর্ট খাতায় লিখে রাখার জন্য (&>, 1>, 2>)
কারখানার মেশিনগুলো যখন কাজ করে, তখন তারা কিছু সাধারণ কথা বলে (Output) আর মাঝে মাঝে ভুল করলে চিৎকার করে "ভুল হয়েছে" বলে (Error)। তুমি চাইলে এই কথাগুলো স্ক্রিনে না দেখিয়ে একটা ডায়েরি বা ফাইলে (file) লিখে রাখতে পারো। > চিহ্নটা একটা তীরের মতো কাজ করে, যা সব কথা ফাইলের দিকে ঠেলে দেয়।

1>file: (১ মানে হলো সাধারণ কথা বা Output) প্রসেসটা সফলভাবে যে কাজটা করেছে, তার ভালো ভালো রিপোর্টগুলো সব এই ফাইলে জমা হবে।

2>file: (২ মানে হলো ভুল বা Error) প্রসেসটা কাজ করতে গিয়ে কী কী ভুল করেছে, সেই বিপদের বা ভুলের মেসেজগুলো শুধু এই ফাইলে জমা হবে, ভালো কথাগুলো এখানে আসবে না।

&>file: (& মানে হলো সবকিছু একসাথে) প্রসেসটার ভালো কথা, খারাপ কথা, ভুলের মেসেজ—সবকিছু একবারে খিচুড়ি পাকিয়ে এই একটা ফাইলের ভেতরে ডায়েরির মতো লেখা হয়ে যাবে।

### 7. Advanced Process Analysis (NEW)
```
fuser, pgrep, pidof
ls -l /proc/PID/exe, cat /proc/PID/maps, ls -l /proc/PID/fd
```
১. গোয়েন্দাগিরি করে চোর বা আইডি খুঁজে বের করা (fuser, pgrep, pidof)
মাঝে মাঝে কারখানায় অদ্ভুত সমস্যা হয়। যেমন—একটা ফাইল বা ফোল্ডার তুমি ডিলিট করতে যাচ্ছ, কিন্তু কম্পিউটার বলছে "অন্য কেউ এটা ব্যবহার করছে!" তখন এই কমান্ডগুলো কাজে লাগে:

fuser (File User): এটা হলো কারখানার সেই সিকিউরিটি গার্ড, যে কোনো একটা খেলনার বা ফাইলের ওপর হাত দিয়ে দাঁড়িয়ে থাকে। তুমি যদি তাকে জিজ্ঞেস করো, "এই ফাইলটা এখন কোন কোন শ্রমিক হাত দিয়ে ধরে রেখেছে?" সে সাথে সাথে সেই কাজের আইডি (PID) তোমাকে বলে দেবে। এমনকি fuser -k দিলে সে ওই ফাইল আটকে রাখা শ্রমিককে ধাক্কা দিয়ে বের করে দেবে!

pgrep (Process Grep): এটা হলো কারখানার এক অদ্ভুত গোয়েন্দা। তুমি তাকে পুরো নাম না বলে শুধু নামের একটা অংশ (যেমন: chrom) বললে সে পুরো কারখানা খুঁজে বের করবে এবং ওই নামের সাথে মিলে যাওয়া সব শ্রমিকের আইডি (PID) একটা কাগজে লিখে এনে তোমাকে দেবে।

pidof (PID of...): এটা খুব সোজা সাপটা একটা ছেলে। তুমি তাকে কোনো কাজের একদম সঠিক নাম ধরে ডাকবে (যেমন: pidof chrome), আর সে কোনো কথা না বাড়িয়ে ফুড়ুৎ করে ওই কাজের আসল আইডি নাম্বারটা (PID) তোমার সামনে এনে হাজির করবে।

২. প্রসেসের পেটের ভেতরের খবর নেওয়া (proc ডিরেক্টরি)
কম্পিউটারের ভেতরে /proc নামে একটা জাদুকরী ড্রয়ার আছে। কারখানায় যতগুলো কাজ চলে, এই ড্রয়ারের ভেতরে তাদের সবার নামে একটা করে ফাইল-ফোল্ডার তৈরি হয় (যেমন আইডি ১০৫ হলে ফোল্ডারের নাম হয় /proc/105/)। এই ফোল্ডারগুলোর ভেতরে উঁকি দিলে প্রসেসটার অনেক গোপন খবর জানা যায়:

ls -l /proc/PID/exe: এটা দিয়ে তুমি দেখতে পারো একটা চলন্ত কাজ আসলে কারখানার কোন আসল ফাইল বা সফটওয়্যার থেকে তৈরি হয়েছে। যেমন, ১০৫ নাম্বার আইডিটা আসলে কি আসল গেম নাকি কোনো ভাইরাস, সেটার আসল ঠিকানা বা রাস্তা (Path) এটা তোমাকে দেখিয়ে দেবে।

cat /proc/PID/maps: একটা প্রসেস যখন কাজ করে, তখন সে কারখানার মেইন মেমোরি বা টেবিলের (RAM) অনেকগুলো জায়গা দখল করে রাখে। এই কমান্ডটা দিলে একটা মানচিত্র (Map) খুলে যায়, যা দেখায় ওই প্রসেসটা মেমোরির কোন কোন কোণা, কোন কোন ফাইল এবং কতটুকু জায়গা নিজের জন্য বুক করে রেখেছে।

ls -l /proc/PID/fd (File Descriptors): একটা প্রসেস কাজ করার সময় একসাথে অনেকগুলো ফাইল পড়তে পারে, গান বাজাতে পারে বা ইন্টারনেট ব্যবহার করতে পারে। এই fd ফোল্ডারটা হলো সেই প্রসেসের "হাতের মুঠো"। এই কমান্ড দিলে তুমি দেখতে পাবে ওই প্রসেসটা এই মুহূর্তে ঠিক কোন কোন ফাইল বা জিনিস নিজের হাত দিয়ে ধরে রেখেছে (Open করে রেখেছে)।

### 8. Service Management (systemd) (NEW)
```
systemctl start/stop/enable/disable/mask/status service
systemctl list-units, systemctl list-unit-files
systemctl daemon-reload, systemd-analyze
```
১. বড় রোবটদের অর্ডার দেওয়া (systemctl commands)
ধরো কারখানায় একটা রোবট আছে যার নাম generator (বিদ্যুৎ দেওয়ার জন্য)। তুমি সুপারভাইজারকে ডেকে এই অর্ডারগুলো দিতে পারো:

systemctl start generator: রোবটটা এখন ঘুমাচ্ছে। তুমি বললে—"জেনারেটর রোবট, এখনই ঘুম থেকে ওঠো এবং কাজ শুরু করো!"

systemctl stop generator: রোবটটা চলছে। তুমি বললে—"জেনারেটর, অনেক হয়েছে, এবার তোমার কাজ বন্ধ করো।"

systemctl enable generator: এটা একটা দারুণ অর্ডার। এর মানে হলো—"শোনো সুপারভাইজার, আজকে রাতে যখন কারখানা বন্ধ হবে এবং কাল সকালে যখন কারখানা আবার নতুন করে খুলবে (Boot হবে), এই জেনারেটর রোবট যেন নিজে নিজেই ঘুম থেকে উঠে কাজ শুরু করে দেয়। আমাকে যেন এসে অন করতে না হয়।"

systemctl disable generator: এটার মানে হলো—"কাল সকালে কারখানা খোলার পর এই রোবট যেন নিজে নিজে চালু না হয়। আমি এসে বললে তবেই অন হবে।"

systemctl mask generator: এটা হলো রোবটটাকে কড়া শাস্তি দেওয়া! অনেক সময় কোনো ভুল কারণে একটা বন্ধ রোবট নিজে নিজে চালু হয়ে যেতে পারে। তুমি যদি mask করে দাও, তবে রোবটের সুইচের ওপর সুপারভাইজার একটা শক্ত টেপ মেরে দেবে। এরপর কেউ চাইলেও ভুল করে বা জোর করে ওই রোবট চালু করতে পারবে না, যতক্ষণ না তুমি তাকে unmask করছ।

systemctl status generator: এটা দিয়ে তুমি সুপারভাইজারকে জিজ্ঞেস করো—"জেনারেটর রোবটের খবর কী?" সুপারভাইজার তখন একটা রিপোর্ট দেখাবে যে রোবটটা এখন চলছে নাকি ঘুমাচ্ছে (Active or Inactive), কতক্ষণ ধরে চলছে এবং সে শেষ কী কী কাজ করেছে।

২. রোবটদের তালিকা বা হাজিরা খাতা দেখা
systemctl list-units: এটা হলো কারখানার মেইন ফ্লোরে গিয়ে দেখা—"এই মুহূর্তে ঠিক কোন কোন রোবট লাইভ কাজ করছে বা অ্যাক্টিভ আছে।" যারা ঘুমাচ্ছে তাদের নাম সাধারণত এখানে থাকে না।

systemctl list-unit-files: এটা হলো কারখানার স্টোর রুমে রাখা মাস্টার ক্যাটালগ বা ফাইলের তালিকা। কারখানায় মোট কতগুলো রোবট আছে (সেটা এখন চলুক আর না চলুক) এবং কাল সকালে কারখানা খোলার পর তারা নিজে নিজে চালু হবে কি না (enabled/disabled)—তার পুরো লিস্ট এখানে দেখা যায়।

৩. কারখানার সিস্টেম আপডেট ও স্পিড মাপা
systemctl daemon-reload: মাঝে মাঝে ম্যানেজার হিসেবে তুমি কোনো রোবটের ভেতরের আসল নিয়মের খাতা বা ব্লুপ্রিন্ট (Configuration File) বদলে দাও। কিন্তু বিগ বস সুপারভাইজার তো পুরনো নিয়মটাই মুখস্থ করে বসে আছে! এই কমান্ডটা দিলে সুপারভাইজার তার মাথাটা একটা ঝাড়া দেয় এবং সব রোবটের নতুন নিয়মের খাতাগুলো আবার পড়ে আপডেট করে নেয়।

systemd-analyze: কাল সকালে যখন তুমি কারখানার মেইন গেট খুললে (Computer Boot হলো), পুরো কারখানা পুরোপুরি চালু হতে মোট কত সেকেন্ড বা মিনিট সময় লাগলো, তার একটা স্টপওয়াচ বা টাইমিং রিপোর্ট দেয় এই কমান্ড। এমনকি systemd-analyze blame দিলে সে একদম আঙুল দিয়ে দেখিয়ে দেবে—"স্যার, ওই অলস জেনারেটর রোবটটার চালু হতে সবচেয়ে বেশি সময় লেগেছে, ও একাই ৫ সেকেন্ড নষ্ট করেছে!"

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
