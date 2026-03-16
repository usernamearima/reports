# HTB INSANE – WINDOWS (STEP‑BY‑STEP METHODOLOGY)

## 1. Reconnaissance (Target Model)

First understand what the machine actually is:

- A single host or part of a larger infrastructure  
- Standalone Windows or Active Directory environment  
- Web application with backend services  
- Custom service or internal application  

The goal is to **map the architecture and role of the system**, not to immediately search for exploits.

---

## 2. Attack Surface Identification

Identify all possible entry points:

- Web applications
- APIs
- Custom ports/services
- SMB / RPC
- WinRM
- Active Directory interfaces
- Downloadable files
- Binaries
- Backups
- Configuration files

The key question:

> **Where can I gain access logically, not through brute force?**

---

## 3. Manual Enumeration

Deeply analyze every discovered entry point:

- Application behavior
- Authentication flows
- Permission models
- Logical flaws
- Service versions
- Unusual responses
- Differences between users
- Edge cases

This phase typically consumes **most of the time during an Insane box**.

---

## 4. Web / Application Logic / API (If Present)

Analyze:

- Authentication mechanisms
- Session management
- Tokens and cookies
- Roles and permission boundaries
- Request sequencing
- Race conditions
- SSRF chains
- IDOR
- Broken access control

Do **not rely on automated scanning**.  
Think like the backend developer and understand how the system processes requests.

---

## 5. Reverse Engineering (Often Required)

If the challenge provides:

- `.exe`
- `.dll`
- `.NET` applications
- Windows services

Analyze them using reverse engineering tools.

Focus on:

- Program logic
- Hardcoded secrets
- Authentication algorithms
- Custom protocols
- Input handling vulnerabilities

---

## 6. Dynamic Analysis

Execute and observe the program in runtime.

Monitor:

- Processes
- File activity
- Registry changes
- IPC mechanisms
- Network traffic

The goal is to understand **what the program actually does**, not just what the code suggests.

---

## 7. Vulnerability Chaining

Combine smaller weaknesses into a complete attack path.

Typical structure: minor flaw → larger logic flaw → system access

**Insane machines almost always require chaining multiple issues**, not a single exploit.

---

## 8. Initial Access

Gain the first level of control over the system:

- User shell
- Service account access
- Web execution context

This is **only the starting point**, not the objective.

---

## 9. Privilege Escalation (Manual)

Analyze potential escalation vectors:

- Misconfigured services
- Scheduled tasks
- Registry permissions
- Token privileges
- DLL hijacking opportunities
- Misconfigurations
- Credential reuse

Enumeration tools may provide hints, but **manual analysis drives the decision process**.

---

## 10. Lateral Movement / Active Directory (If Applicable)

Investigate:

- Trust relationships
- User privileges
- Delegation settings
- Token usage
- Access to other hosts

Approach the environment **like a system administrator**, not like an automated scanner.

---

## 11. Access Stabilization

Ensure you fully understand **why the access works**.

Avoid blind persistence.  
The objective is **knowledge of the attack vector**, not leaving backdoors.

---

## 12. Documentation and Verification

Document the entire attack path as **one clear logical chain**.

If you cannot explain the compromise **without referencing tools or commands**, return to earlier stages and reassess the analysis.

---

# Core Principle

If you become stuck, return to **Attack Surface Identification (Step 2)** or **Manual Enumeration (Step 3)**.

On **Insane difficulty**, progress is rarely blocked by a missing exploit.

It is almost always blocked by **insufficient analysis or incomplete understanding of the system**.
