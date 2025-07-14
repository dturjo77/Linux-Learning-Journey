
System Monitoring Commands 📊

Welcome to the world of system monitoring! These commands are like magic tools 🪄 that let you peek inside your computer to see how it’s doing. Imagine your computer as a busy toy factory, and these tools help you check how fast the workers (CPU), storage (disks), and machines (memory) are working. Each section below explains a command, its options (flags), and fun examples to make it super easy to understand, even for a 10-year-old! Let’s dive in! 🚀
Table of Contents

1. iostat
2. vmstat
3. htop
4. sar
5. dstat
6. iotop
7. perf
Tips and Tricks


1. iostat
What it does: iostat is like a doctor checking your computer’s heart (CPU) and how fast it’s moving toys (data) to and from the storage (disk). It shows how busy your CPU is and how much reading/writing your disk is doing.
How to Use
Run this to see basic CPU and disk stats:
iostat

Example Output
Linux 5.15.0-73-generic (my-laptop) 07/15/2025

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          10.20    0.00    2.30    0.50    0.00   87.00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               5.00      100.50       50.25     1005000     502500


CPU: %user (10.2%) means programs are using 10.2% of the CPU. %idle (87%) means the CPU is relaxing.
Disk: sda (your hard drive) reads 100.5 KB per second and writes 50.25 KB per second.

Flags



Flag
Description



-c
Show only CPU stats (skip disk).


-d
Show only disk stats (skip CPU).


-x
Show detailed stats (like disk usage percentage).


<interval> <count>
Update every <interval> seconds, <count> times (e.g., 1 3 for 1 second, 3 updates).


More Examples

Check every 2 seconds, 3 times:
iostat 2 3

This updates CPU and disk stats every 2 seconds, 3 times.

Show detailed disk stats:
iostat -x -d

Output:
Device:  rrqm/s   wrqm/s   r/s   w/s   rkB/s   wkB/s   %util
sda       0.00     0.00   2.50  1.50  80.00   40.00    5.20

%util shows the disk is only 5.2% busy.



Note: You might need sudo for detailed stats. Install with sudo apt install sysstat (Ubuntu).


2. vmstat
What it does: vmstat is like a spy watching your computer’s workers (processes), toy storage (memory), and delivery trucks (disks). It shows how many processes are waiting, how much memory is free, and disk activity.
How to Use
Run this for a quick snapshot:
vmstat

Example Output
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0      0  800000 100000 200000    0    0    50    25  100  200 10  5 80  5  0


r: 1 process is ready to run.
free: 800,000 KB (~800 MB) of free memory.
us/sy/id: CPU usage (10% user, 5% system, 80% idle).

Flags



Flag
Description



-s
Show detailed stats (like total memory).


-d
Show disk stats (read/write sectors).


<interval> <count>
Update every <interval> seconds, <count> times.


More Examples

Update every 3 seconds, 4 times:
vmstat 3 4

Shows how memory and CPU change over time.

Show detailed stats:
vmstat -s

Output:
    16384  total memory
    8000  used memory
    8384  active memory




3. htop
What it does: htop is like a colorful dashboard showing all the programs running in your toy factory. You can scroll, sort, or even stop programs using your keyboard!
How to Use
Start it with:
htop

What You See

Top: Bars for CPU, memory, and swap usage.
Bottom: List of processes (like firefox, bash) with their CPU and memory usage.
Use arrow keys to scroll, F9 to stop a process, or q to quit.

Flags



Flag
Description



-u <user>
Show only processes for a specific user (e.g., htop -u bob).


-s <column>
Sort by a column (e.g., htop -s CPU).


-d <delay>
Set refresh delay in tenths of a second (e.g., -d 10 for 1 second).


More Examples

Show only Bob’s processes:
htop -u bob

Shows only programs Bob is running (like his games).

Refresh every 0.5 seconds:
htop -d 5




Note: Install with sudo apt install htop (Ubuntu).


4. sar
What it does: sar is like a time-traveling reporter that logs how your computer’s CPU, memory, disk, and network were doing. It’s part of the sysstat package.
How to Use
Run this for real-time stats:
sar 1 3

Example Output
Linux 5.15.0-73-generic (my-laptop) 07/15/2025

02:53:01 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
02:53:02 AM     all      10.50      0.00      3.20      0.80      0.00     85.50

Shows CPU usage over 3 seconds.
Flags



Flag
Description



-u
Show CPU usage (default).


-d
Show disk activity.


-r
Show memory usage.


-n DEV
Show network stats.


<interval> <count>
Update every <interval> seconds, <count> times.


More Examples

Check disk stats:
sar -d 2 3

Output:
02:53:01 AM       DEV       tps  rd_sec/s  wr_sec/s
02:53:03 AM      sda      5.00    100.00     50.00


Check memory usage:
sar -r 1 3

Shows memory stats like free and used memory.



Note: Install with sudo apt install sysstat (Ubuntu).


5. dstat
What it does: dstat is a colorful, flexible spy showing real-time stats for CPU, disk, network, and more. You can mix and match what you want to see!
How to Use
Start with:
dstat

Example Output
----total-cpu-usage---- -dsk/total- -net/total- ---paging-- ---system--
usr sys idl wai stl  read  writ   recv  send   in   out   int   csw
 10   5  80   5   0   100k   50k    10k   20k    0k    0k   200   300

Flags



Flag
Description



-c
Show CPU stats.


-d
Show disk stats.


-n
Show network stats.


-g
Show paging stats.


-y
Show system stats (interrupts, context switches).


More Examples

Show CPU and disk only:
dstat -cd


Show top CPU and I/O users:
dstat -cd --top-cpu --top-io

Highlights programs using the most CPU and disk.



Note: Install with sudo apt install dstat (Ubuntu).


6. iotop
What it does: iotop is a detective that shows which programs are reading or writing to your disk the most. It’s interactive like htop.
How to Use
Run with:
sudo iotop

What You See

List of processes with their disk read/write speeds.
Use arrow keys to scroll or q to quit.

Flags



Flag
Description



--only
Show only processes using disk I/O.


-u <user>
Show only processes for a specific user.


-p <pid>
Show only a specific process ID.


More Examples

Show only active disk users:
sudo iotop --only


Show Bob’s disk usage:
sudo iotop -u bob




Note: Always needs sudo. Install with sudo apt install iotop (Ubuntu).


7. perf
What it does: perf is a scientist analyzing why programs are slow or using too much CPU. It’s great for finding performance problems.
How to Use
Measure a command’s performance:
sudo perf stat ls

Example Output
 Performance counter stats for 'ls':
          0.123456 ms task-clock
             1234 context-switches
               10 cpu-migrations
              567 page-faults

Flags



Flag
Description



stat
Show performance stats for a command.


record
Record performance data.


report
Show a report from recorded data.


-g
Include call graph (function calls).


More Examples

Record a program’s performance:
sudo perf record -g sleep 5
sudo perf report

Records sleep 5 and shows a detailed report.

Average over 3 runs:
sudo perf stat -r 3 ls




Note: Needs sudo. Install with sudo apt install linux-tools-common (Ubuntu).


Tips and Tricks

Mix and match: Open two terminals and run htop and iotop to see CPU and disk usage together.
Watch trends: Use sar -u 1 10 to monitor CPU for 10 seconds.
Customize dstat: Try dstat -cdngy --top-cpu for a full system overview.
Be careful with perf: It’s powerful but can generate big data files with record.

Have fun exploring your computer’s toy factory! If you want more examples or help, just ask! 😄
