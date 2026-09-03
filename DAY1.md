# 🌐 IP Address and IPv4

---

# What is an IP Address?

**IP** stands for **Internet Protocol**.

An **IP address** is a logical address assigned to a device on a network. It helps identify the **source and destination** of data so that information can reach the correct device.

For example:

```text
Laptop → 192.168.1.10
Phone  → 192.168.1.11
TV     → 192.168.1.12
```

If a laptop wants to send data to a phone, it needs to know the phone's network address.

```text
Laptop
192.168.1.10
      │
      │ Data
      ▼
Phone
192.168.1.11
```

The IP address helps the network determine:

> **Where should this data go?**

---

# Why Do IP Addresses Exist?

Imagine sending a physical letter.

```text
You
 │
 │ Letter
 ▼
House Address
 │
 ▼
Correct Person
```

You need an address to ensure the letter reaches the correct destination.

The same concept applies to computer networks.

Imagine multiple computers connected to a network:

```text
Computer A
Computer B
Computer C
```

If Computer A wants to send data specifically to Computer B, the network needs a way to identify Computer B.

This is why devices need network addresses.

```text
Computer A → 192.168.1.10
Computer B → 192.168.1.20
Computer C → 192.168.1.30
```

Now Computer A can send data to:

```text
Destination: 192.168.1.20
```

Therefore, the main purpose of an IP address is:

> **To identify network destinations and help route data to the correct location.**

---

# What is a Logical Address?

An IP address is called a **logical address** because it is assigned based on the network configuration and can change.

For example, the same laptop can have different IP addresses on different networks.

### Home Wi-Fi

```text
Laptop → 192.168.1.10
```

### Office Wi-Fi

```text
Laptop → 10.0.0.25
```

### Mobile Hotspot

```text
Laptop → 192.168.43.5
```

The physical device remains the same, but its IP address can change depending on the network it connects to.

Therefore:

> **A logical address is an address assigned to a device based on its network configuration and location within a network.**

---

# What is IPv4?

**IPv4** stands for:

> **Internet Protocol Version 4**

IPv4 is the fourth version of the Internet Protocol and is widely used for network communication.

An IPv4 address looks like:

```text
192.168.1.10
```

It consists of four sections separated by dots:

```text
192 . 168 . 1 . 10
 │     │    │    │
Octet Octet Octet Octet
```

Each section is called an **octet**.

Each octet contains **8 bits**:

```text
4 Octets × 8 Bits = 32 Bits
```

Therefore:

> **An IPv4 address is 32 bits long.**

---

# Bits and Octets

Computers store and process information using binary values:

```text
0 and 1
```

Each binary digit is called a **bit**.

Since an IPv4 address contains four octets, and each octet contains 8 bits:

```text
8 + 8 + 8 + 8 = 32 bits
```

For example:

```text
192.168.1.10
```

In binary:

```text
192 → 11000000
168 → 10101000
1   → 00000001
10  → 00001010
```

Combined:

```text
11000000.10101000.00000001.00001010
```

Each group contains 8 bits:

```text
11000000
││││││││
8 bits
```

---

# Why Does Each Octet Range from 0 to 255?

Each octet contains **8 bits**.

The smallest possible value is:

```text
00000000 = 0
```

The largest possible value is:

```text
11111111 = 255
```

Therefore, each octet can range from:

```text
0 → 255
```

Examples of valid IPv4 addresses:

```text
192.168.1.10
10.0.0.1
255.255.255.255
```

This is invalid:

```text
192.168.1.300 ❌
```

Because:

```text
300 > 255
```

---

# How Many IPv4 Addresses Are Available?

IPv4 uses **32 bits**.

Each bit can have two possible values:

```text
0 or 1
```

Therefore, the total number of possible IPv4 addresses is:

```text
2³² = 4,294,967,296
```

So, IPv4 provides approximately:

> **4.3 billion possible addresses**

However, not all IPv4 addresses are available for public use because some address ranges are reserved for **private networks and special purposes**.
