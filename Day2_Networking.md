📘 Learn important Kali Linux commands for networking, ethical hacking, and cybersecurity

| Command       | Purpose                            |
| ------------- | ---------------------------------- |
| `ifconfig`    | Show IP and network interfaces     |
| `ip`          | Modern network info tool           |
| `iwconfig`    | Show wireless info                 |
| `ping`        | Test connection to a host          |
| `traceroute`  | Show path to host                  |
| `mtr`         | Live traceroute + packet loss      |
| `host`        | DNS lookup                         |
| `dig`         | Advanced DNS lookup                |
| `whois`       | Domain ownership info              |
| `arp-scan`    | Scan local network for devices     |
| `nmap`        | Port and service scanner           |
| `tcpdump`     | CLI packet sniffer                 |
| `wireshark`   | GUI packet sniffer                 |
| `netstat`     | Show network connections           |
| `ss`          | Modern netstat                     |
| `route`       | Show/change routing table          |
| `ssh`         | Remote secure login                |
| `scp`         | Secure file copy                   |
| `wget`        | Download files from URLs           |
| `curl`        | Talk to web APIs or download pages |
| `airmon-ng`   | Start monitor mode for Wi-Fi       |
| `airodump-ng` | Scan Wi-Fi networks/devices        |


### 🖥️ Basic Network Info 
🔹 ifconfig - Shows your computer’s IP address and network details.

🔹 ip - Modern version of ifconfig. Shows IP, routes, links.
    ip addr
    ip link
    ip route
    
🔹 iwconfig - Shows your wireless (Wi-Fi) settings.
    iwconfig

    
 ### 🛰️ Testing the Network
 🔹 ping - Check if another device is alive.
     ping google.com
     
 🔹 traceroute - See how your data travels through the internet.
     traceroute google.com
     
 🔹 mtr - Live traceroute with packet loss info.
     mtr google.com


  ### 🌍 Domain Tools (DNS)
  🔹 host - Find the IP address of a domain.
      host example.com
      
  🔹 dig - Get deep info about domain DNS.
      dig example.com
      
  🔹 whois - Find domain owner and registration details.
      whois example.com


   ### 🔍 Network Scanning Tools
  🔹 arp-scan - Find all devices in your local network.
      sudo arp-scan 192.168.1.0/24
      
  🔹 nmap - Scan open ports, services, and OS on targets.
      nmap -A 192.168.1.1
      nmap -sn 192.168.1.0/24
      
  🔹 tcpdump - Capture and analyze network packets in terminal.
      sudo tcpdump -i wlan0
      
  🔹 wireshark - GUI tool to capture and view network traffic (packets).
      wireshark

      
   ### 🧭 Routing and Connections
  🔹 netstat - Show connections and listening ports.
      netstat -tulnp
      
  🔹 ss - Modern version of netstat (faster and better).
      ss -tulpn
      
  🔹 route - Show or manage the system routing table.
      route -n
      ip route show


   ### 🔐 Remote Access & File Transfer
   🔹 ssh - Securely connect to another machine (remote login).
       ssh user@192.168.1.10
       
   🔹 scp - Securely copy files to/from another machine.
       scp file.txt user@192.168.1.10:/home/user/
       scp user@192.168.1.10:/home/user/file.txt .


   ### 🌐 Downloading Files
   🔹 wget - Download files from the internet.
       wget https://example.com/file.zip
       wget -O custom.txt https://example.com/file.txt

   🔹 curl - Talk to websites and download or send data.
       curl https://example.com
       curl -O https://example.com/file.zip
       curl -I https://example.com
       curl -d "name=value" -X POST https://example.com


   ### 📶 Wireless Hacking Tools
   🔹 airmon-ng - Put your Wi-Fi card into monitor mode (to spy on traffic).
      sudo airmon-ng start wlan0
      sudo airmon-ng stop wlan0mon
      sudo airmon-ng check kill

   🔹 airodump-ng - Scan for nearby Wi-Fi networks and devices.
      sudo airodump-ng wlan0mon
      sudo airodump-ng --bssid <BSSID> -c <channel> wlan0mon

 

## 📡 1. `ping host`

**What it does:**  
Sends packets to a remote host to see if it's reachable.

**Example:**
```bash
ping google.com
```

💡 You'll see replies if the internet is working and the site is reachable.

---

## 🧾 2. `whois domain`

**What it does:**  
Shows information about who owns a domain.

**Example:**
```bash
whois example.com
```

📋 You'll get the domain's owner, registration date, and expiry info.

---

## 📥 3. `dig domain`

**What it does:**  
Fetches DNS records like IP addresses for a domain.

**Example:**
```bash
dig google.com
```

🔎 Shows IP addresses, DNS servers, and more.

---

## 🧠 4. `nslookup domain`

**What it does:**  
Another way to find DNS details about a domain.

**Example:**
```bash
nslookup openai.com
```

---

## 🌐 5. `ss`

**What it does:**  
Shows open network sockets (like who is connected to what).

**Example:**
```bash
ss -tuln
```

📈 See open TCP/UDP ports on your computer.

---

## 🔐 6. `ssh user@host`

**What it does:**  
Lets you log in to another computer remotely and securely.

**Example:**
```bash
ssh student@192.168.1.10
```

🔐 You need a username and password or SSH key.

---

## 📤 7. `scp source destination`

**What it does:**  
Securely copy files between computers.

**Example:**
```bash
scp myfile.txt user@192.168.1.10:/home/user/
```

🔄 Copies `myfile.txt` to the remote computer.

---

## 🌍 8. `wget url`

**What it does:**  
Downloads files from the web.

**Example:**
```bash
wget https://example.com/file.zip
```

💾 Saves `file.zip` to your computer.

---

## 🌐 9. `curl url`

**What it does:**  
Sends web requests and shows the response (used in APIs, websites, etc).

**Example:**
```bash
curl https://api.github.com
```

📬 Useful for testing APIs.

---

## 🛣️ 10. `traceroute domain`

**What it does:**  
Shows the path your internet traffic takes to reach a website.

**Example:**
```bash
traceroute google.com
```

🛤️ Good for seeing where delays happen in the network.

---

## 📶 11. `mtr domain`

**What it does:**  
Combines `ping` and `traceroute` to diagnose network problems in real-time.

**Example:**
```bash
mtr google.com
```

📊 Keeps refreshing to show changing network status.

---

## 🕵️ 12. `nmap`

**What it does:**  
Scans networks for open ports and services.

**Example:**
```bash
nmap 192.168.1.1
```

🛡️ Used for network security checks.

---

## 🖧 13. `ip addr`

**What it does:**  
Shows IP addresses and network details.

**Example:**
```bash
ip addr
```

🧾 Replaces the older `ifconfig`.

---

## 🧷 14. `ip link`

**What it does:**  
Shows and changes network interface status.

**Example:**
```bash
ip link set eth0 down
```

🛠️ Use it to turn off/on network cards.

---

## 🗺️ 15. `ip route`

**What it does:**  
Shows routing table (how your computer sends traffic).

**Example:**
```bash
ip route
```

🛤️ Shows default gateways, routing rules, etc.

---

## 📸 16. `tcpdump -i interface`

**What it does:**  
Captures packets (network data) going in and out of your system.

**Example:**
```bash
tcpdump -i eth0
```

🧪 Great for debugging traffic issues (text-based).

---

## 🧪 17. `wireshark`

**What it does:**  
GUI tool for analyzing network packets.

🖥️ Just run `wireshark` (if installed), and select an interface to start.

🧠 More powerful and visual than `tcpdump`.

---

## 🔥 18. `ufw status`

**What it does:**  
Shows current firewall rules (if `ufw` is used).

**Example:**
```bash
sudo ufw status
```

🛡️ Easy firewall manager for Ubuntu-based systems.

---

## 🔐 19. `iptables -L`

**What it does:**  
Lists firewall rules using the iptables system.

**Example:**
```bash
sudo iptables -L
```

🧱 Shows how your firewall is blocking/allowing traffic.

---

## 🧪 20. `nc host port` (Netcat)

**What it does:**  
Tests connections or sets up mini servers.

**Example (check if port is open):**
```bash
nc -zv google.com 80
```

**Example (create a simple chat server):**
```bash
nc -l 1234
```



