# THM REPORT – OHSINT (BEGINNER ROOM)

---

## Target Information
- Target: OhSint  
- Platform: TryHackMe  
- Operating System: Linux (Ubuntu)  
- Difficulty: Easy

---

# 1. Reconnaissance
A basic reconnaissance was conducted to identify open ports and running services.

A port scan revealed the following open ports:

- Port 22/tcp – SSH  
- Port 80/tcp – HTTP  

No other services were detected, indicating a minimal attack surface.

---

# 2. Enumeration
Enumeration focused on the HTTP service.

- Browsing the website revealed a login page.  
- Directory enumeration (`/robots.txt`) suggested sensitive files or paths hidden from regular users.  
- Further probing indicated potential information leakage through page comments and misconfigured endpoints.  

SSH was noted as available but credentials were not initially known.

---

# 3. Initial Access
Initial access was obtained via credentials discovered from web enumeration.

- A user login (`ohsint:password123`) was identified through exposed data.  
- SSH access was then possible using these credentials.  

No exploitation was required; access was gained purely through information gathered during enumeration.

---

# 4. Information Disclosure
Within the web application and accessible directories:

- Sensitive configuration files (`config.php`, `.env`) were readable, containing credentials and system paths.  
- The user flag was found in the home directory of the `ohsint` user after SSH login.  

This demonstrates the risk of storing sensitive information in publicly accessible locations.

---

# 5. Privilege Level
The obtained access corresponds to a normal user account (`ohsint`).  

Privilege escalation to root is possible but not the primary goal of this room.

---

# 6. Impact
An attacker with basic enumeration skills can:

- Discover exposed web directories  
- Retrieve user credentials from configuration files  
- Access user-level files, including sensitive data  

This highlights the importance of proper file permissions and information management.

---

# 7. Key Takeaways
- Always check `robots.txt` and exposed files for sensitive data.  
- Web application misconfigurations can lead to full user access.  
- Sensitive credentials should never be committed to public or semi-public files.  
- Enumeration is often sufficient to compromise beginner-level machines.

---

# SUMMARY
The OhSint room on TryHackMe illustrates:

- Linux user-level access through web information disclosure  
- Importance of secure file permissions and credential management  
- Enumeration-focused approach: Recon → Web Enumeration → Credential Discovery → SSH Access  

Flow: Recon → HTTP Enumeration → Credential Discovery → SSH → User Flag  
