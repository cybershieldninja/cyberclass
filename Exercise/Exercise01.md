## Materials & tools (available inside attacker)

nmap, curl, gobuster (or nikto), sqlmap (installed but not used in this module), tcpdump (optional).

Wordlist (optional): /opt/wordlists/common.txt

---

# Module 1 — Recon & Surface Discovery (Beginner)

    Goal: Teach safe reconnaissance and basic web surface discovery using nmap, curl, gobuster (or nikto), and interpreting results to pick next steps. Students will perform only non‑intrusive discovery and report findings.

    Learning objectives

    - Run basic host discovery and port scans safely within the lab.

    - Identify running web services and extract HTTP banners/headers.

    - Find likely web entry points (hidden directories / endpoints).

    - Record commands and short findings; propose one next test per target.
    

Exercise 1 — Recon (nmap)

    Goal: Discover live hosts and open ports in the lab network.

    Prompt to students: “From the attacker container, list active hosts and the top 20 TCP ports for the DVWA container. What ports are open and which services might be running?”

    Hints: nmap -sC -sV dvwa or nmap -p- dvwa. Ask them to interpret service banners.

Exercise 2 — Web content discovery (gobuster)

    Goal: Find hidden directories or files on DVWA.

    Prompt: “Use gobuster or nikto to find likely attack surfaces (login pages, upload endpoints).”

    Starter hint: gobuster dir -u http://dvwa/ -w /usr/share/wordlists/dirb/common.txt (students may need to install /point to a wordlist).

Exercise 3 — SQL Injection (DVWA low)

    Goal: Practise SQLi on DVWA at the low security setting.

    Prompt: “Use the DVWA SQL injection page. Try to extract a known username or confirm vulnerability using sqlmap or manual payloads.”

    Hints: Change DVWA security to low (within app). Use sqlmap -u "http://dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --dbs --batch.

Exercise 4 — XSS (stored/reflected)

    Goal: Identify and exploit a reflected XSS on DVWA or Juice Shop.

    Prompt: “Find a form or parameter that echoes input into the page. Can you craft a simple <script>alert(1)</script> payload that executes?”

    Hints: Use browser devtools or curl to submit payloads from attacker container’s curl.

Exercise 5 — Password cracking (john)

    Goal: Crack a small password hash list.

    Prompt: “One of the web apps stores password hashes. Extract a sample hash (provided in class) and use john to attempt cracking with a small wordlist.”

    Hints: john --wordlist=/usr/share/wordlists/rockyou.txt hashfile.

For each exercise, require students to write a one-paragraph findings report and a step-by-step log of commands they ran. That reinforces learning.


**Note:** 
*Important safety:
- Do not expose lab services to your home network unless instructed.
- Do NOT publish container ports to your home network during coursework.
- Only attack containers you started yourself.*

*You must Read & agree before starting the lab* [Safety-Guidlines](../Lab/Safety-Guidelines.md)