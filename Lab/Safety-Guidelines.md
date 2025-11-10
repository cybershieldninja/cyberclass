# Safety & Acceptable‑Use Guidelines

Read this carefully and accept it before participating in any lab exercise. 
<!-- Violation may result in removal from the course. -->


1) **Core rule (no exceptions)**

    You may only attack systems you have explicit authorization to attack. For this class that means: only containers started from the provided docker-compose.yml (or images explicitly approved by the instructor). Do not scan, probe, or attack any external IPs, university networks, cloud services, classmates’ machines, or any devices you do not own and have written permission to test.

2)  **Legal & ethical obligations**

    All activity is subject to local laws and your institution’s acceptable‑use policy. Ignorance is not a defense.
    Never attempt to exploit vulnerabilities on networks/hosts outside this lab.
    If you find an unexpected vulnerability that exposes other students’ data or the instructor’s host, stop immediately and report it to the instructor (see contact below). Do not attempt to exploit or publicize it.

3) **Isolation & network rules**

    The lab runs on an internal *bridge* network created by the docker-compose.yml. Targets are reachable only from the attacker container (hostnames: dvwa, juice-shop, etc.).

    Do not add ports: mappings to expose lab targets to your home or institutional network unless explicitly instructed.

    Do not change network settings that would attach containers to your host LAN or use host networking (*network_mode: "host"*).    

4) System & resource rules

    Only run the attacker plus one target if your machine is constrained (8 GB / 50 GB). Stop unused services with podman compose stop <service>.

    Do not run containers with --privileged or --cap-add=ALL unless instructor authorizes it for a specific lab step.

5) Prohibited actions (examples)

    Attacking any IP, domain, or service not created/provided by this lab.

    Using this environment to host or distribute malicious code (malware, crypto‑miners, botnets).

    Attempting to pivot from lab containers to the host machine or other devices on your network.

    Publicly posting exploits, credentials, screen captures, or data from the lab that could let others reproduce attacks outside the lab.

6) Safe data handling & privacy

    Treat lab credentials and any sample user data as sensitive. Do not publish them.

    If you collect logs, captures, or screenshots for assignments, sanitize or redact any real hostnames/IPs or personal data before sharing.    

7) Short Dos & Don’ts (one‑line memory aids)

    - Do: ask if unsure; stop and report unexpected behavior.

    - Don’t: expose lab services to the internet or your home LAN.

    - Do: run tools from inside the attacker container (not from your host).

    - Don’t: store or publish real credentials, personal data, or exploit scripts.

8) Consent statement (students must agree before starting)

    **I have read and understand the Cyber Lab Safety & Acceptable‑Use Guidelines. I agree to only target lab containers I started or the images explicitly approved by the instructor. I will not attack external systems and will report any unexpected security exposure immediately.**    