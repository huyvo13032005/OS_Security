# Discretionary Access Control (DAC)

## 📌 Introduction

**Discretionary Access Control (DAC)** is an access control model where the owner of a resource determines who is allowed to access it.
Permissions are assigned based on user identity and ownership, giving users discretion over their own resources.

---

## 🧠 Key Characteristics

* Resource owner controls access
* Permissions based on user identity
* Flexible and easy to manage
* Commonly implemented in operating systems
* Vulnerable to privilege misuse

---

## ⚙️ How DAC Works

In DAC, each object has:

* Owner
* Access permissions
* Access Control List (ACL) (optional)

The owner decides:

* Who can read
* Who can write
* Who can execute

---

## 🖥 Example (Linux File Permissions)

```bash
-rwxr-xr-- 1 user user file.txt
```

Breakdown:

* Owner: `rwx`
* Group: `r-x`
* Others: `r--`

Command examples:

```bash
chmod 755 file.txt
chown user file.txt
```

---

## 📊 DAC Permission Matrix

| Subject | Object | Permission |
| ------- | ------ | ---------- |
| User A  | File 1 | Read       |
| User B  | File 1 | Write      |
| User C  | File 1 | None       |

---

## ⚠️ Security Weaknesses

DAC is vulnerable to:

* Trojan horse attacks
* Privilege abuse
* Permission propagation
* Malware execution with user privileges

Example:

```bash
User downloads malicious script
Script inherits user permissions
Script accesses sensitive files
```

---

## 🔐 DAC vs Other Models

| Model | Control | Flexibility | Security |
| ----- | ------- | ----------- | -------- |
| DAC   | Owner   | High        | Low      |
| MAC   | System  | Low         | High     |
| RBAC  | Role    | Medium      | Medium   |

---

## 🛠 Mitigation Techniques

* Principle of Least Privilege
* File permission auditing
* Use MAC for sensitive systems
* Limit executable permissions
* Monitor user activity

---

## 📚 Real-world Usage

DAC is used in:

* Linux / Unix file systems
* Windows NTFS permissions
* Database access control
* Shared file environments

---

## 🔎 Related Concepts

* MAC (Mandatory Access Control)
* RBAC (Role-Based Access Control)
* ACL (Access Control List)
* Least Privilege Principle
* File System Security

