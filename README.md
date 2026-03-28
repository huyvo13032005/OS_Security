# 🛡️ Operating System Security Labs

This repository contains my hands-on practice and writeups related to **Operating System Security**, focusing on:

* Discretionary Access Control (DAC)
* Race Condition Vulnerabilities
* Privilege Escalation Concepts
* File Permission Exploitation

These labs are performed in a Linux environment (Kali/Ubuntu) for educational and cybersecurity learning purposes.

---

# 📌 Lab 1: Discretionary Access Control (DAC)

## 🎯 Objective

Understand how Linux file permissions work and how improper DAC configuration can lead to privilege escalation.

## 🧠 Concepts Covered

* File ownership
* Read / Write / Execute permissions
* chmod, chown
* SUID bit
* Privilege escalation via misconfigured files

## 🔬 Example

```bash
ls -l file
chmod 777 file
chmod u+s binary
```

## ⚠️ Vulnerability

If a binary owned by root has SUID enabled and is writable, a normal user may escalate privileges.

Example:

```bash
-rwsrwxrwx 1 root root vulnerable_binary
```

## 🚨 Exploitation

User modifies binary and executes it:

```bash
./vulnerable_binary
```

Result: privilege escalation to root.

---

# 📌 Lab 2: Race Condition

## 🎯 Objective

Exploit timing vulnerability when a program checks a file before using it.

## 🧠 Concepts Covered

* TOCTOU (Time Of Check To Time Of Use)
* Symbolic links
* File replacement attack
* Privilege escalation

## 🔬 Vulnerable Code Example

```c
if(access("file", W_OK) == 0){
    FILE *fp = fopen("file", "w");
    fwrite("data", 1, 4, fp);
}
```

Between `access()` and `fopen()` attacker replaces the file.

## ⚙️ Exploit Steps

### 1. Create symbolic link

```bash
ln -s /etc/passwd file
```

### 2. Run race condition loop

```bash
while true; do
    ln -sf /etc/passwd file
done
```

### 3. Trigger vulnerable program

```bash
./vulnerable_program
```

## 💥 Result

Attacker modifies protected system file.

---

# 📌 Lab 3: Operating System Security Concepts

## Topics Covered

* DAC vs MAC
* Linux Permissions
* SUID/SGID
* Sticky Bit
* Race Conditions
* Privilege Escalation

## Permission Table

| Permission | Value |
| ---------- | ----- |
| Read       | 4     |
| Write      | 2     |
| Execute    | 1     |

Example:

```
chmod 755 file
```

---

# 🧪 Environment

* Kali Linux
* GCC / Clang
* Ubuntu
* Linux Kernel

Install dependencies:

```bash
sudo apt update
sudo apt install gcc clang -y
```

---

# 🎓 Learning Outcomes

After completing these labs, I understood:

* How DAC works in Linux
* How misconfigured permissions lead to vulnerabilities
* How Race Conditions are exploited
* Basic privilege escalation techniques

---

# ⚠️ Disclaimer

This repository is for **educational purposes only**.
All experiments were conducted in controlled lab environments.

---

# 👨‍💻 Author

CTF Player | Cybersecurity Student | OS Security Learner
