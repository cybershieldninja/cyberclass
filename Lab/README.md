Welcome to the lab!

1) Start lab:
   <!-- docker-compose up --build -d -->
```bash
    podman compose --file .\docker-compose.yml up --detach
```   

2) Enter attacker:
   <!-- docker exec -it lab_attacker bash -->
```bash
    podman exec -it lab_attacker bash
```     

3) Test connectivity:
```bash
   ping dvwa
   curl http://dvwa/
```

4) Example reconnaissance commands (inside attacker):
```bash
   nmap -sC -sV dvwa
   gobuster dir -u http://dvwa/ -w /opt/wordlists/common.txt
   sqlmap -u "http://dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --batch --dbs
```   

5) When done:
   <!-- docker-compose down -->
```bash
    podman compose -f .\docker-compose.yml down
```   

**Note:** 

*Important safety:*
- *Do not expose lab services to your home network unless instructed.*
- *Do NOT publish container ports to your home network during coursework.*
- *Only attack containers you started yourself.*

*You must Read & agree before starting the lab* [Safety-Guidlines](./Safety-Guidelines.md)