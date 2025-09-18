# 🔐 Securing OCI Object Storage

## 🏁 Initial Security Tasks

- **IAM Policies** → Grant access to specific users and resources.  
- **Network Source Restrictions** → Limit access to requests originating from allowed IP addresses.  
- **Prevent Deletion** → Protect buckets and objects from accidental or malicious deletion.  
- **Encryption Keys** →  
  - Default keys are auto-generated.  
  - Recommended: create & manage **custom keys** in **OCI Vault**.  
- **Network Security** →  
  - Data in transit is encrypted with **TLS 1.2 by default**.  
- **Security Zones** → Ensure storage complies with **OCI security best practices**.  

---

## 🔄 Routine Security Tasks

- **Key Rotation** →  
  - Vault assigns each master encryption key a version.  
  - Rotation generates a **new version**, limiting exposure.  
  - Helps reduce risk if a key is compromised.  

- **Security Audit** →  
  - **Audit Service** automatically records all API calls.  

- **Data Protection Strategies** →  
  - Enable **Object Versioning** to reduce risk from accidental/malicious deletions.  
  - Restrict **BUCKET_DELETE** and **OBJECT_DELETE** permissions to minimal IAM groups.  

- **Data Integrity** →  
  - Every uploaded object has an **MD5 checksum**.  
  - Verify uploaded objects:  
    - Compare offline MD5 checksum with console/API checksum.  

- **Retention Rules** →  
  - Configure to protect objects from premature deletion.  

---

## ✅ Key Takeaways

- Use **IAM, network sources, and encryption** for strong security foundations.  
- Regularly **rotate keys, audit activity, and verify object integrity**.  
- Apply **versioning and retention rules** to minimize data loss.  
- Always **follow least privilege principles** for delete permissions.  
