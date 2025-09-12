# 🖼️ Demonstration: Create and Use a Custom Image in OCI  

In this demonstration, we will create a **custom image** from an existing instance and then use it to launch a new instance.  

---

## Step 1: Existing Instance with Apache 🌐  
- Previously launched instance: `demoinstance`  
- Apache web server installed and serving a test page  

---

## Step 2: Create a Custom Image ⚡  
1. Go to **More Actions → Create Custom Image**  
2. A message appears:  
   > *The instance will be taken offline for several minutes during the imaging process.*  
   - ✅ Best practice: Manually shut down the instance before creating a custom image  
3. Specify a name (e.g., `ociaa-custom-image`)  
4. Click **Create Custom Image**  
5. Instance state changes to **Creating Image**, then back to **Running**  

---

## Step 3: Verify Custom Image ✅  
- Navigate to **Compute → Custom Images**  
- Confirm the new image (`ociaa-custom-image`) is listed  

---

## Step 4: Launch an Instance from Custom Image 🚀  
1. Click **Create Instance**  
2. Name it (e.g., `instance-customimage`)  
3. Under **Image and Shape → Change Image → Custom Images**, select the custom image  
4. Keep default networking and settings  
5. Skip SSH key pair option  
6. Click **Create**  

---

## Step 5: Validate the Instance 🔎  
- Copy the public IP and open in a browser → Apache test page appears 🌐  
- Attempt SSH connection:  
  - Works successfully ✅ because the custom image carries over previous configurations  

---

## 🎯 Summary  
- Created a custom image from an existing instance  
- Launched a new instance using the custom image  
- Verified both web server accessibility and SSH connectivity  

---
