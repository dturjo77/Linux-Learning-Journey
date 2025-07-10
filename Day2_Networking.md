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

 





