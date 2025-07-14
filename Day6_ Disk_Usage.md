# 💾 Disk Usage & Disk Utility Commands — Explained with Examples

These commands help you understand how much space your files and drives are using and also let you create disk speed test files.

---

## 📊 1. `df` — Disk Free

**What it does:**  
Shows total and available disk space on mounted filesystems.

### 🧾 Basic Usage

```bash
df
```

📉 Shows size in blocks (not easy to read).

### ✅ Recommended Usage

```bash
df -h
```

🧠 `-h` = human-readable (shows MB/GB instead of blocks).

#### 📌 Other Options

| Option | Meaning |
|--------|---------|
| `-h` | Show sizes in human-readable format |
| `-T` | Show filesystem type |
| `-a` | Include dummy filesystems |

---

## 📁 2. `du` — Disk Usage

**What it does:**  
Shows how much space files and folders are taking up.

### 📂 Basic Usage

```bash
du
```

🧱 Shows usage in blocks for each file/folder.

### ✅ Recommended Usage

```bash
du -h
```

📏 Shows usage in readable sizes (KB, MB, GB).

### 🧮 Example: Show folder sizes at top level only

```bash
du -h --max-depth=1
```

🧾 Lists each directory size in the current folder only.

#### 📌 Other Options

| Option | Meaning |
|--------|---------|
| `-h` | Human-readable sizes |
| `--max-depth=N` | Show depth of folder structure |
| `-a` | Show all files, not just folders |
| `-s` | Show total size only (summary) |

---

## ⚙️ 3. `dd` — Data Duplicate

**What it does:**  
Low-level copying of data — useful for creating test files, USB images, etc.

### 📄 Example: Create a test file for disk speed

```bash
dd if=/dev/zero of=testfile bs=1G count=1 oflag=dsync
```

💡 What this does:
- `if=/dev/zero` → reads zeros (empty data)
- `of=testfile` → writes to `testfile`
- `bs=1G` → block size of 1 gigabyte
- `count=1` → write only 1 block
- `oflag=dsync` → make sure it's fully written before finishing (real speed test)

### 🔥 Wipe a disk (USE WITH CAUTION)

```bash
dd if=/dev/zero of=/dev/sdX bs=1M
```

❌ This will erase all data! (Used to wipe drives)

#### 📌 Other Options

| Option | Meaning |
|--------|---------|
| `if=` | Input file (or source) |
| `of=` | Output file (or destination) |
| `bs=` | Block size |
| `count=` | Number of blocks |
| `oflag=dsync` | Ensure sync write (accurate testing) |

---

## 🧠 Summary Table

| Command | Purpose | Key Option |
|---------|---------|------------|
| `df` | View mounted disk space | `-h` |
| `du` | View folder/file space usage | `-h`, `--max-depth` |
| `dd` | Test speed or write data directly | `bs=`, `count=`, `oflag=` |

---

## 🚀 4. `hdparm -Tt /dev/sda`

**What it does:**  
Measures disk read speed for buffered and cached reads.

### ⚡ Example

```bash
sudo hdparm -Tt /dev/sda
```

🧠 Output tells:
- `-T` → Cached read speed (RAM test)
- `-t` → Direct disk read speed (real disk performance)

#### 📌 Flags

| Option | Meaning |
|--------|---------|
| `-T` | Test cached reads (from memory) |
| `-t` | Test buffered reads (from disk) |

> 🔐 You need `sudo` for this command.

---

## 📦 5. `lsblk`

**What it does:**  
Lists all block devices (disks, partitions, USBs, etc.) in a tree-like format.

### 🧾 Basic Usage

```bash
lsblk
```

### 🧮 With Extra Info

```bash
lsblk -f
```

Shows filesystem type, label, and UUID.

#### 📌 Flags

| Option | Meaning |
|--------|---------|
| `-f` | Show filesystem info |
| `-o +UUID` | Add UUID to output |
| `-d` | Show only physical devices (no partitions) |

---

## 🆔 6. `blkid`

**What it does:**  
Shows the UUID and filesystem type of each block device.

### 🧾 Basic Usage

```bash
sudo blkid
```

### 🕵️ For a Specific Device

```bash
sudo blkid /dev/sda1
```

📌 Useful for editing `/etc/fstab`.

#### 📌 Output Fields

- `UUID`: Universally Unique Identifier
- `TYPE`: Filesystem type (ext4, swap, etc.)
- `LABEL`: Optional volume name

---

## 📁 7. `df -i`

**What it does:**  
Shows inode usage for each mounted filesystem.

### 🧮 Example

```bash
df -i
```

📌 Inodes = Number of files your disk can hold.

- `Used` → How many inodes are in use
- `IUse%` → Inode usage percentage
- `Filesystem` → Which disk or partition

#### 📌 Flags

| Option | Meaning |
|--------|---------|
| `-i` | Show inode stats instead of disk size |

---

## 🧠 Summary Table

| Command | Purpose | Flags / Notes |
|---------|---------|----------------|
| `hdparm -Tt` | Test disk speed | Needs `sudo` |
| `lsblk` | View disks & mount points | `-f`, `-o`, `-d` |
| `blkid` | Show UUID & filesystem | Needs `sudo` |
| `df -i` | View inode usage | `-i` flag |

---
