# 🛠️ AutoSpoof — Offensive Cybersecurity Toolkit

AutoSpoof is an automated offensive cybersecurity tool designed for ethical hacking and penetration testing. It performs network scanning, ARP spoofing, DNS spoofing, and HTTP website cloning to simulate Man-in-the-Middle (MITM) attacks for educational and research purposes.

> ⚠️ Disclaimer: This tool is for educational and authorized penetration tests only. Always obtain permission before use. Misuse may lead to legal consequences.

## 📌 Features

- 🔍 Network Scanner: Discovers live hosts and their MAC/IP addresses.
- 🕵️‍♂️ ARP Spoofer: Redirects network traffic through your machine.
- 🌐 DNS Spoofer: Intercepts and modifies DNS responses.
- 🪞 Website Cloner: Automatically clones specified HTTP websites.
- 🔁 Auto Mode: Chains all modules for full attack automation.

## 🔧 Installation

1. Clone this repository:
   ```
   git clone https://github.com/SC0RPI0-V/Auto-spoof.git
   cd Auto-spoof
   ```
2. Install dependencies:
   ```
   pip install scapy colorama requests beautifulsoup4 netfilterqueue
   ```
3. Grant root privileges for packet operations:
   ```bash
   sudo bash
   ```

## 🚀 Usage

- Run the full automated chain:
  ```bash
  sudo python3 auto_spoof.py
  ```
- Or run modules individually:
  - Network Scanner:
    ```bash
    sudo python3 network_scanner.py
    ```
  - ARP Spoofer:
    ```bash
    sudo python3 arp_spoofer.py -t <target_ip> -g <gateway_ip>
    ```
  - DNS Spoofer:
    ```bash
    sudo python3 dns_spoofer.py
    ```
  - Website Cloner:
    ```bash
    sudo python3 clone_sites.py
    ```

## 📚 Project Status

- ✅ Core modules (scanner, ARP/DNS spoofing, HTTP clone) tested.
- 🔄 Planned: HTTPS downgrade detection.
- 🚧 Future: Real-time monitoring UI.


## 🛠️ Troubleshooting

To enable port forwarding and NFQUEUE for DNS interception:

1. Enable IP forwarding:
   ```bash
   echo 1 > /proc/sys/net/ipv4/ip_forward
   ```

2. Redirect packets to NFQUEUE for processing:
   ```bash
   iptables -I FORWARD -j NFQUEUE --queue-num 1
   iptables -I OUTPUT -p udp --dport 53 -j NFQUEUE --queue-num 1
   iptables -I INPUT -p udp --sport 53 -j NFQUEUE --queue-num 1
   ```

3. Allow forwarding on your network interface (`yourinterface`):
   ```bash
   iptables -A FORWARD -i yourinterface -j ACCEPT
   iptables -A FORWARD -o yourinterface -j ACCEPT
   ```


