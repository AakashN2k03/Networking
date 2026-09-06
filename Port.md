# 🔌 What is a Port in Networking?

A **port** is a logical communication endpoint that helps identify **which application or service** on a device should receive network data.

Think of it like this:

```text
IP Address  → Identifies the device
Port Number → Identifies the application/service on that device
```

Or simply:

```text
IP Address  → Correct Device
Port Number → Correct Application
```

---

# 📌 Example

Suppose a server has this IP address:

```text
192.168.1.10
```

It runs multiple services:

```text
192.168.1.10:80   → Web Server (HTTP)
192.168.1.10:443  → Secure Web Server (HTTPS)
192.168.1.10:22   → SSH
```

Here:

```text
192.168.1.10 → Device/Server
80, 443, 22 → Ports
```

---

# 🌐 Why Do We Need Ports?

A single computer can run multiple applications simultaneously.

For example:

```text
Your Computer
│
├── Browser
├── WhatsApp
├── VS Code
├── Zoom
└── Database
```

All of these applications may use the network.

So, when data arrives at your computer, the operating system needs to determine:

> **Which application should receive this data?**

That's what the **port number** helps determine.

---

# 🔢 Port Number Range

Port numbers range from:

```text
0 → 65535
```
