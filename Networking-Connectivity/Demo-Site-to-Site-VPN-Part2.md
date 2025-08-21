# Demonstration: Site-to-Site VPN (Part 2)

## 🔹 Step 1: Configure Shared Secrets
1. Open **tunnel1**
   - Under *Tunnel Information*, click **Edit**
   - Set **Shared Secret** → `secret1`
   - Save changes
2. Open **tunnel2**
   - Set **Shared Secret** → `secret2`
   - Save changes

➡️ Both tunnels now show **Lifecycle State = Available**, but **IPSec Status = Down** (because IPSec files are not yet configured on CPE).

---

## 🔹 Step 2: Connect to CPE VM in Ashburn
- Use **Cloud Shell** to SSH into `cpevm`
- Install **Libreswan**  
  ```bash
  sudo yum install libreswan -y
  ```
- Confirm installation success

---

## Step 3: Configure IPSec Files
1. Update sysctl.conf
- Modify system parameters to support IPSec
- Apply changes:
  ```bash
  sudo sysctl -p
  ```
- Configure IPSec Main Config
Set:
  - Public IP of CPE VM
  - Tunnel1 IP address
  - Tunnel2 IP address
  - Shared Secrets (`secret1`, `secret2`)
- Example (simplified snippet):
  ```conf
  conn tunnel1
    left=%defaultroute
    leftid=<CPE-VM-Public-IP>
    right=<OCI-Tunnel1-Public-IP>
    psk=secret1

  conn tunnel2
      left=%defaultroute
      leftid=<CPE-VM-Public-IP>
      right=<OCI-Tunnel2-Public-IP>
      psk=secret2
  ```

3. Configure Tunnel-Specific Files
Define:
 - Private IP of CPE VM
 - Public IP of CPE VM
 - Tunnel1 & Tunnel2 Public IPs

---

## 🔹 Step 4: Restart IPSec Service
```bash
sudo systemctl restart ipsec
```

---

## Step 5: Verify Tunnel Status
- Add routes to OCI as needed
- Check Phoenix Region → IPSec Connection
- ✅ Status changes to UP

---

## ✅ Summary of Part 2

- Configured shared secrets for both tunnels
- Installed Libreswan on the CPE VM
- Created and updated IPSec configuration files
- Restarted the IPSec service
- Verified that the IPSec tunnels are UP
