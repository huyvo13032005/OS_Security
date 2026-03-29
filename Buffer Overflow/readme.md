# Buffer Overflow

## 📌 Introduction

A **Buffer Overflow** occurs when a program writes more data to a buffer than it can hold.
This overflow overwrites adjacent memory, which may lead to crashes, data corruption, or arbitrary code execution.

Buffer overflows are one of the most common and dangerous software vulnerabilities.

---

## 🧠 How It Happens

* Fixed-size buffer is allocated
* Input exceeds buffer size
* Extra data overwrites memory
* Control flow may be hijacked

---

## ⚙️ Simple Example (C)

```c
#include <stdio.h>
#include <string.h>

void vulnerable() {
    char buffer[10];
    gets(buffer);   // unsafe
    printf("You entered: %s\n", buffer);
}

int main() {
    vulnerable();
    return 0;
}
```

If user inputs more than 10 characters → overflow occurs.

---

## 📍 Stack Layout (Conceptual)

```
| Return Address |
| Saved EBP      |
| buffer[10]     |
```

Overflowing `buffer` may overwrite:

* Saved EBP
* Return address
* Control flow

---

## 🚨 Impact

Buffer overflow can lead to:

* Arbitrary code execution
* Privilege escalation
* Denial of Service (DoS)
* Data corruption
* Bypass authentication

---

## 🧪 Exploitation Concept

```
[ Padding ][ New Return Address ][ Shellcode ]
```

Attacker overwrites return address to jump to malicious code.

---

## 🔐 Prevention Techniques

* Use safe functions (`fgets`, `strncpy`)
* Stack canaries
* Address Space Layout Randomization (ASLR)
* Data Execution Prevention (DEP / NX)
* Bounds checking
* Compiler protections

---

## 🛠 Secure Version

```c
#include <stdio.h>
#include <string.h>

void safe() {
    char buffer[10];
    fgets(buffer, sizeof(buffer), stdin);
    printf("You entered: %s\n", buffer);
}
```

---

## 📊 Types of Buffer Overflow

* Stack-based buffer overflow
* Heap-based buffer overflow
* Integer overflow
* Format string vulnerability
* Off-by-one overflow

---

## 🔎 Related Concepts

* Stack Overflow (security)
* Heap Overflow
* Return Oriented Programming (ROP)
* Shellcode
* ASLR
* DEP
* Stack Canary
