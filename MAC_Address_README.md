# MAC Address — Beginner-Friendly Notes

## What is a MAC Address?

**MAC Address (Media Access Control Address)** is a unique identifier associated with a network interface of a device.

You can think of it as the **local hardware/network-interface address** used when communicating on a local network.

Example:

```text
MAC Address:
A4:5E:60:12:AB:9F
```

> **Important:** A MAC address identifies a **network interface**, not necessarily the entire device. A laptop can have multiple network interfaces, such as Wi-Fi and Ethernet, and each can have its own MAC address.

---

## Where is a MAC Address Used?

A MAC address is mainly used for communication on a **local network (LAN)**.

For example, imagine:

```text
Laptop ───── Wi-Fi ───── Router
```

Your laptop needs to send a frame to the router. The local network uses MAC addresses to identify the network interfaces involved in that local communication.

Example:

```text
Laptop MAC  →  Router MAC
```

If two devices are connected to the same local network:

```text
Laptop A ───────── Router ───────── Laptop B
```

MAC addresses help the local network deliver Ethernet/Wi-Fi frames to the correct network interface.

---

# MAC Address vs IP Address

This is the most important distinction.

| MAC Address | IP Address |
|---|---|
| Identifies a network interface | Identifies a logical network address/interface |
| Mainly used for local-network/link communication | Used for routing between networks |
| Layer 2 (Data Link) | Layer 3 (Network) |
| Usually associated with a network interface | Assigned through network configuration |
| Example: `A4:5E:60:12:AB:9F` | Example: `192.168.1.10` |

A simple way to remember:

```text
IP  → Where am I / where does the packet need to go?
MAC → Which local network interface should receive this frame?
```

---

# If We Already Have an IP Address, Why Do We Need MAC?

This is the most common question.

At first, it seems that the IP address should be enough:

```text
Laptop IP = 192.168.1.10
```

So why do we need:

```text
Laptop MAC = A4:5E:60:12:AB:9F
```

The reason is that **IP and MAC operate at different layers and perform different jobs**.

- **IP works at Layer 3** and helps packets get routed between networks.
- **MAC works at Layer 2** and helps deliver frames on the current local network/link.

Think of it this way:

```text
IP  → "Where is the destination?"
MAC → "Who should receive this local frame right now?"
```

---

# Real-Time Example: Opening Google

Suppose your laptop is connected to your home Wi-Fi.

Your laptop:

```text
IP  = 192.168.1.10
MAC = AA:BB:CC:11:22:33
```

Your router:

```text
IP  = 192.168.1.1
MAC = DD:EE:FF:44:55:66
```

You type:

```text
https://google.com
```

## Step 1 — Find Google's IP

Your laptop uses DNS to find an IP address for Google.

For example:

```text
google.com
     ↓
142.250.x.x
```

Now your laptop knows:

```text
Destination IP = 142.250.x.x
```

---

## Step 2 — Is Google on the local network?

Your laptop checks whether Google's IP belongs to its local network.

It does not.

Your laptop is on:

```text
192.168.1.x
```

Google is on a completely different network.

Therefore, your laptop thinks:

> "Google is not directly connected to my local network. I need to send this packet to my router, which is my next hop."

---

## Step 3 — Find the Router's MAC Address

Your laptop knows:

```text
Router IP = 192.168.1.1
```

But local Wi-Fi/Ethernet communication needs a MAC address.

Using ARP (for IPv4), the laptop can discover:

```text
192.168.1.1
      ↓
DD:EE:FF:44:55:66
```

So it now knows the router's MAC.

---

## Step 4 — Create the Packet and Frame

Conceptually, the data looks like:

```text
┌─────────────────────────────────────────┐
│              LOCAL FRAME                │
│                                         │
│ Source MAC      = Laptop MAC            │
│ Destination MAC = Router MAC            │
│                                         │
│ ┌─────────────────────────────────────┐ │
│ │             IP PACKET               │ │
│ │                                     │ │
│ │ Source IP      = Laptop IP          │ │
│ │ Destination IP = Google IP          │ │
│ └─────────────────────────────────────┘ │
└─────────────────────────────────────────┘
```

Notice the important difference:

```text
MAC Destination → Router
IP Destination  → Google
```

This is the key to understanding why both addresses are needed.

---

# Why Is Google's MAC Address Not Needed?

This is another very important question.

You might think:

> "If I am sending data to Google, shouldn't I know Google's MAC address?"

**No.**

Your laptop and Google's server are not on the same local network.

The simplified path is:

```text
Your Laptop
     ↓
Your Router
     ↓
ISP
     ↓
Internet
     ↓
Google
```

Your laptop only needs the MAC address of the **next device on its local link**, usually the router.

It does not need Google's MAC address.

---

# Then What Is the Connection Between Google's IP and My Laptop's MAC?

This is where everything comes together.

Suppose:

```text
Laptop:
IP  = 192.168.1.10
MAC = AA:BB:CC:11:22:33

Router:
IP  = 192.168.1.1
MAC = DD:EE:FF:44:55:66

Google:
IP  = 142.250.x.x
```

Your laptop wants to reach:

```text
Google IP = 142.250.x.x
```

But the **first physical/local step** is:

```text
Laptop → Router
```

Therefore:

```text
Source MAC      = Laptop MAC
Destination MAC = Router MAC

Source IP       = Laptop IP
Destination IP  = Google IP
```

So:

```text
                  FINAL DESTINATION
                         ↓
                      Google
                    142.250.x.x
                         ▲
                         │
              ┌──────────┴──────────┐
              │      IP PACKET      │
              │                     │
              │ Source IP: Laptop   │
              │ Dest IP: Google     │
              └─────────────────────┘
                         │
                         │ carried inside
                         ▼
              ┌─────────────────────┐
              │    LOCAL FRAME      │
              │                     │
              │ Source MAC: Laptop  │
              │ Dest MAC: Router    │
              └─────────────────────┘
                         │
                         ▼
                       Router
```

### In one sentence:

**The IP address tells the network the overall destination, while the MAC address helps deliver the frame to the correct interface on the current local link.**

---

# What Happens After the Router Receives It?

The router receives the frame because its MAC address was the destination MAC.

The router then forwards the IP packet toward Google.

The next hop may be another router:

```text
Laptop → Home Router → ISP Router → Other Router → Google
```

The MAC addresses are used **hop by hop**.

For example:

### Hop 1

```text
Laptop → Home Router

MAC:
Laptop → Home Router

IP:
Laptop → Google
```

### Hop 2

```text
Home Router → ISP Router

MAC:
Home Router → ISP Router

IP:
Laptop/network → Google
```

### Hop 3

```text
ISP Router → Next Router

MAC:
ISP Router → Next Router

IP:
Laptop/network → Google
```

The exact Layer 2 details vary by link technology, but the important beginner concept is:

> **MAC addressing is local/link-level. IP addressing is used for Layer 3 routing across networks.**

---

# Why Does the MAC Address Change at Each Hop?

Suppose the packet travels:

```text
Laptop
   ↓
Router A
   ↓
Router B
   ↓
Router C
   ↓
Google
```

The Layer 2 frame is rebuilt for each link.

Conceptually:

```text
Laptop → Router A
MAC: Laptop → Router A

Router A → Router B
MAC: Router A → Router B

Router B → Router C
MAC: Router B → Router C
```

The Layer 2/MAC destination is therefore about the **current hop**, not Google's ultimate destination.

The Layer 3/IP packet is what routers use to determine where the packet should go next.

---

# Why Can't We Just Use IP Everywhere?

Because IP and MAC solve different problems.

Imagine your home network has:

```text
Laptop A
IP  = 192.168.1.10
MAC = AA:AA:AA:AA:AA:10

Laptop B
IP  = 192.168.1.11
MAC = BB:BB:BB:BB:BB:11

Phone
IP  = 192.168.1.12
MAC = CC:CC:CC:CC:CC:12
```

The local network needs a way to identify the network interface that should receive a local frame.

That is where Layer 2 addressing, such as MAC addressing on Ethernet/Wi-Fi, comes in.

IP alone does not replace the Layer 2 addressing mechanism.

---

# A Simple Delivery Analogy

Think about sending a parcel from your house in Chennai to someone in Delhi.

The **final address** is like the IP destination:

```text
Delhi
```

But the parcel still has to move through intermediate delivery points:

```text
Your House
    ↓
Local Delivery Center
    ↓
Chennai Hub
    ↓
Other Hub
    ↓
Delhi Hub
    ↓
Final Destination
```

At each stage, the current delivery system needs to know:

> "Where should I send this next?"

MAC is similar to the **local/next-hop delivery information**.

IP is similar to the **overall logical destination**.

---

# MAC Address Format

A traditional MAC address is **48 bits (6 bytes)**.

Example:

```text
A4 : 5E : 60 : 12 : AB : 9F
```

There are 6 hexadecimal pairs:

```text
A4
5E
60
12
AB
9F
```

Each pair represents 1 byte:

```text
A4 = 1 byte
5E = 1 byte
60 = 1 byte
12 = 1 byte
AB = 1 byte
9F = 1 byte
```

Therefore:

```text
6 bytes × 8 bits
= 48 bits
```

---

# Important: MAC Is Not Exactly a "Physical Address"

People often call MAC a **physical address**, but this can be misleading.

A MAC address is associated with a **network interface**, and it can sometimes be changed, randomized, or spoofed by software.

For example, a laptop might have:

```text
Wi-Fi adapter → MAC address A
Ethernet adapter → MAC address B
```

So it is better to think:

> **MAC address = Layer 2 address of a network interface**

rather than simply:

> "MAC = permanent physical identity of the whole device."

---

# Quick Comparison

```text
                    MAC                    IP
----------------------------------------------------------
Layer               Layer 2               Layer 3

Main purpose        Local/link delivery   Routing

Scope               Local network/link    Across networks

Example             AA:BB:CC:11:22:33    192.168.1.10

Identifies          Network interface     Logical address

Google example      Router's MAC needed   Google's IP needed
```

---

# The Most Important Example to Remember

When your laptop opens Google:

```text
1. DNS
   google.com
       ↓
   Google's IP

2. Laptop checks destination
   Google is outside local network

3. Laptop chooses router as next hop

4. Laptop finds router's MAC
   Router IP → Router MAC

5. Laptop sends:

   MAC:
   Laptop → Router

   IP:
   Laptop → Google

6. Router forwards the packet

7. At each next hop:
   MAC = current link's next-hop interface
   IP  = continues toward Google's network
```

## Final Mental Model

```text
               IP
        "Where am I going?"
                 │
                 ▼
Laptop ───────► Router ───────► Internet ───────► Google
   │               │
   │ MAC           │ MAC
   ▼               ▼
Local delivery   Next-hop delivery
```

### Remember these 3 lines:

> **IP = logical addressing and routing**

> **MAC = local/link-level addressing**

> **You need Google's IP because you want to reach Google's network, but your laptop only needs the MAC of the next local hop (usually your router), not Google's MAC.**
