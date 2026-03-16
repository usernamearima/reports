# HTB INSANE – KALI / LINUX (STEP‑BY‑STEP METHODOLOGY)

## 1. Reconnaissance (Understanding the Target)

First determine what the machine actually is:

- Standalone Linux host
- Container
- Part of a larger infrastructure
- Backend behind a web application
- Custom service

The goal is to **understand the logical architecture of the system**, not to immediately search for CVEs.

---

## 2. Attack Surface Identification

Identify all possible entry points:

- Web applications / APIs
- Custom ports
- SSH
- Downloadable files
- Backups
- Binaries
- Cron jobs
- IPC mechanisms
- Unusual services

Key question:

> **Where does the system implicitly trust user input?**

---

## 3. Manual Enumeration

Perform deep analysis of services and applications:

- Parameters
- Edge cases
- Logic flaws
- Differences in responses
- Role behavior
- Permission boundaries

This stage typically consumes **most of the time on Insane machines**.

---

## 4. Web / API / Application Logic (If Present)

Analyze:

- Authentication flows
- Session management
- Cookies
- Tokens
- Request sequencing
- Race conditions
- IDOR
- SSRF
- General logic flaws

Testing should be **manual**, not dependent on automated scanners.

---

## 5. Reverse Engineering (Often Required)

Analyze:

- ELF binaries
- Scripts
- Services
- Plugins

Common tools:

- Ghidra
- `strings`
- `objdump`
- `readelf`

Focus on identifying:

- Application logic
- Hardcoded secrets
- Custom protocols
- Input parsing vulnerabilities

---

## 6. Dynamic Analysis

Run the program and observe runtime behavior.

Typical monitoring includes:

- `strace`
- `ltrace`
- `gdb`
- Log analysis
- Network traffic inspection

The objective is to understand **how the program behaves in practice**, not only how it appears in code.

---

## 7. Vulnerability Chaining

Combine smaller weaknesses into a full exploitation path.

Example chain: information disclosure → logic flaw → code execution

**Insane machines almost always require chaining multiple issues.**

---

## 8. Initial Access

Obtain the first level of system control:

- User shell
- Service account access
- Web shell

This is **not the objective**, only an intermediate step.

---

## 9. Privilege Escalation (Manual)

Investigate potential escalation vectors:

- `sudo` permissions
- SUID binaries
- Linux capabilities
- Cron jobs
- Writable files
- Services
- PATH hijacking
- Container escapes

Enumeration tools may provide hints, but **manual reasoning determines the path forward**.

---

## 10. Pivoting / Lateral Movement

Explore additional components within the environment:

- Other networks
- Internal services
- Containers
- Sockets
- Trust boundaries

Use tunneling or proxy techniques to reach new targets.

---

## 11. Understanding Stabilization

Ensure complete understanding of **why the access works**.

Avoid blind persistence.  
The objective is **full comprehension of the exploitation vector**.

---

## 12. Documentation and Verification

Document the entire attack path as **one coherent logical chain**.

If the compromise cannot be explained **without listing commands**, return to earlier steps and reassess the analysis.

---

# Core Principle

If progress stops, return to **enumeration and logical analysis**.

On **Insane difficulty**, problems rarely arise from missing exploits.

They almost always result from **insufficient analysis or incomplete understanding of the system**.
