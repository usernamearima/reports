# HTB REPORT – FAWN (BEGINNER LAB)

---

## Target Information
- Target: Fawn
- Platform: Hack The Box
- Operating System: Linux
- Difficulty: Very Easy

---

# 1. Reconnaissance
A basic port scan was performed against the target system.
The scan identified a single relevant open service:

- Port 21/tcp – FTP

No other significant network services were discovered.

---

# 2. Enumeration
Enumeration of the FTP service revealed that anonymous login was enabled.
This configuration allows anyone to authenticate to the FTP server without valid credentials.

Anonymous FTP access is a common and serious security misconfiguration.

---

# 3. Initial Access
Initial access was obtained by logging into the FTP service using the anonymous account:

ftp <target_ip>
Name: anonymous
Password: anonymous

Access to the FTP directory and its contents was successfully achieved.

---

# 4. Information Disclosure
While browsing the FTP directory, a file containing the user flag was discovered.
The file was readable without any form of authentication or authorization control.

This resulted in direct exposure of sensitive information.

---

# 5. Privilege Level
Access in this lab is limited to the FTP user context.
No privilege escalation to root is required or possible, as per the intended design of the box.

---

# 6. Impact
An unauthenticated attacker can access files hosted on the FTP server.
This misconfiguration leads to information disclosure and may expose sensitive data to the public.

---

# 7. Key Takeaway
- Anonymous FTP access is a critical security flaw
- Data exposure can occur even without gaining a shell
- Proper service enumeration is essential during the early stages of a penetration test
- Misconfigurations alone can result in real security incidents

---

# SUMMARY
The FAWN machine teaches the basics of service enumeration and misconfiguration awareness:

- Lack of authentication leads directly to data exposure
- Not every successful attack results in shell access
- Information disclosure is a valid and serious vulnerability

Flow: Recon → FTP Enumeration → Anonymous Login → Data Exposure
