# Assignment 4 — Deploy EpicReads Portfolio Website via Nginx

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will deploy a static portfolio website on an Ubuntu VM using Nginx. You will download the website template, add your ownership proof in the footer, deploy the files to the Nginx web root, and verify the website is publicly accessible via a browser.

---

# Task 0 — Pre-flight Check

## Goal

Verify the Ubuntu VM and Nginx are ready for deployment.

### Evidence

#### Screenshot 0 — Output of `sudo systemctl status nginx --no-pager` showing Active (running)

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/450df9b4-5815-40b0-b377-519e54900763" />


---

# Task 1 — Get the Website Source Code

## Goal

Download and extract the portfolio website template.

### Evidence

#### Screenshot 1 — Output of `ls -la` showing the extracted project folder


<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/bcbfcb83-4cff-484d-9802-0977f48f4692" />



---

# Task 2 — Add Ownership Proof (Anti-Copy Change)

## Goal

Update the website footer with your deployment details.

### Evidence

#### Screenshot 2 — Nano editor open with the updated footer showing your Full Name, Group, Week, and Date

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/dc57cf81-4bd7-4941-a599-5f8d8f870a2a" />


---

# Task 3 — Deploy Website via Nginx

## Goal

Deploy the portfolio website to the Nginx web root.

### Evidence

#### Screenshot 3 — Output of `sudo nginx -t` showing configuration test successful


<img width="1452" height="175" alt="image" src="https://github.com/user-attachments/assets/eb5fe817-3025-4b82-af45-94c810e1d745" />


---

#### Screenshot 4 — Output of `ls /var/www/html` showing deployed website files


<img width="1541" height="81" alt="image" src="https://github.com/user-attachments/assets/4161e1a0-15f6-4b4c-a0b7-66e2f22f91b9" />


---

# Task 4 — Verify Website is Live

## Goal

Verify the deployed website is publicly accessible and the footer contains your details.

### Evidence

#### Screenshot 5 — Output of `curl ifconfig.me` showing the server's public IP address


<img width="1470" height="177" alt="image" src="https://github.com/user-attachments/assets/0c319e2c-6dd6-4641-af4f-613d6d6585d8" />


---

#### Screenshot 6 — Browser showing the live website with your Full Name and deployment details in the footer

<img width="716" height="412" alt="WhatsApp Image 2026-10-13 at 7 45 06 PM" src="https://github.com/user-attachments/assets/f2adec03-e2ac-4bec-892c-723c824fd2d1" />


---

# Task 5 — Mini Real DevOps Operational Check

## Goal

Verify the deployed website and Nginx service are healthy.

### Evidence

#### Screenshot 7 — Output of `systemctl is-enabled nginx`


<img width="1576" height="200" alt="image" src="https://github.com/user-attachments/assets/b9a710cf-5ddf-4d36-b212-c2e5555bbf1b" />


---

#### Screenshot 8 — Output of `curl -I http://localhost` showing 200 OK


<img width="1562" height="297" alt="image" src="https://github.com/user-attachments/assets/77e78e14-db5d-44f2-b445-2344847a4a91" />


---

# LinkedIn Post (Mandatory)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/dDEy2p-P

---

#### Screenshot — Published LinkedIn post showing the live website with your Full Name in the footer

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/2af929ad-648f-4409-a2a1-309677837744" />


---

# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- Ownership proof in the footer is mandatory
- Do not expose sensitive information (keys, passwords, account IDs)

---

# Completion Checklist

- [✅] Screenshot 0: Nginx service status (active/running)
- [✅] Screenshot 1: Website files downloaded and extracted
- [✅] Screenshot 2: Footer updated with Full Name, Group, Week, and Date
- [✅] Screenshot 3: Nginx configuration test successful
- [✅] Screenshot 4: Website files deployed to /var/www/html
- [✅] Screenshot 5: Public IP retrieved
- [✅] Screenshot 6: Live website accessible in browser with footer details
- [✅] Screenshot 7: Nginx enabled on boot
- [✅] Screenshot 8: Local HTTP response returns 200 OK
- [✅] LinkedIn post published and URL submitted
- [✅] Full Name visible in all required screenshots
- [✅] No sensitive data exposed

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme  
- 🎓 University: https://university.pravinmishra.com?utm_source=github&utm_medium=readme  
- 💬 Discord Community: https://discord.pravinmishra.com?utm_source=github&utm_medium=readme  
- 📝 Blog: https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) — Agentic AI Track.*
