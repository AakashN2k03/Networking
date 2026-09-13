# 🌐 NAT — Network Address Translation

## 📌 What is NAT?

**NAT (Network Address Translation)** is a technique used by a router to translate **private IP addresses into public IP addresses** and vice versa.

It allows multiple devices in a private network to communicate with the Internet using a **public IP address**.

```text 
Private Network                    Internet

Laptop → 192.168.1.10 ──┐
Phone  → 192.168.1.11 ──┤
TV     → 192.168.1.12 ──┤
                         ↓
                       Router
                         ↓
                    NAT / PAT
                         ↓
                 Public IP
                49.204.100.25
                         ↓
                     Internet
```

---

# 🤔 Why was NAT needed?

The main reason NAT became important was the **limited number of IPv4 addresses**.

IPv4 provides about **4.3 billion addresses**, but the number of Internet-connected devices became much larger.

Instead of giving every device a public IP address, networks started using **private IP addresses**.

Common private IP ranges are:

```text
10.0.0.0        – 10.255.255.255
172.16.0.0      – 172.31.255.255
192.168.0.0     – 192.168.255.255
```

For example:

```text
Laptop → 192.168.1.10
Phone  → 192.168.1.11
TV     → 192.168.1.12
```

These devices can share a single public IP through NAT.

---

# 🌍 Private IP vs Public IP

### Private IP

Used inside a local/private network.

```text
192.168.1.10
```

It is **not directly routable over the public Internet**.

### Public IP

Used to identify a network/device on the public Internet.

```text
49.204.100.25
```

Your ISP typically provides a public IP to your router.

---

# 🔄 How NAT Works

Suppose your laptop has:

```text
Private IP:
192.168.1.10
```

Your router has:

```text
Public IP:
49.204.100.25
```

The laptop wants to access a website.

### Step 1 — Laptop sends a request

```text
Source:
192.168.1.10

Destination:
142.250.x.x
```

### Step 2 — Router receives the packet

The router performs NAT.

```text
192.168.1.10
      ↓
     NAT
      ↓
49.204.100.25
```

The source IP is changed to the router's public IP.

### Step 3 — Packet goes to the Internet

```text
49.204.100.25
       ↓
    Internet
       ↓
    Website
```

### Step 4 — Response comes back

The website sends the response to:

```text
49.204.100.25
```

The router checks its NAT information and determines which internal device requested the data.

```text
49.204.100.25
       ↓
      NAT
       ↓
192.168.1.10
       ↓
    Laptop
```

---

# 📋 NAT Table

The router keeps track of translations.

For example:

```text
Private Address          Public Address

192.168.1.10:5000  →  49.204.100.25:60001
192.168.1.11:5001  →  49.204.100.25:60002
```

This allows the router to identify which internal device should receive each response.

---

# 🧩 Types of NAT

There are three commonly discussed types:

## 1. Static NAT

**One private IP ↔ One public IP**

The mapping is fixed.

```text
192.168.1.10
      ↕
49.204.100.10
```

Example:

```text
Internal Web Server
10.0.0.10
      ↕
Public IP
50.20.30.40
```

### Use case

Useful when a specific internal server needs a consistent public IP.

---

# 2. Dynamic NAT

A private IP is mapped to a public IP from a **pool of public addresses**.

Example:

```text
Private                  Public

10.0.0.10  ─────────→  50.20.30.1
10.0.0.11  ─────────→  50.20.30.2
10.0.0.12  ─────────→  50.20.30.3
```

The mapping is dynamic rather than permanently fixed.

---

# 3. PAT — Port Address Translation ⭐

**PAT allows many private devices to share one public IP address.**

This is extremely common in home networks.

Example:

```text
Laptop
192.168.1.10:5000
       ↓
       PAT
       ↓
49.204.100.25:60001
```

Phone:

```text
Phone
192.168.1.11:5001
       ↓
       PAT
       ↓
49.204.100.25:60002
```

Both devices use the same public IP:

```text
49.204.100.25
```

But different port numbers allow the router to distinguish their connections.

---

# 🏠 Real-World Example

Your home might look like this:

```text
                    INTERNET
                        │
                        │
                Public IP
              49.204.100.25
                        │
                    ┌───▼───┐
                    │Router │
                    │  NAT  │
                    └───┬───┘
                        │
          ┌─────────────┼─────────────┐
          │             │             │
          ▼             ▼             ▼
       Laptop          Phone          TV
    192.168.1.10   192.168.1.11   192.168.1.12
```

Instead of requiring:

```text
Laptop → Public IP
Phone  → Public IP
TV     → Public IP
```

they can share:

```text
             One Public IP
                  ↓
           49.204.100.25
                  ↓
             NAT / PAT
          ↙       ↓       ↘
      Laptop    Phone      TV
```

---

# 🔑 Why is NAT Important?

### 1. Conserves IPv4 addresses

Multiple devices can share one public IPv4 address.

```text
100 devices
     ↓
    NAT
     ↓
1 Public IP
```

### 2. Allows private networks

Organizations and homes can use private IP addresses internally.

```text
192.168.x.x
10.x.x.x
172.16.x.x – 172.31.x.x
```

### 3. Makes Internet connectivity practical

Millions of private networks can independently use the same private IP ranges.

For example:

```text
Home A → 192.168.1.10
Home B → 192.168.1.10
Home C → 192.168.1.10
```

This is possible because these are separate private networks.

---

# 🧠 NAT vs PAT

| NAT                              | PAT                                  |
| -------------------------------- | ------------------------------------ |
| Translates IP addresses          | Translates IP addresses + ports      |
| Can use one-to-one mapping       | Many devices can share one public IP |
| Static/Dynamic mappings possible | Very common in home networks         |
| May require multiple public IPs  | Can work with one public IP          |

---


## ⭐ Remember This

> **NAT acts as a translator between a private network and the public Internet, allowing private devices to communicate externally while conserving public IPv4 addresses.**
