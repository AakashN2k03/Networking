# 🌐 IP Addressing: IPv4 and IPv6

A beginner-friendly guide to understanding IP addresses, IPv4, and IPv6.

---

## Table of Contents

**Part 1 — IPv4**
1. [What is an IP Address?](#what-is-an-ip-address)
2. [Why Do IP Addresses Exist?](#why-do-ip-addresses-exist)
3. [What is a Logical Address?](#what-is-a-logical-address)
4. [What is IPv4?](#what-is-ipv4)
5. [Bits and Octets](#bits-and-octets)
6. [Why Does Each Octet Range from 0 to 255?](#why-does-each-octet-range-from-0-to-255)
7. [How Many IPv4 Addresses Are Available?](#how-many-ipv4-addresses-are-available)

**Part 2 — IPv6**
1. [What is IPv6?](#1-what-is-ipv6)
2. [Why was IPv6 created?](#2-why-was-ipv6-created)
3. [What does an IPv6 address look like?](#3-what-does-an-ipv6-address-look-like)
4. [Why hexadecimal?](#4-why-hexadecimal)
5. [IPv6 address shortening](#5-ipv6-address-shortening)
6. [IPv6 address structure](#6-ipv6-address-structure)
7. [IPv6 uses prefixes](#7-ipv6-uses-prefixes)

---

# Part 1 — IPv4

## What is an IP Address?

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

## Why Do IP Addresses Exist?

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

## What is a Logical Address?

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

## What is IPv4?

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

## Bits and Octets

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

## Why Does Each Octet Range from 0 to 255?

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

## How Many IPv4 Addresses Are Available?

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

---

# Part 2 — IPv6

## 1. What is IPv6?

**IPv6 = Internet Protocol version 6.**

Its main job is to give devices an **IP address** so they can communicate over a network.

For example:

```text
Your Laptop
    ↓
IPv6 Address
    ↓
2001:db8:1234:5678::10
```

Think of an IP address like a **house address**.

- House address → tells where a house is
- IP address → tells where a device/network is

---

## 2. Why was IPv6 created?

The older protocol is **IPv4**.

IPv4 uses:

```text
192.168.1.10
```

IPv4 has only **32 bits**.

That gives roughly:

**4.3 billion addresses**

Sounds huge, but the internet has billions of devices.

So IPv4 addresses became scarce.

IPv6 increases this massively by using **128 bits**.

```text
IPv4 → 32 bits
IPv6 → 128 bits
```

IPv6 has approximately:

**340 undecillion addresses**

That's:

```text
2^128
```

So address exhaustion is basically no longer the problem.

---

## 3. What does an IPv6 address look like?

IPv4:

```text
192.168.1.10
```

IPv6:

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

It uses:

- hexadecimal numbers
- `:` as a separator
- 8 groups
- each group = 16 bits

Example:

```text
2001 : 0db8 : 85a3 : 0000 : 0000 : 8a2e : 0370 : 7334
  ↑      ↑      ↑      ↑      ↑      ↑      ↑      ↑
 16     16     16     16     16     16     16     16 bits
```

Total:

```text
8 × 16 = 128 bits
```

---

## 4. Why hexadecimal?

128 bits would be extremely long if written in binary.

Instead of:

```text
0010000000000001...
```

we use hexadecimal:

```text
2001:db8:...
```

Each hexadecimal digit represents **4 bits**.

So:

```text
4 hex digits = 16 bits
```

That's why each IPv6 section contains up to 4 hexadecimal digits.

---

## 5. IPv6 address shortening

IPv6 addresses can look intimidating:

```text
2001:0db8:0000:0000:0000:0000:0000:0001
```

We can remove leading zeros:

```text
2001:db8:0:0:0:0:0:1
```

And consecutive groups of zeros can be replaced with:

```text
::
```

So:

```text
2001:db8:0:0:0:0:0:1
```

becomes:

```text
2001:db8::1
```

### Important rule

`::` can represent consecutive zero groups **only once** in an IPv6 address.

For example:

```text
2001:db8::1
```

is valid.

---

## 6. IPv6 address structure

One of the most important concepts is that an IPv6 address isn't simply "the device number."

Usually it has two major parts:

```text
Network Prefix       Interface ID
      ↓                    ↓
2001:db8:1234:5678 : abcd:ef12:3456:7890
```

Think:

```text
NETWORK                     DEVICE
   ↓                           ↓
2001:db8:1234:5678       abcd:ef12:3456:7890
```

The network prefix identifies the network.

The interface ID identifies an interface/device within that network.

---

## 7. IPv6 uses prefixes

You'll commonly see:

```text
2001:db8:1234:5678::/64
```

The `/64` means:

```text
First 64 bits = network prefix
Remaining 64 bits = interface ID
```

Conceptually:

```text
2001:db8:1234:5678 | abcd:ef12:3456:7890
<---- 64 bits ----> <---- 64 bits ---->
      NETWORK             HOST
```

A `/64` network contains:

```text
2^64
```

possible interface IDs — an enormous number.
