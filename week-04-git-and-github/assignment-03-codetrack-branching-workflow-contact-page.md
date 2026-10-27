# Assignment 3 — CodeTrack: Branching Workflow (Add & Verify a Contact Page)

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will add a new Contact page to CodeTrack using a clean feature-branch workflow. You will keep each change in a separate commit, prove that your default branch remains unchanged before the merge, and validate the result after merging.

---

# Task 1 — Confirm Repository State and Default Branch

## Goal

Start from a clean default branch (`main` or `master`) and confirm the repository status.

### Evidence

#### Screenshot 1 — Output of `git status` and `git branch` showing a clean status and the default branch checked out

<img width="833" height="342" alt="image" src="https://github.com/user-attachments/assets/e0c25742-63cd-4b19-86f3-a7a6a0ddb495" />


---

# Task 2 — Create and Switch to a Feature Branch

## Goal

Create a branch named exactly `feature/contact-page` and switch to it.

### Evidence

#### Screenshot 2 — Output of `git checkout -b feature/contact-page` and `git branch` showing `* feature/contact-page`

<img width="1705" height="175" alt="image" src="https://github.com/user-attachments/assets/05c04d96-04e3-43de-93cc-46df648b60b7" />


---

# Task 3 — Add contact.html on the Feature Branch

## Goal

Create `contact.html` with the provided content and commit it alone using the message `feat(contact): add Contact page`.

### Evidence

#### Screenshot 3 — Output of `ls` showing `contact.html`

<img width="1470" height="103" alt="image" src="https://github.com/user-attachments/assets/3c0b0625-19ed-4024-a558-fcc9f1504237" />


---

#### Screenshot 4 — Output of `git commit`

<img width="1815" height="185" alt="image" src="https://github.com/user-attachments/assets/b66dff4b-fd08-46bc-adc4-dae23bfe90f6" />


---

#### Screenshot 5 — Output of `git log --oneline -3` showing the new commit

<img width="1701" height="111" alt="image" src="https://github.com/user-attachments/assets/8a2f92f9-f762-43c1-9534-e4e8988a4942" />


---

# Task 4 — Add the Contact Link to index.html

## Goal

Add the provided Contact Page link to `index.html` and commit it separately using the message `feat(nav): add Contact Page link`.

### Evidence

#### Screenshot 6 — Output of `git status` showing `index.html` as modified before staging

<img width="1486" height="175" alt="image" src="https://github.com/user-attachments/assets/2d767d4b-de1b-4685-9961-4711dda05eaa" />


---

#### Screenshot 7 — Output of `git commit`

<img width="1747" height="192" alt="image" src="https://github.com/user-attachments/assets/c552c144-4841-4735-bb2b-2a29ee39e537" />


---

#### Screenshot 8 — Browser showing the Contact Page link on the homepage while on `feature/contact-page`

<img width="1600" height="903" alt="WhatsApp Image 2026-10-24 at 7 02 07 PM" src="https://github.com/user-attachments/assets/8fa57db9-15a8-401e-8c63-1a774c4294bb" />


---

# Task 5 — Verify Isolation (Prove the Default Branch Is Unchanged)

## Goal

Switch back to the default branch and confirm that `contact.html` and the Contact Page link do not exist there yet.

### Evidence

#### Screenshot 9 — Terminal showing the checkout and `ls` output, proving `contact.html` is absent

<img width="644" height="440" alt="WhatsApp Image 2026-10-14 at 11 31 09 PM" src="https://github.com/user-attachments/assets/d9691a41-2bbc-45e8-8fc1-41d7454afe51" />


---

#### Screenshot 10 — Browser showing the homepage on the default branch with no Contact Page link

<img width="1599" height="910" alt="WhatsApp Image 2026-10-27 at 6 30 35 PM" src="https://github.com/user-attachments/assets/5a6f0ea2-60ee-452f-a55b-26926ab5e157" />


---

# Task 6 — Merge the Feature Branch into the Default Branch

## Goal

Merge `feature/contact-page` into your default branch and confirm the Contact page works.

### Evidence

#### Screenshot 11 — Output of `git merge feature/contact-page`

<img width="1616" height="82" alt="image" src="https://github.com/user-attachments/assets/ad06355a-9985-4352-bc99-111c5e08ad63" />


---

#### Screenshot 12 — Output of `ls` showing `contact.html` after the merge

<img width="1505" height="93" alt="image" src="https://github.com/user-attachments/assets/288da8a6-62ef-4e86-b2d1-585a8df6cdf0" />


---

#### Screenshot 13 — Browser showing the Contact page opened from the homepage link on the default branch

<img width="716" height="436" alt="WhatsApp Image 2026-10-24 at 7 06 32 PM" src="https://github.com/user-attachments/assets/72b0234d-65c5-4fc3-9a8a-c100c772ab76" />


---

# Task 7 — Inspect History (Graph View)

## Goal

Display the repository history as a graph and locate both feature commits.

### Evidence

#### Screenshot 14 — Full output of `git log --oneline --graph --decorate --all`

<img width="1720" height="217" alt="image" src="https://github.com/user-attachments/assets/fffd9e74-d6d7-4e43-bf98-75c9db948f55" />


---

# Task 8 — Optional Cleanup (Delete the Feature Branch)

## Goal

Delete the merged `feature/contact-page` branch to keep your branch list clean.

### Evidence

#### Screenshot 15 (Optional) — Output showing `feature/contact-page` deleted and no longer listed

<img width="1532" height="190" alt="image" src="https://github.com/user-attachments/assets/2fb1126b-ab51-4ad1-9430-345b6715eac5" />


---

# Submission Instructions

- Tasks 1–7 are required; Task 8 is optional
- Add all required screenshots in your submission
- Evidence must show `contact.html` and the homepage link were absent before merging, and working after merging
- Do not expose passwords, access tokens, or private keys

---

# Completion Checklist

- [✅] Repository confirmed clean on the default branch (Screenshot 1)
- [✅]  `feature/contact-page` created and checked out (Screenshot 2)
- [✅] `contact.html` added in its own commit (Screenshots 3–5)
- [✅] Homepage Contact link added in a separate commit (Screenshots 6–8)
- [✅] Default branch proven unchanged before merge (Screenshots 9–10)
- [✅] Feature branch merged and Contact page verified (Screenshots 11–13)
- [✅] Graph history reviewed (Screenshot 14)
- [✅] Optional cleanup completed (Screenshot 15)
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
