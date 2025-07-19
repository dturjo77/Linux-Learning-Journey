# 🧠 Linux Process Management Commands Cheat Sheet

This file contains essential Linux commands used to monitor, control, and manage system processes.

---

## 📋 View Processes:

🔹### Command: ps
    shows a snapshot of the currently running processes on your system. It helps you see what programs (processes) are running at the moment.
| Command            | What It Does                                |
| ------------------ | ------------------------------------------- |
| `ps -e` or `ps -A` | Show **all processes** on the system        |
| `ps -u <username>` | Show processes for a specific user          |
| `ps aux`           | Show **detailed info** for all processes    |
| `ps -ef`           | Show full-format list (similar to `ps aux`) |

 🔹### Command: top
     Shows the real-time view of what your system is doing right now.
     htop (optional) Enhanced top with colors and interactivity
 ---
## ❌ Killing Processes:

 🔹### Command: kill
     Full Meaning: Sends a signal to a process — usually used to stop or terminate it.
     kill <PID>        Ex:kill 1234

     1. killall – Kill by name
        killall <process_name>     Ex:killall firefox

     2. pkill – Kill by pattern (partial name)
        pkill <name_or_pattern>    Ex:pkill fire

     3. xkill – Kill by clicking on a window (GUI only)
        xkill

      | Command   | Kill By      | GUI Support  | Use Case                   |
      | --------- | ------------ | ------------ | -------------------------- |
      | `kill`    | PID          | ❌           | Kill a specific process    |
      | `killall` | Exact name   | ❌           | Kill all of one type       |
      | `pkill`   | Name/pattern | ❌           | Kill using name patterns   |
      | `xkill`   | Mouse click  | ✅           | Kill unresponsive GUI apps |
 ---
 ## 🚦 Foreground, Background, and Job Control:

   🔹### Command: Ctrl + Z   Full Meaning: Suspends a running process (puts it in the background as "stopped").

   🔹### Command: jobs   Full Meaning: Lists all background and stopped jobs.

   🔹### Command: bg   Full Meaning: Background
       Purpose: Resumes a suspended (paused) job and runs it in the background.

   🔹### Command: fg   Full Meaning: Foreground
       Purpose: Brings a background or suspended job back to the foreground (your active terminal).
       You're running multiple tasks. One is quietly working in the background.
       Now you want to bring it back to the front so you can watch or control it — that’s what fg does.

       | Command | What it does                            |
       | ------- | --------------------------------------- |
       | `jobs`  | Shows list of background/suspended jobs |
       | `bg`    | Resume a paused job in background       |
       | `fg`    | Resume a job in foreground              |
       | `fg %n` | Bring job number **n** to foreground    |
 ---
   ## 🎯 Changing Process Priority:

    🔹### Command: renice   Full Meaning: Re-set the nice value
        Purpose: Changes the priority of a running process — higher or lower.
        renice [nice value] or +n -p [PID]

    🔹### Command: nice -n value command
         Full Meaning: Start a new process with a given priority (nice value).
         nice -n [value] [command]       
 ---
   ## 📁 Redirecting Output:
 
    🔹### &>filename: Redirects both stdout and stderr to a file.
          1>filename: Redirects stdout to a file.
          2>filename: Redirects stderr to a file. 

       | Command  | What it redirects     | Sent to |
       | -------- | --------------------- | ------- |
       | `1>file` | Standard output only  | `file`  |
       | `2>file` | Error output only     | `file`  |
       | `&>file` | Both output and error | `file`  |
 ---
   ## 🛠️ Tracing & Debugging:

     🔹### Command: strace -p <pid>  Purpose:Traces system calls made by a running process.

     🔹### Command: ltrace -p <pid>  Purpose:Traces library function calls made by a running process.
 ---




