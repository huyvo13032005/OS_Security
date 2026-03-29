# Race Condition

## 📌 Introduction

A **Race Condition** occurs when multiple threads or processes access and manipulate shared data concurrently without proper synchronization.
The final result depends on the timing and order of execution, leading to unpredictable behavior and potential security vulnerabilities.

---

## ⚠️ Causes

Race conditions typically occur when:

* Multiple threads/processes access shared variables
* No synchronization mechanism is used
* Read and write operations are non-atomic
* Critical sections are not protected

---

## 🧠 Simple Example

### Python Example (Race Condition)

```python
import threading

counter = 0

def increment():
    global counter
    for _ in range(100000):
        counter += 1

threads = []
for _ in range(2):
    t = threading.Thread(target=increment)
    threads.append(t)
    t.start()

for t in threads:
    t.join()

print("Counter =", counter)
```

Expected result: `200000`
Actual result: **Unpredictable** (due to race condition)

---

## 🔐 Fix Using Lock

```python
import threading

counter = 0
lock = threading.Lock()

def increment():
    global counter
    for _ in range(100000):
        with lock:
            counter += 1

threads = []
for _ in range(2):
    t = threading.Thread(target=increment)
    threads.append(t)
    t.start()

for t in threads:
    t.join()

print("Counter =", counter)
```

---

## 🛠 Prevention Techniques

* Mutex / Lock
* Semaphore
* Atomic operations
* Critical Section protection
* Monitor
* Thread-safe data structures

---

## 📚 Real-world Impact

Race conditions can lead to:

* Data corruption
* Privilege escalation
* Authentication bypass
* Financial transaction errors
* Denial of Service (DoS)

---

## 🧪 Security Example

A common race condition vulnerability:

```
check_permission()
write_file()
```

An attacker may modify the file between the check and write operations, leading to a **TOCTOU (Time-of-Check to Time-of-Use)** vulnerability.

---

## 🔎 Related Concepts

* TOCTOU
* Deadlock
* Mutex
* Semaphore
* Thread synchronization
