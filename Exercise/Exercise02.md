### **Module 2: Network Fundamentals for Cybersecurity — Beginner Lab Exercises**

**Goal:** Teach basic network concepts, such as IP addressing, subnetting, port scanning, and network monitoring, with practical exercises. These exercises will help students understand how to explore and secure a network.

---

### **Exercise 1: Host Discovery with Nmap**

**Goal:** Discover live hosts and open ports within the lab network.

**Prompt:**
“From the attacker container, scan the lab network for live hosts and open ports. What hosts are alive, and which ports are open on the DVWA container?”

**Hints:**

* Use `nmap -sn` to discover live hosts (ping scan).
* Use `nmap -sC -sV` to discover open ports and services running on `dvwa`.
* Alternatively, use `nmap -p-` to scan all ports.
* After scanning, check for common services like HTTP (port 80), HTTPS (port 443), and SSH (port 22).

**Example command:**

```bash
nmap -sn 192.168.1.0/24  # Scan for live hosts in the subnet
nmap -sC -sV dvwa  # Scan DVWA for open ports and service versions
```

**Question to Ask Students:**

* Paste the command you used and the output showing the live hosts and open ports.
* Which service is running on port 80? What other ports are open?

---

### **Exercise 2: Network Interface and IP Addressing**

**Goal:** Understand the network interfaces and IP address configuration within the lab environment.

**Prompt:**
“Identify the IP address of the attacker container and check the network interfaces. What IP addresses are assigned to the attacker container and the DVWA container?”

**Hints:**

* Use the `ip a` or `ifconfig` command to list network interfaces and their assigned IPs.
* The attacker container and the DVWA container should have IP addresses within the same subnet.

**Example command:**

```bash
ip a  # Display network interfaces and IP addresses
```

**Question to Ask Students:**

* What is the IP address of your attacker container?
* What IP address is assigned to the DVWA container?

---

### **Exercise 3: Port Scanning and Service Discovery (Nmap)**

**Goal:** Perform a deeper port scan and identify the services running on the DVWA container.

**Prompt:**
“Use `nmap` to scan for open ports and identify the services running on the DVWA container. What ports are open, and what services can you identify?”

**Hints:**

* Use the `nmap -sC -sV` command for a safe and detailed scan.
* The `-sC` option runs default NSE scripts, which can reveal more information about the services.
* The `-sV` flag attempts to determine the version of the services running.

**Example command:**

```bash
nmap -sC -sV dvwa  # Scan for open ports and identify service versions
```

**Question to Ask Students:**

* Paste the output of your `nmap` scan showing the open ports and their corresponding services.
* What services are running on ports 80, 443, and any other open ports?

---

### **Exercise 4: Traffic Analysis with Tcpdump**

**Goal:** Capture network traffic between the attacker and the DVWA container to analyze HTTP packets.

**Prompt:**
“Use `tcpdump` to capture HTTP traffic between the attacker and the DVWA container. What can you observe in the packet capture?”

**Hints:**

* Use `tcpdump` to capture traffic on port 80 (HTTP).
* Use the `-i eth0` option to specify the network interface.
* You can capture only a few packets for easier analysis, e.g., by using the `-c` option to limit the number of captured packets.

**Example command:**

```bash
tcpdump -i eth0 port 80 -c 10  # Capture 10 HTTP packets
```

**Question to Ask Students:**

* Paste the first few lines of the `tcpdump` output.
* What type of packets can you observe (e.g., SYN, ACK, HTTP requests)?

---

### **Exercise 5: DNS Lookup and Reverse DNS**

**Goal:** Use DNS and WHOIS to gather information about the target system.

**Prompt:**
“Perform a DNS lookup and a reverse DNS lookup for the DVWA container. What DNS records can you retrieve?”

**Hints:**

* Use `dig` to query DNS records for the DVWA container.
* Use `whois` to gather information about domain registration (useful if DVWA or any other target were on a public domain).

**Example command:**

```bash
dig dvwa  # Perform a DNS query for DVWA
whois dvwa  # Perform a WHOIS query
```

**Question to Ask Students:**

* Paste the `dig` and `whois` output.
* What DNS record (A record) did you get for `dvwa`?
* What information did you find in the `whois` output?

---

### **Exercise 6: Basic Troubleshooting with Ping and Traceroute**

**Goal:** Troubleshoot network connectivity between containers.

**Prompt:**
“Use `ping` and `traceroute` to check the network connectivity between your attacker container and the DVWA container. What is the network path, and can you confirm connectivity?”

**Hints:**

* `ping` will show if the target is reachable.
* `traceroute` will show the network path between the attacker and the DVWA container, including any intermediate hops.

**Example command:**

```bash
ping -c 4 dvwa  # Ping DVWA to check connectivity
traceroute dvwa  # Trace the route to DVWA
```

**Question to Ask Students:**

* Paste the output from `ping` and `traceroute`.
* Do you see any unusual hops or delays in the traceroute? What does this tell you about the network path?

---

### **Exercise 7: Subnetting Practice**

**Goal:** Understand subnetting and calculate IP ranges.

**Prompt:**
“Given the network `192.168.1.0/24`, what are the valid IP addresses and the broadcast address? Can you calculate the subnet mask and divide the network into two smaller subnets?”

**Hints:**

* A `/24` network has 256 IP addresses, with the first address reserved as the network address and the last address reserved as the broadcast address.
* To divide the network into two smaller subnets, reduce the subnet size to `/25` or `/26`.

**Example solution (not direct answer):**

* Network address: `192.168.1.0`
* Broadcast address: `192.168.1.255`
* Valid IPs: `192.168.1.1 - 192.168.1.254`

**Question to Ask Students:**

* What are the valid IP address ranges for the subnets you’ve created?
* What is the broadcast address for the network `192.168.1.0/24`?

---

### **Exercise 8: Investigating ARP and Local Network Traffic**

**Goal:** Investigate ARP and local network traffic to understand how devices communicate within a subnet.

**Prompt:**
“Use `arp-scan` to scan for devices within your local network. What other devices are visible in the local subnet?”

**Hints:**

* `arp-scan` sends ARP requests to all devices on the local network to gather their MAC addresses and IP addresses.
* The local network subnet can be derived from the IP address of your attacker container.

**Example command:**

```bash
arp-scan 192.168.1.0/24  # Scan the local subnet for devices
```

**Question to Ask Students:**

* Paste the output from `arp-scan`.
* What devices are on the local network, and what are their MAC addresses?

---

### **Final Write-up for Each Exercise**

For every exercise, require students to submit:

1. **One-paragraph findings report**: This helps students summarize their learnings and reinforce key concepts.
2. **Step-by-step log**: This log should include the commands they used, what the outputs were, and their interpretation. This builds good documentation habits.

---


---

**Quick Troubleshooting:**

* **No output in `tcpdump`**: Ensure that the correct interface (`eth0`) is being used.
* **Unable to ping DVWA**: Check if the container is running and the network bridge is up. Make sure no firewall is blocking ICMP.
* **Slow or incomplete `nmap` scans**: Limit the ports scanned or reduce the scan intensity with `-T3` or `-T2`.

