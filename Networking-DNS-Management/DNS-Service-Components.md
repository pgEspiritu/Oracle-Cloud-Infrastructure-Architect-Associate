# DNS Service Components

## Overview
DNS zones are built using several components that work together to make a domain accessible on the internet. Below are the main building blocks:

---

## Components

### 1. Domain
- A **domain** is a specific location (or group of locations) on the internet.  
- Example: `oracle.com`  
- A domain is a portion of the DNS tree delegated to a user's control.

---

### 2. Zone
- A **zone** is a portion of the DNS namespace.  
- Each zone contains:  
  - **Start of Authority (SOA) record**  
  - **Nameserver (NS) record**

---

### 3. Label
- A **label** is a part of a domain name, separated by periods (`.`).  
- Example: `www.oracle.com`  
  - `www` is the **label**.  
- Labels are prepended to the zone name to form subdomains.

---

### 4. Child Zone
- A **child zone** is an independent subdomain.  
- Each child zone has its own:  
  - **SOA record**  
  - **NS record**  
- The **parent zone** must contain a **nameserver record** pointing to the nameservers of the child zone.

---

### 5. Resource Records
Resource Records contain specific domain information for a zone. Examples include:

- **A Record**: Maps a domain name to an IPv4 address.  
- **AAAA Record**: Maps a domain name to an IPv6 address.  
- **MX Record**: Defines the mail server responsible for handling email for the domain.  
- **NS Record**: Specifies authoritative DNS servers for the zone.  
- **SOA Record**: Provides administrative information about the zone.

---

## Summary
- **Domain** → Unique location on the internet (e.g., `oracle.com`)  
- **Zone** → A part of the DNS namespace with SOA + NS records  
- **Label** → Portion of a domain name (e.g., `www` in `www.oracle.com`)  
- **Child Zone** → Independent subdomain with its own SOA and NS records  
- **Resource Records** → Data that defines the mapping and services for the domain  
