# 📘 CIDR Blocks and Subnetting

## 🧠 What is a CIDR Prefix?

A **CIDR (Classless Inter-Domain Routing)** prefix represents an IP address or a range of IP addresses in the form: `A.B.C.D/x`


- **A.B.C.D**: Network address (IPv4)
- **/x**: Network prefix (number of bits used for network portion)

Example: `192.168.1.0/24`


## ✂️ Subnetting

Subnetting is the process of dividing a **larger network** into **smaller, more manageable subnetworks**.

> 📌 **Smaller prefix number means a larger network**  
> Example:
> - `/16` = 2^16 host addresses = **larger network**
> - `/24` = 2^8 host addresses = **smaller network**

### 🔢 Bit Allocation

- `/24`: First 24 bits are for **network**, last 8 bits for **hosts**
- `/16`: First 16 bits are for **network**, last 16 bits for **hosts**

Example:
```text
CIDR Block: 192.168.1.0/24
Network Address: First 24 bits → 192.168.1
Host Range: 192.168.1.0 to 192.168.1.255
```


## 🔍 CIDR Example in Detail

Given:
```text
IP Address: 192.168.1.2
Subnet Mask: /24 = 255.255.255.0
```

### 💡 Binary Representation

- `192` = `128 + 64`
- `192.168.1.2` in binary
- Perform a **logical AND** with the subnet mask.

### 🧮 Logical AND Explanation

Logical AND operation:

| Bit A | Bit B | A AND B |
|-------|-------|---------|
| 1     | 1     | 1       |
| 1     | 0     | 0       |
| 0     | 1     | 0       |
| 0     | 0     | 0       |

Apply this to each octet:
`192.168.1.2 AND 255.255.255.0 = 192.168.1.0`


Result:
- **Network Address** = `192.168.1.0`

## ✅ Summary

By now, you should understand:

- What CIDR prefixes are
- How subnetting works
- Why smaller prefix numbers represent larger networks
- How to calculate a network address using logical AND


