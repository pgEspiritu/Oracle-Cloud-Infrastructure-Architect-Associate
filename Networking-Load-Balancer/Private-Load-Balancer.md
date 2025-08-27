# Private Load Balancers (OCI)

## When to Use a Private Load Balancer
Use a **private load balancer** when:
- You want to **isolate your load balancer from the internet**.
- You want to **improve security posture** by ensuring the load balancer is **only accessible within your Virtual Cloud Network (VCN)**.

---

## Key Characteristics
- **Deployed in a private subnet**.
- Assigned a **private IP address**.
  - This private IP serves as the **entry point for incoming traffic**.
- **Not reachable from the internet**.
  - Accessible only from within the VCN containing the host subnet.

---

## Placement Requirements
- Unlike public load balancers:
  - A **private load balancer requires only a single subnet** to host **both the primary and standby load balancers**.
- No need for multiple subnets or regional subnet.

---

## Floating Private IP Address
- Similar to public load balancers having a *floating public IP*, private load balancers have a **floating private IP**.
- This IP is used for:
  - Routing traffic seamlessly between primary and standby load balancers.
  - Ensuring failover capability without changing client-side configurations.

---

## IP Address Requirements
A private load balancer **consumes three private IP addresses** from the host subnet:
1. One for the **primary** load balancer.
2. One for the **standby** load balancer.
3. One for the **floating private IP address**.

---

## Summary
- Private load balancers:
  - Improve security by **isolating from internet**.
  - Require only **one private subnet**.
  - Are assigned only **private IP addresses**.
  - Use a **floating private IP** for seamless failover.
- **Total IPs used**: 3 private IPs (primary, standby, floating).

