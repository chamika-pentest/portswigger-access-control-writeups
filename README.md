# portswigger-access-control-writeups
etailed write-ups of PortSwigger Web Security Academy labs focusing on access control vulnerabilities, privilege escalation, and real-world exploitation techniques using Burp Suite.

# 🧪 PortSwigger Lab Write-Up  
## User role can be modified in user profile (Apprentice)

### 📌 Lab Information
- **Lab Name:** User role can be modified in user profile  
- **Difficulty:** Apprentice  
- **Category:** Access Control / Privilege Escalation  
- **Platform:** PortSwigger Web Security Academy  

---

### 🎯 Objective
Gain unauthorized access to the `/admin` panel by escalating privileges and delete the user **carlos**.

---

### 🔐 Given Credentials
- **Username:** wiener  
- **Password:** peter  

---

### 🛠 Tools Used
- Web Browser (Chrome / Firefox)
- Burp Suite (Community / Professional)
- PortSwigger Web Security Academy Lab Environment

---

### 🧠 Vulnerability Overview
The application allows users to update profile information such as email.  
However, **sensitive parameters like `roleid` are not properly validated server-side**.

This results in:
- Access Control Misconfiguration
- Privilege Escalation
- IDOR-like behavior

---

### 🧩 Step-by-Step Exploitation

#### 1️⃣ Login
- Log in using `wiener:peter`
- Navigate to **My Account**

#### 2️⃣ Update Email
- Change the email address and submit the form

#### 3️⃣ Intercept Request
- Intercept the request using **Burp Proxy**
- Send it to **Repeater**

#### 4️⃣ Identify Role ID
- Observe the response:
```json
"roleid": 1
5️⃣ Modify Role ID

Change the request body to:

"roleid": 2


Send the request

6️⃣ Verify Privilege Escalation

Confirm role has changed to admin

7️⃣ Access Admin Panel

Visit:

/admin

8️⃣ Delete User

Delete the user carlos

✅ Lab Status

✔ Successfully Solved

🧯 Security Impact

Unauthorized privilege escalation

Full administrative access

Account takeover and user deletion

🔒 Mitigation & Recommendations

Never allow role modification from client-side input

Enforce strict server-side authorization

Implement Role-Based Access Control (RBAC)

Validate and whitelist allowed parameters

🧑‍💻 Author

Chamika Jayasooriya
Cybersecurity / Penetration Testing
