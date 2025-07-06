# Day 1: Basic Linux Navigation

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

[Back to Main README](README.md)
