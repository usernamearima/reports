# HTB REPORT – MEOW (BEGINNER LAB)

---

## Target Information
- **Target:** Meow  
- **Platform:** Hack The Box  
- **Operating System:** Linux  
- **Difficulty:** Very Easy  

---

1. Reconnaissance
A basic port scan was performed against the target system.  
The scan revealed a single open service:

- **Port 23/tcp – Telnet**

2. Enumeration
Further enumeration of the Telnet service showed that it was **misconfigured**.  
The service allowed connections **without proper authentication**, enabling users to log in without providing valid credentials.

This indicates a critical security misconfiguration.

3. Initial Access
Initial access was obtained by connecting directly to the Telnet service:

```bash
telnet <target_ip>
```
4. Privilege Level
The obtained shell was running with root privileges.
No privilege escalation techniques were required, as the service provided full administrative access by default.
```bash 
id
uid=0(root) gid=0(root) groups=0(root)
```
5. Impact
This vulnerability results in a complete system compromise.
An attacker can gain full control over the machine without using exploits, malware, or advanced techniques — solely due to improper configuration of a remote access service.

6. Key Takeaway
- Telnet transmits data in plaintext and should never be exposed to untrusted networks.
- Remote access services must always enforce strong authentication.
- Misconfiguration can be as dangerous as software vulnerabilities.
- Even very simple security oversights can lead to total compromise.

---

SUMMARY

MEOW pokazuje absolutne podstawy bezpieczeństwa:
– brak uwierzytelniania = natychmiastowy dostęp
– nie każdy atak wymaga exploita
– błędna konfiguracja jest często najgroźniejszą podatnością

Flow: Recon → Telnet → Brak auth → Root access.
