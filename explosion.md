# Explosion - Hack The Box

## Reconnaissance

- VPN connection established using OpenVPN

- Nmap scan performed:

```bash
nmap -sC -sV <target_IP>
```

### Result

- Port 3389 open → RDP (Remote Desktop Protocol)

---

## Enumeration

- RDP service identified
- No additional authentication details required initially

---

## Exploitation

- Connect using xfreerdp:

```bash
xfreerdp /v:<target_IP>
```

- If needed, specify Administrator user:

```bash
xfreerdp /v:<target_IP> /u:Administrator /p: /cert:ignore
```

- No password required (misconfiguration)

---

## Post-Exploitation

- Successful remote desktop session established
- Access to Windows environment obtained

- Locate the flag on the desktop
- Open the file to retrieve the flag

---

## Vulnerability

The RDP service allows login without a password.

---

## Impact

- Full remote access to the system
- Complete compromise of the machine
- Potential lateral movement inside the network

---

## Remediation

- Enforce strong authentication (password / MFA)
- Disable empty passwords
- Restrict RDP access (VPN / firewall rules)
- Monitor login attempts and sessions

---

## Skills Demonstrated

- Service enumeration with Nmap
- RDP service identification
- Remote access using xfreerdp
- Exploitation of weak authentication
