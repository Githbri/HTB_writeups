# Meow - Hack The Box

## Reconnaissance

- VPN connection established using OpenVPN
- Target reachable via ping
- Nmap scan performed:

```bash
nmap -sV <target_IP>
```

- Port 23 (Telnet) identified as open

## Exploitation

- Connected to target using Telnet:

```bash
telnet <target_IP>
```

- Tried common usernames:
  - admin
  - administrator
  - root

- Successful login with user: **root** (no password)

## Post-Exploitation

- Listed files using:

```bash
ls
```

- Found `flag.txt`
- Retrieved flag:

```bash
cat flag.txt
```

## What I Learned

- Importance of port scanning with Nmap
- Basic service enumeration
- Weak authentication vulnerabilities
- Telnet security weaknesses
