# Basic Linux Navigation

## Overview
Today, I started my Linux journey by learning fundamental navigation commands, focusing on understanding the file system and basic file operations in a Kali Linux VM. This is part of *The Linux Command Line* (Chapter 3) and TryHackMe's "Linux Fundamentals 1" course.

## Learning Objectives
- Understand and use commands: `ls`, `cd`, `pwd`, `clear`, `mkdir`, `touch`, `rm`, `cp`, `mv`.
- Navigate the Linux file system confidently.
- Complete practical tasks to reinforce learning.

## Tasks
1. **TryHackMe: Linux Fundamentals 1** (1 hour)
   - Completed the module, learning how to navigate directories and manage files.
   - Key takeaway: Understanding the Linux file system hierarchy (e.g., `/home`, `/etc`).
2. **Kali VM Practice** (1 hour)
   - Created a directory: `mkdir test`
   - Added a file: `touch file1.txt`
   - Navigated directories: `cd test`, `pwd` to confirm location
   - Deleted the file: `rm file1.txt`

## Practice
- Listed hidden files: `ls -a` (discovered `.` and `..` entries).
- Moved a file: `mv file1.txt test/` to practice file relocation.

## Notes
- `ls -a` reveals hidden files, which start with a dot (e.g., `.bashrc`).
- `pwd` is super helpful for keeping track of my current directory.
- Accidentally tried `rm` without checking—learned to double-check before deleting!


---

## 📂 1. `ls`

**Lists files and folders in the current directory.**

```bash
ls
```

🧒 Like looking inside your current folder.

---

## 🔍 2. `ls -R`

**Lists all files, including in subfolders (recursive).**

```bash
ls -R
```

🪜 See everything inside every folder.

---

## 👻 3. `ls -a`

**Shows hidden files (those starting with a dot).**

```bash
ls -a
```

🔍 Reveals files like `.bashrc`.

---

## 📋 4. `ls -al`

**Lists everything in detail (permissions, size, date, etc.).**

```bash
ls -al
```

📊 See who owns the files and when they were changed.

---

## 🚪 5. `cd directoryname`

**Changes your current folder.**

```bash
cd Documents
```

👟 Move into the Documents folder.

---

## ⬆️ 6. `cd ..`

**Goes up one level in the folder structure.**

```bash
cd ..
```

🚶 Step back to the parent folder.

---

## 🧭 7. `pwd`

**Prints where you are (current folder path).**

```bash
pwd
```

🗺️ Shows something like `/home/username/Desktop`.

---

## 📃 8. `cat > filename`

**Creates a new file and lets you type into it. Press Ctrl+D to save.**

```bash
cat > hello.txt
```

✍️ Type your message and hit Ctrl+D to finish.

---

## 📖 9. `cat filename`

**Shows the content of a file.**

```bash
cat hello.txt
```

📰 Great for short files.

---

## ➕ 10. `cat file1 file2 > file3`

**Joins two files and saves into a new file.**

```bash
cat file1.txt file2.txt > merged.txt
```

🧩 Combine files into one!

---

## 🕑 11. `touch filename`

**Creates an empty file or updates the time it was last modified.**

```bash
touch new.txt
```

📁 Good for making quick files.

---

## 🗑️ 12. `rm filename`

**Deletes a file.**

```bash
rm old.txt
```

🚫 Poof! It’s gone.

---

## 📝 13. `cp source destination`

**Copies a file or folder.**

```bash
cp hello.txt backup.txt
```

📄 Makes a duplicate copy.

---

## 🚚 14. `mv source destination`

**Moves or renames a file/folder.**

```bash
mv file.txt newname.txt
```

✏️ Rename or organize files.

---

## 🕵️ 15. `find / -name filename`

**Finds a file anywhere on your computer (slow).**

```bash
find / -name "myfile.txt"
```

🔎 Search from the root. Add `sudo` if needed.

---

## 📌 16. `file filename`

**Tells what kind of file it is.**

```bash
file photo.jpg
```

🧠 Knows if it’s text, image, or binary.

---

## 📑 17. `less filename`

**Lets you scroll through a file one page at a time.**

```bash
less bigfile.txt
```

🔽 Use arrow keys, `q` to quit.

---

## ⬆️ 18. `head filename`

**Shows the first 10 lines of a file.**

```bash
head notes.txt
```

---

## ⬇️ 19. `tail filename`

**Shows the last 10 lines of a file.**

```bash
tail log.txt
```

🧪 Great for watching logs.

---

## 📂 20. `lsof`

**Lists files that are currently open by apps.**

```bash
lsof
```

🔍 See what programs are using files.

---

## 📏 21. `du -h --max-depth=1`

**Shows how big folders are (one level deep).**

```bash
du -h --max-depth=1
```

📦 Good for finding space hogs.

---

## 💾 22. `parted /dev/sdX`

**Manages hard disk partitions (advanced).**

```bash
sudo parted /dev/sda
```

⚠️ Be careful! Use only if you know disks.

---

## 📊 23. `stat filename`

**Shows detailed info about a file.**

```bash
stat myfile.txt
```

⏰ Shows last access, change, modify times, and permissions.

---

## 🧩 24. `strings filename`

**Pulls out readable text from a file (great for binary or malware).**

```bash
strings program.exe
```

🧠 Useful in security and reverse engineering.

---

## 🔢 25. `xxd filename`

**Shows the file in hexadecimal (hex dump).**

```bash
xxd myfile
```

🔍 Like peeking inside the file’s code.

---

## 📏 26. `truncate -s size filename`

**Changes a file’s size. Shrink or grow it.**

```bash
truncate -s 0 myfile.txt
```

📁 This will make the file empty!

---

## 🔥 27. `shred -u filename`

**Securely deletes a file by overwriting it.**

```bash
shred -u secret.txt
```
