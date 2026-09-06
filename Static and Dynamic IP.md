# 🌐 Static IP vs Dynamic IP

An **IP address** identifies a device on a network. Depending on how the address is assigned, it can be either:

* **Static IP Address** → Stays the same
* **Dynamic IP Address** → Can change automatically

---

# 1️⃣ What is a Static IP Address?

A **Static IP address** is an IP address that is manually assigned or reserved for a device and generally remains the same.

## Example

Your server has this IP address:

```text
192.168.1.100
```

Today:

```text
Server → 192.168.1.100
```

Tomorrow:

```text
Server → 192.168.1.100
```

Next month:

```text
Server → 192.168.1.100
```

The address remains unchanged.

---

## 📌 Why Do We Need Static IPs?

Some devices need to be **consistently reachable at the same address**.

For example:

* 🌐 Web Servers
* 🗄️ Database Servers
* 🖨️ Network Printers
* 📹 CCTV Cameras
* 🎮 Game Servers
* 🏢 Enterprise Servers

Imagine your company database changes its IP address every day.

Today:

```text
Database → 192.168.1.100
```

Tomorrow:

```text
Database → 192.168.1.150
```

Applications trying to connect to the old IP address would fail.

Therefore, servers often use **Static IP addresses**.

---

## 🏢 Example: Static IP in a Company Network

Suppose you have the following network:

```text
Router       → 192.168.1.1

Web Server   → 192.168.1.10
Database     → 192.168.1.20
Printer      → 192.168.1.30
```

These devices can always be reached using the same IP address.

```text
Application
     │
     ▼
192.168.1.20
(Database)
```

---

# 2️⃣ What is a Dynamic IP Address?

A **Dynamic IP address** is automatically assigned to a device and may change over time.

Dynamic IP addresses are usually assigned using:

## 🔥 DHCP

**DHCP = Dynamic Host Configuration Protocol**

DHCP automatically provides devices with:

* IP Address
* Subnet Mask
* Default Gateway
* DNS Server

---

## 💻 Example

When you connect your laptop to Wi-Fi:

```text
Laptop
   │
   │ Requests IP Address
   ▼
DHCP Server / Router
   │
   │ Assigns
   ▼
192.168.1.105
```

Your laptop receives:

```text
IP Address: 192.168.1.105
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.1
DNS: 8.8.8.8
```

Later, the DHCP lease may expire, or you may reconnect to the network.

Your laptop could then receive:

```text
192.168.1.120
```

So, the IP address can change.

---

# 🔄 How DHCP Assigns a Dynamic IP

The DHCP process is commonly called **DORA**.

**DORA stands for:**

1. **Discover**
2. **Offer**
3. **Request**
4. **Acknowledge**

---

## 1️⃣ Discover

Your device asks:

> "Is there any DHCP server available?"

```text
Laptop → DHCP DISCOVER
```

---

## 2️⃣ Offer

The DHCP server responds:

> "I can give you this IP address."

```text
DHCP Server → OFFER

IP: 192.168.1.105
```

---

## 3️⃣ Request

Your device says:

> "Okay, I want this IP."

```text
Laptop → DHCP REQUEST
```

---

## 4️⃣ Acknowledge

The DHCP server confirms the assignment:

```text
DHCP Server → ACKNOWLEDGEMENT
```

Now your device can use:

```text
192.168.1.105
```

---

# ⏳ What is a DHCP Lease?

A Dynamic IP address is usually assigned for a specific period called a **lease**.

For example:

```text
IP Address: 192.168.1.105

Lease Time: 24 hours
```

After that period, the device may try to renew the same ip if not receive new ip:

* 🔄 Renew the same IP address
* 🔀 Receive a different IP address

- The IP may change if, for example, the device disconnects for a long time, the DHCP configuration changes, or the previous IP is no longer available.

---

# 🆚 Static IP vs Dynamic IP

| Feature                     | Static IP                      | Dynamic IP             |
| --------------------------- | ------------------------------ | ---------------------- |
| **Changes?**                | ❌ Usually does not change      | ✅ Can change           |
| **Assignment**              | Manual / Reserved              | Automatically via DHCP |
| **Management**              | Requires more configuration    | Automatic              |
| **Best For**                | Servers                        | User devices           |
| **Cost**                    | Can be more expensive publicly | Usually cheaper        |
| **Reliability for Hosting** | ⭐⭐⭐⭐⭐                          | ⭐⭐                     |
| **Scalability**             | Harder to manage manually      | Easy                   |
| **Common Usage**            | Servers, Printers              | Laptops, Phones        |

---
