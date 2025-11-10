# 🧪 Cyber Security Lab Exercise

This project sets up a lightweight, containerized cyber security lab using Docker Compose.

---

## ⚙️ Prerequisites
- [podman - Installation](https://podman.io/docs/installation)
- [podman Compose](https://podman-desktop.io/docs/compose/setting-up-compose)

### 📡 Network: `cyber-lab` (Docker bridge network)

All containers are connected to a custom Docker bridge network called `cyber-lab`, allowing internal communication between services.

```bash
    podman network create \  --driver=bridge \  --subnet=10.28.0.0/24 \  --gateway=10.28.0.1 \  cyber-lab
```
### Verify Cybersecurity Lab Network
```bash
    podman network inspect cyber-lab
        or
    podman network ls
```

---

## Pre‑lab checklist (student must confirm)

<label><input type="checkbox" id="task1"> I have read & accepted the Safety & Acceptable‑Use Guidelines. </lable>

<label><input type="checkbox" id="task2"> I will only target dvwa and juice-shop inside the lab network.</lable>

---

# - [Exercise 01](Exercise01.md) 


---

**Note:** 
*Important safety:
- Do not expose lab services to your home network unless instructed.
- Do NOT publish container ports to your home network during coursework.
- Only attack containers you started yourself.*

*You must read & agree before starting the lab* [Safety-Guidlines](./Lab/Safety-Guidelines.md)