# HTB REPORT – DANCING (BEGINNER LAB)

---

## Target Information
- Target: Dancing
- Platform: Hack The Box
- Operating System: Windows
- Difficulty: Very Easy

---

# 1. Reconnaissance
An initial port scan was conducted against the target machine to identify exposed services.

The scan revealed one notable open port:

- Port 445/tcp – SMB (Server Message Block)

No additional attack surface was identified during the reconnaissance phase.

---

# 2. Enumeration
Further enumeration focused on the SMB service.

Anonymous (guest) access to the SMB shares was enabled.
Listing available shares revealed a publicly accessible share containing files.

This represents a common Windows misconfiguration where SMB allows unauthenticated access.

---

# 3. Initial Access
Initial access was achieved by connecting to the SMB service using a guest session.

The SMB client was used to list and access shared resources without providing credentials.

Access to the shared directory was successfully obtained.

---

# 4. Information Disclosure
Inside the SMB share, a text file containing the user flag was discovered.

The file was readable by any unauthenticated user, leading to direct disclosure of sensitive information.

No exploitation beyond basic enumeration was required.

---

# 5. Privilege Level
The access level is limited to an unauthenticated SMB guest user.

Privilege escalation is not required or intended for this machine.

---

# 6. Impact
An attacker can anonymously access SMB shares and read sensitive files.

This can result in data leakage and may expose internal documents or credentials in real-world environments.

---

# 7. Key Takeaway
- Anonymous SMB access is a serious security misconfiguration
- Sensitive files should never be exposed through guest shares
- Basic enumeration can lead directly to success
- Windows services require strict access control

---

# SUMMARY
The DANCING machine demonstrates fundamental Windows enumeration concepts:

- SMB misconfiguration leads to information disclosure
- No credentials or exploitation techniques are required
- Enumeration alone can compromise confidentiality

Flow: Recon → SMB Enumeration → Guest Access → Data Exposure
