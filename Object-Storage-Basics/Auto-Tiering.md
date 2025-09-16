# 🔄 OCI Object Storage Auto-Tiering

## 📌 Recap of Storage Tiers
- **Standard Tier**
  - ⚡ Fast, frequent access
  - 🚫 No retrieval charges
  - 🚫 No retention requirements  

- **Infrequent Access Tier**
  - ⏳ Optimized for infrequent access
  - 💲 Lower storage cost than Standard
  - 📅 31-day minimum retention
  - 💵 Retrieval fees apply  

---

## 🤖 What is Auto-Tiering?
Auto-Tiering automatically moves objects between **Standard** and **Infrequent Access** tiers based on **access patterns**.

- 📊 Monitors how data is accessed  
- 🔁 Moves infrequently accessed objects → **Infrequent Access tier**  
- 🔁 Moves frequently accessed objects back → **Standard tier**  
- 🪣 Enabled **at the bucket level**  
- 📦 Applies to objects **larger than 1 MiB**  

---

## 💡 Benefits
- ⏱️ Saves time (no need for complex lifecycle policies)  
- 💲 Reduces cost automatically  
- 📉 Pro-rated storage costs  
- 🚫 No retrieval charges when objects move between tiers  

---

## 🛠️ Use Cases
- 🆕 **New applications** with unknown access patterns  
- 🔄 **Changing workloads** where access frequency varies over time  

---

## ✅ Key Takeaway
Auto-Tiering = **Hands-free cost optimization**  
- Smart tier assignment  
- Reduced storage cost  
- No manual rules required  
