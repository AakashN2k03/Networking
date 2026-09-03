# 🌐 Subnet, Subnet Mask, and CIDR

## 1. What is a Subnet?

**Subnet** stands for **Subnetwork**.

A subnet is a smaller network created by dividing a larger network into smaller networks.

---

## 2. Why do Subnets Exist?

Subnets divide a large network into smaller and more manageable networks.

### Benefits of Subnetting

* Reduces broadcast traffic
* Improves network performance
* Improves security
* Makes network management easier
* Organizes devices into logical groups
* Helps use IP addresses efficiently

---

## 3. What is a Subnet Mask?

A **Subnet Mask** determines which part of an IP address represents the **Network** and which part represents the **Host (device)**.

Example:

```text
IP Address:  192.168.1.10
Subnet Mask: 255.255.255.0
```

A subnet mask uses binary values:

```text
1 → Network portion
0 → Host portion
```

Example:

```text
255.255.255.0

11111111.11111111.11111111.00000000
^^^^^^^^^^^^^^^^^^^^^^^^
       Network

                          00000000
                          ^^^^^^^^
                           Host
```

---

## 4. What is CIDR?

**CIDR** stands for **Classless Inter-Domain Routing**.

CIDR is a shorter way of representing how many bits belong to the **network portion**.

Example:

```text
192.168.1.0/24
```

The `/24` means:

```text
First 24 bits → Network
Remaining 8 bits → Host
```

---

## 5. CIDR and Subnet Mask

CIDR and Subnet Mask represent the **same network boundary information**, but in different formats.

```text
CIDR:        /24
Subnet Mask: 255.255.255.0
```

`/24` means there are **24 consecutive `1` bits** in the subnet mask:

```text
11111111.11111111.11111111.00000000
```

Therefore:

```text
/24 = 255.255.255.0
```

---

## 6. CIDR vs Subnet Mask

| CIDR  | Subnet Mask       | Total IP Addresses |
| ----- | ----------------- | -----------------: |
| `/8`  | `255.0.0.0`       |         16,777,216 |
| `/16` | `255.255.0.0`     |             65,536 |
| `/24` | `255.255.255.0`   |                256 |
| `/25` | `255.255.255.128` |                128 |
| `/26` | `255.255.255.192` |                 64 |
| `/27` | `255.255.255.224` |                 32 |
| `/28` | `255.255.255.240` |                 16 |
| `/29` | `255.255.255.248` |                  8 |
| `/30` | `255.255.255.252` |                  4 |

### Difference

**CIDR** uses short notation:

```text
/24
```

**Subnet Mask** uses decimal notation:

```text
255.255.255.0
```

Both describe the same thing:

> Where the network portion ends and the host portion begins.

---
