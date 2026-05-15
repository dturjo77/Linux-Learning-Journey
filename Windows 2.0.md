
---

## 🪟 Complete Windows Foundation Masterlist (Cybersecurity Focused)

### 1. File Operations
```
dir
dir /s
dir /a
cd \directoryname
cd ..
pwd (PowerShell: Get-Location)
type filename
copy source destination
move source destination
del filename
touch filename (PowerShell: New-Item)
Get-ChildItem -Path path -Recurse -Name filename
Get-Content filename
Get-Item filename
Remove-Item filename
Get-Content filename -Head 10
Get-Content filename -Tail 10
Get-FileHash filename
fsutil file createnew filename size
```

### 2. Directory Operations
```
mkdir directoryname
rmdir directoryname
copy /s source destination (recursive)
move source destination (rename/move directories)
Get-ChildItem -Path path -Recurse -Directory
Remove-Item -Recurse directoryname
```

### 3. Registry Analysis (NEW – Critical for Forensics)
```
reg query HKLM\... /v ValueName
reg add HKLM\... /v ValueName /t REG_SZ /d data
reg delete HKLM\... /v ValueName
reg export HKLM\... output.reg
reg save HKLM\SAM sam.hive
reg load HKU\TempUser C:\Users\username\NTUSER.DAT
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\...
Set-ItemProperty -Path ... -Name ... -Value ...
Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
Get-ChildItem -Path HKCU:\Software\Microsoft\Windows\CurrentVersion\Run
```

### 4. Sysinternals Suite (NEW – Live Response Essentials)
*(Download from Microsoft Sysinternals; add folder to PATH)*
```
autorunsc -a (all autostarts)
procexp (GUI; Process Explorer)
procmon (GUI; Process Monitor)
tcpview (GUI)
handle -a (list all open handles)
sigcheck -e -u -v file.exe (verify signature)
psexec \\remote cmd
streams filename (detect Alternate Data Streams)
sdelete -p 3 file (secure delete)
```

### 5. Process Operations (Enhanced)
```
tasklist
taskkill /PID pid
taskkill /IM name
Get-Process
Stop-Process -Name name
Start-Process command
Set-ProcessPriority -Id pid -Priority value
Get-Process | Sort-Object CPU -Descending
Get-Service (NEW – view services)
sc query serviceName
sc stop/start serviceName
Get-CimInstance Win32_Process (detailed process info)
wmic process list full (legacy, but useful)
```

### 6. File Permissions & ACLs (Extended)
```
icacls filename /grant user:permissions
icacls filename /setowner owner
icacls directory /t
Get-Acl filename
Set-Acl -Path filename -AclObject acl
icacls filename /inheritance:r (remove inherited)
icacls filename /remove user
icacls filename /reset (reset to inherited)
```

### 7. Networking (Basic & Deep Dive)
```
ping host
tracert domain
nslookup domain
netstat -ano (include PID)               # was -an, now -ano
netstat -anob (show process name)
Get-NetAdapter
Get-NetIPAddress
Test-NetConnection -ComputerName host
Test-NetConnection -ComputerName host -Port port
Invoke-WebRequest url
netsh interface show interface
netsh advfirewall show allprofiles
netsh advfirewall set allprofiles state on/off
Get-NetFirewallRule
nmap (external)
Get-NetTCPConnection                    # more detailed than netstat
Get-NetUDPEndpoint
Get-NetConnectionProfile
```

### 8. Network Forensics & Packet Capture (NEW)
```
netsh trace start capture=yes maxsize=500 filemode=circular
netsh trace stop
pktmon start --capture
pktmon stop
pktmon format C:\Windows\System32\PktMon.etl -o report.txt
Get-NetIPAddress | select IPAddress, InterfaceAlias
Test-NetConnection -DiagnoseRouting
```

### 9. Archives and Compression
```
Compress-Archive -Path files -DestinationPath archive.zip
Expand-Archive -Path archive.zip
tar -cf archive.tar files (Windows 10+)
tar -xf archive.tar
7z a archive.7z files (if 7-Zip)
7z x archive.7z
```

### 10. Text Processing (Extended)
```
findstr pattern files
findstr /s pattern dir
Select-String -Path files -Pattern pattern
echo text
(Get-Content filename) -replace 'string1', 'string2' | Set-Content filename
Compare-Object (Get-Content file1) (Get-Content file2)
(Get-Content filename).Count
Sort-Object
Get-Unique (PowerShell)
```

### 11. Disk Usage & Partition Management
```
diskpart (interactive)
fsutil volume diskfree drive:
Get-Disk
Get-Partition
Get-PhysicalDisk
Get-Volume
format drive: /fs:NTFS (CMD)
chkdsk drive: /f
```

### 12. System Information
```
systeminfo
date /t
time /t
whoami
Get-ComputerInfo
Get-CimInstance Win32_Processor
Get-CimInstance Win32_LogicalDisk
Get-CimInstance Win32_BIOS
```

### 13. System Monitoring and Performance
```
perfmon
resmon
Get-Counter
Get-Process | Sort-Object CPU -Descending
Get-Counter '\Processor(_Total)\% Processor Time'
typeperf "\Processor(_Total)\% Processor Time" -sc 5
```

### 14. Search and Find (Enhanced)
```
where filename
Get-Command commandname
Get-ChildItem -Path path -Recurse -Include pattern
Get-ChildItem -Path . -Recurse -Filter *.dll -ErrorAction SilentlyContinue
```

### 15. Package Installations
```
winget install pkgname
winget upgrade pkgname
winget remove pkgname
choco install pkgname
choco upgrade pkgname
choco uninstall pkgname
```

### 16. Python pip (unchanged)
```
pip install packagename
pip uninstall packagename
pip freeze > requirements.txt
pip install -r requirements.txt
pip list
```

### 17. Version Control (Git)
```
git init, clone, add, commit -m, status, pull, push
git branch, branch <name>, checkout
git log, diff
```

### 18. Environment Variables (Extended)
```
set
echo %VARIABLE%
set VARIABLE=value
Get-ChildItem Env:
$Env:VARIABLE = "value"
Remove-Item Env:VARIABLE
[Environment]::GetEnvironmentVariable("PATH", "Machine")  # system-wide
```

### 19. Job Scheduling
```
schtasks /query
schtasks /create /tn taskname /tr command
schtasks /delete /tn taskname
Get-ScheduledTask
New-ScheduledTask
Get-ScheduledTaskInfo -TaskName ...
Start-ScheduledTask
```

### 20. PowerShell Scripting (Extended)
```
#Comment
$variable = value
if (condition) {...}
foreach ($item in $collection) {...}
while (condition) {...}
function name {...}
param(...)
try { ... } catch { ... }
Get-Command -Module ...
```

### 21. PowerShell Remoting & Execution Policy (NEW)
```
Enable-PSRemoting -Force
Set-ExecutionPolicy RemoteSigned
Enter-PSSession -ComputerName remote
Invoke-Command -ComputerName remote -ScriptBlock { ... }
Get-PSSessionConfiguration
winrm get winrm/config
```

### 22. Windows Defender / Antivirus Commands (NEW)
```
Get-MpComputerStatus
Get-MpThreat
Update-MpSignature
Start-MpScan -ScanType QuickScan
MpCmdRun -Scan -ScanType 2  (full scan)
Get-MpPreference
```

### 23. Advanced Event Log & Audit Policy (Enhanced)
```
wevtutil el
wevtutil qe Security /f:text /c:10
Get-WinEvent -LogName Security
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4624}
Get-EventLog -LogName Application
auditpol /get /category:*              # NEW
auditpol /set /subcategory:"Logon" /success:enable /failure:enable
wevtutil qe Security /q:"*[System[(EventID=4625)]]" /f:text
```

### 24. Security-Specific Commands (Extended with AD, WMI)
```
net user
net user username password /add
net localgroup groupname username /add
Get-LocalUser
Get-LocalGroupMember groupname
net accounts  (password policy)
Get-ADUser -Filter * -Properties *     # if AD module
Search-ADAccount -LockedOut
Get-ADGroupMember "Domain Admins"
nltest /dclist:domain
klist
gpresult /h report.html
Get-WmiObject -Class Win32_StartupCommand
Get-CimInstance -ClassName Win32_Service | where StartMode -eq 'Auto'
Get-AppLockerPolicy
Set-AppLockerPolicy -PolicyObject ...
Test-AppLockerPolicy -Path file.exe
```

### 25. Malware Persistence Detection (NEW)
```
schtasks /query /fo LIST /v
wmic startup list
Get-CimInstance Win32_StartupCommand
reg query HKLM\Software\Microsoft\Windows\CurrentVersion\Run
reg query HKCU\Software\Microsoft\Windows\CurrentVersion\Run
Get-Service | where StartType -eq 'Automatic'
Get-WmiObject -Namespace root\subscription -Class __EventFilter
```

### 26. Binary Analysis & Digital Signature (NEW)
```
sigcheck -e -u -v suspicious.exe
Get-AuthenticodeSignature file.ps1
certutil -hashfile file.exe SHA256
strings.exe file.exe > strings.txt       # Sysinternals
dumpbin /headers file.exe (if VS tools)
```

### 27. Group Policy & Security Templates (NEW)
```
gpupdate /force
gpresult /h result.html
rsop.msc (GUI, start from run)
secedit /export /cfg secconfig.inf
secedit /configure /db secedit.sdb /cfg secconfig.inf
```

### 28. Windows Subsystem for Linux (WSL) (NEW)
```
wsl --list --verbose
wsl --exec <command>
wsl --import <Distro> <InstallLocation> <FileName>
wsl --terminate <Distro>
```

### 29. Logging and Auditing (Already covered in Event Log, but added convenience)
```
wevtutil el
wevtutil qe System /f:text
Get-WinEvent -LogName System
Get-EventLog -LogName Application
Get-WinEvent -MaxEvents 50 -LogName Security
```

### 30. Others (Terminal & Productivity)
```
command1 & command2
command1 && command2
history (PowerShell: Get-History)
cls
Start-Process -FilePath "wt"
code .  (VS Code if installed)
```

---
