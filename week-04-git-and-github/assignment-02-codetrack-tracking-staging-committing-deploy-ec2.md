# Assignment 2 — CodeTrack: Tracking, Staging, Committing + Deploy to EC2

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will track and stage project files, create two meaningful Git commits in `CodeTrack`, verify your commit history, and deploy the CodeTrack static website to an EC2 instance using Nginx. This connects local version-control practice with a basic manual deployment workflow used in real DevOps environments.

---

# Task 1 — Verify Git Setup and Enter the Repository

## Goal

Confirm that Git works and that you are inside the correct `CodeTrack` repository.

### Evidence

#### Screenshot 1 — Output of `pwd` showing you're inside `CodeTrack`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/31633a83-a9f4-4114-89d4-085208d90d24" />


---

#### Screenshot 2 — Output of `git status` showing no "not a git repository" error

<img width="743" height="177" alt="image" src="https://github.com/user-attachments/assets/9b41f65e-4139-4936-99d5-bcc8cd11730a" />


---

# Task 2 — Create index.html and style.css

## Goal

Create the two starter UI files inside `CodeTrack`.

### Evidence

#### Screenshot 3 — Output of `ls` showing `index.html` and `style.css`

<img width="663" height="97" alt="image" src="https://github.com/user-attachments/assets/f029233d-bd8d-4e4d-98ac-77bab9886b23" />


---

# Task 3 — Add Starter Content

## Goal

Copy the provided starter HTML and CSS content into your local `index.html` and `style.css` files.

### Evidence

#### Screenshot 4 — Your editor showing the contents of `index.html` and `style.css`

<img width="716" height="448" alt="WhatsApp Image 2026-10-15 at 4 12 45 PM" src="https://github.com/user-attachments/assets/a10200eb-fe8f-4187-89e5-ac173e7ce26f" />

<img width="716" height="476" alt="WhatsApp Image 2026-10-15 at 4 13 45 PM" src="https://github.com/user-attachments/assets/d8815728-9aef-4943-843a-51e389e552ad" />

---

# Task 4 — Track and Stage Files Correctly

## Goal

Confirm both files show as untracked, then stage them individually with `git add`.

### Evidence

#### Screenshot 5 — Output of `git status` showing both files as untracked

<img width="1550" height="442" alt="image" src="https://github.com/user-attachments/assets/3c4f33c2-adf3-48aa-864f-c60a38c31210" />


---

#### Screenshot 6 — Output of `git status` showing both files staged under "Changes to be committed"

<img width="782" height="397" alt="image" src="https://github.com/user-attachments/assets/823ec790-8afc-4619-89d8-2cb3dcd2dbe8" />


---

# Task 5 — Create the First Commit (Clean Initial Commit)

## Goal

Commit the staged starter files using the message `Initial UI scaffold: add index.html and style.css`, then check the log.

### Evidence

#### Screenshot 7 — Output of `git commit`

<img width="1837" height="280" alt="image" src="https://github.com/user-attachments/assets/b31da6fa-6d4d-40df-83f9-ae6c1303369f" />


---

#### Screenshot 8 — Output of `git log --oneline` showing the first commit

<img width="1586" height="222" alt="image" src="https://github.com/user-attachments/assets/5942ff1f-978f-4767-8fe8-5b24400ef668" />


---

# Task 6 — Modify index.html and Create a Second Commit

## Goal

Follow the instruction comment inside `index.html` to update the Student Name and Group Name, then commit that change separately using the message `Update homepage content: heading, tagline, CTA button`.

### Evidence

#### Screenshot 9 — Browser showing the updated page with your Student Name and Group Name visible

<img width="1327" height="1186" alt="WhatsApp Image 2026-10-15 at 4 20 43 PM" src="https://github.com/user-attachments/assets/0f3caa65-eb0d-41e9-950d-7a9376f3c6e0" />


---

#### Screenshot 10 — Output of `git status` showing `index.html` as modified

<img width="1432" height="398" alt="image" src="https://github.com/user-attachments/assets/20472849-d6d6-4bf1-8cbe-97d35eb5e047" />


---

#### Screenshot 11 — Output of `git commit`

 <img width="1432" height="398" alt="image" src="https://github.com/user-attachments/assets/20472849-d6d6-4bf1-8cbe-97d35eb5e047" />

---

#### Screenshot 12 — Output of `git log --oneline` showing two commits

<img width="1532" height="286" alt="image" src="https://github.com/user-attachments/assets/37b749fe-7ab3-4438-816a-bebad42bd5cd" />


---

# Task 7 — Deploy to EC2 with Nginx (Static Website)

## Goal

Install and start Nginx on your EC2 instance, then copy `index.html` and `style.css` into the Nginx web root.

### Evidence

#### Screenshot 13 — Output of `systemctl status nginx --no-pager` showing Nginx `active (running)`

<img width="1787" height="728" alt="image" src="https://github.com/user-attachments/assets/0f43a575-9232-4a75-9316-8f3a29c70e26" />


---

#### Screenshot 14 — Output of `curl -I http://localhost` showing `HTTP/1.1 200 OK`

<img width="1692" height="312" alt="image" src="https://github.com/user-attachments/assets/f451099e-a11c-4a5a-81ce-e95a640b2320" />


---

#### Screenshot 15 — Browser showing the CodeTrack site loaded at `http://<EC2_PUBLIC_IP>`, with your Full Name and Group Name visible

Add your screenshot here.

---

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/dmFr2wFi

---

#### Screenshot — LinkedIn post showing the deployed CodeTrack application

<img width="1620" height="942" alt="image" src="https://github.com/user-attachments/assets/3e2ad153-8fca-4e75-823a-834950447b56" />


---

# Submission Instructions

- Add all required screenshots in your submission
- Full Name and Group Name must be visible in the deployed application evidence
- `git log --oneline` output must show at least two meaningful commits
- Do not expose AWS access keys, passwords, private key contents, or other sensitive information

---

# Completion Checklist

- [✅] `CodeTrack` repository verified with `git status` (Screenshots 1–2)
- [✅] `index.html` and `style.css` created and populated (Screenshots 3–4)
- [✅] Starter files staged and committed in the first commit (Screenshots 5–8)
- [✅] Student Name and Group Name updated in `index.html` (Screenshot 9)
- [✅] Second controlled commit created (Screenshots 10–12)
- [✅] Nginx active on the EC2 instance and CodeTrack reachable via its public IP (Screenshots 13–15)
- [✅] LinkedIn post published and URL submitted
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
