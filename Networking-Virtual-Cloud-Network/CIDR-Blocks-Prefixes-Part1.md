# 📘 Understanding CIDR Block Prefixes


## 🧾 What is CIDR?

**CIDR** stands for **Classless Inter-Domain Routing**.

> In simple terms, CIDR defines a **range of IP addresses** using a standardized notation: `A.B.C.D/x`
  - `A.B.C.D` → IP address  
  - `/x` → prefix length (number of bits in the network portion)

---

## 🔢 CIDR Example

Let’s say you have the following IP range: `10.0.0.0 to 10.0.255.255`

The **CIDR notation** for this range is: `10.0.0.0/16`

This means:
- The **first 16 bits** (two octets) are fixed.
- The remaining 16 bits can vary.

---

## 🧮 Calculating Number of IPs in a CIDR Block

### ✅ Formula: 
`2^(32 - prefix_length)`

For `10.0.0.0/16`: `2^(32 - 16) = 2^16 = 65,536 IP addresses`


---

## 🧠 Understanding Octets and Binary Representation

In IPv4, an IP address consists of **4 octets**, each of 8 bits: `192.168.0.2 → 4 octets = 32 bits total`

Each bit position represents a power of 2: `128 64 32 16 8 4 2 1`


### ✏️ Binary Example

Let’s convert a few numbers into binary:

#### 10 → Binary
- 8 + 2 = 10 → bits ON at 8 and 2
- Binary: `00001010`

#### 192 → Binary
- 128 + 64 = 192
- Binary: `11000000`

#### 168 → Binary
- 128 + 32 + 8 = 168
- Binary: `10101000`

#### 0 → Binary
- All bits OFF
- Binary: `00000000`

#### 2 → Binary
- Bit ON at 2
- Binary: `00000010`

### Full IP Address Conversion
```BINARY
192.168.0.2 → Binary:
192 → 11000000
168 → 10101000
0 → 00000000
2 → 00000010
```

---

## 🏁 Summary

- **CIDR** allows compact representation of IP address ranges.
- The `/x` in CIDR denotes how many bits are fixed in the network portion.
- You can calculate the number of IPs using: `2^(32 - x)`
- Understanding **binary representation** helps decode how IPs are assigned and grouped.





