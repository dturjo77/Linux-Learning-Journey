# 📊 System Monitoring Commands

## 📋 Table of Contents
1. [iostat](#1-iostat)
2. [vmstat](#2-vmstat)
3. [htop](#3-htop)
4. [sar](#4-sar)
5. [dstat](#5-dstat)
6. [iotop](#6-iotop)
7. [perf](#7-perf)
8. [Tips and Tricks](#tips-and-tricks)

---

## 1. iostat
**What it does**: `iostat` is like a doctor checking your computer’s heart (CPU) and how fast it’s moving toys (data) to and from the storage (disk).

### How to Use
```
iostat
```

### Example Output
```
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          10.20    0.00    2.30    0.50    0.00   87.00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               5.00      100.50       50.25     1005000     502500
```

### Flags

| Flag | Description |
|------|-------------|
| -c   | Show only CPU stats |
| -d   | Show only disk stats |
| -x   | Show detailed stats |
| `<interval> <count>` | Update every `<interval>` seconds, `<count>` times |

### More Examples
```
iostat 2 3
iostat -x -d
```

> Note: You might need `sudo`. Install: `sudo apt install sysstat`

---

## 2. vmstat
**What it does**: Like a spy watching your computer’s workers (processes), toy storage (memory), and delivery trucks (disks).

### How to Use
```
vmstat
```

### Example Output
```
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0      0  800000 100000 200000    0    0    50    25  100  200 10  5 80  5  0
```

### Flags

| Flag | Description |
|------|-------------|
| -s   | Show detailed stats |
| -d   | Show disk stats |
| `<interval> <count>` | Update every X seconds, Y times |

### More Examples
```
vmstat 3 4
vmstat -s
```

---

## 3. htop
**What it does**: A colorful dashboard of running programs. You can scroll, sort, or even stop them.

### How to Use
```
htop
```

### Flags

| Flag | Description |
|------|-------------|
| -u <user> | Show only user's processes |
| -s <column> | Sort by column |
| -d <delay> | Set refresh delay |

### More Examples
```
htop -u bob
htop -d 5
```

> Install: `sudo apt install htop`

---

## 4. sar
**What it does**: A time-traveling reporter that logs system activity over time.

### How to Use
```
sar 1 3
```

### Flags

| Flag | Description |
|------|-------------|
| -u   | CPU usage |
| -d   | Disk activity |
| -r   | Memory usage |
| -n DEV | Network stats |
| `<interval> <count>` | Repeat monitoring |

### More Examples
```
sar -d 2 3
sar -r 1 3
```

> Install: `sudo apt install sysstat`

---

## 5. dstat
**What it does**: A real-time stat viewer. Mix and match what you want to see!

### How to Use
```
dstat
```

### Flags

| Flag | Description |
|------|-------------|
| -c   | CPU stats |
| -d   | Disk stats |
| -n   | Network stats |
| -g   | Paging stats |
| -y   | System stats |

### More Examples
```
dstat -cd
dstat -cd --top-cpu --top-io
```

> Install: `sudo apt install dstat`

---

## 6. iotop
**What it does**: Shows which processes are using the disk the most.

### How to Use
```
sudo iotop
```

### Flags

| Flag | Description |
|------|-------------|
| --only | Show only I/O using processes |
| -u <user> | Filter by user |
| -p <pid> | Show specific process |

### More Examples
```
sudo iotop --only
sudo iotop -u bob
```

> Needs `sudo`. Install: `sudo apt install iotop`

---

## 7. perf
**What it does**: Performance analyzer for slow or CPU-heavy programs.

### How to Use
```
sudo perf stat ls
```

### Flags

| Flag | Description |
|------|-------------|
| stat   | Show stats |
| record | Record performance |
| report | Report from recording |
| -g     | Show call graph |

### More Examples
```
sudo perf record -g sleep 5
sudo perf report
sudo perf stat -r 3 ls
```

> Install: `sudo apt install linux-tools-common`

---

## 🎯 Tips and Tricks
- Open `htop` and `iotop` side-by-side to see full system usage.
- Use `sar -u 1 10` to watch CPU activity over 10 seconds.
- Combine `dstat -cdngy --top-cpu` for full system monitoring.
- Be mindful: `perf` can create large files when recording.

---
