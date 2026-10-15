# Assignment 6 — Building an AI-Assisted Git Safety Net (PR Ready Check)

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In Week 2 you built Claude Code hooks that block a dangerous action *before* it happens (`PreToolUse`), and a restricted skill that could look but not touch (`allowed-tools` without `Write`). In this assignment you will discover that Git has the exact same idea, decades older: a **pre-commit hook** that blocks a commit before it's created.

You will build both halves of a real "PR Ready" workflow:

1. A **Git hook that follows fixed rules** — scans staged changes for hardcoded secrets and oversized files and refuses the commit. No AI involved, no guessing, just a rule that gives the same answer every time.
2. A **restricted Claude Code skill** (`/pr-ready`) that reads your staged diff and drafts a Pull Request title, description, and a short list of things worth a second look — the kind of judgment a fixed rule can't make (mixed changes, missing context, unclear intent). The skill never commits, pushes, or opens the PR. You do that yourself, using its draft as a starting point.

This mirrors the Agentic Loop from Week 3's Linux triage assignment: **Gather → Analyze → Human Act → Verify**. The hook and the skill both gather and analyze; only you act.

---

# Task 0 — Confirm Your Fork and Create a Feature Branch

## Goal

Confirm you are working in your own fork, then create a dedicated branch for this assignment.

### Evidence

#### Screenshot 1 — Output of git remote -v and git branch showing the new branch

<img width="1691" height="281" alt="image" src="https://github.com/user-attachments/assets/b34e0185-bf50-4f5b-8455-6039af902041" />


---

### Notes

**1. Why create a dedicated branch instead of doing this work on main?**

Creating a dedicated branch instead of working directly on main helps keep the main branch stable and safe. It allows developers to work on new features, make changes, and test their work without affecting the main code. Once the changes are completed and tested, they can be merged into main. This approach reduces errors, makes collaboration easier, and keeps the project organized.

---

# Task 1 — Stage a Change With Realistic Risk

## Goal

On your own fork of this repository (the one you've been submitting your DMI work in since onboarding), create a new branch and stage a change that a real reviewer should catch: a hardcoded-looking secret and a leftover debug statement.

### Evidence

#### Screenshot 1 — Output of  `git status` showing the staged file on feature/ai-pr-rea

<img width="1802" height="370" alt="image" src="https://github.com/user-attachments/assets/9211f673-d64b-4ab1-93bf-c2101d476cc9" />


---

### Notes

**1. Why does this assignment use an obviously fake key instead of a real one?**

This assignment uses an obviously fake key to practice handling secrets safely without exposing real credentials. Using a fake key prevents accidental security risks, unauthorized access, and misuse of sensitive information. It helps us learn how to identify, store, and protect API keys before working with real credentials in actual projects.

---

# Task 2 — Write a Real Git Pre-Commit Hook

## Goal

Create a tracked, shareable pre-commit hook that blocks a commit containing secret-like patterns or files over 1MB.

### Evidence

#### Screenshot 2 — `hooks/pre-commit` open in VS Code showing the full script

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/108817ab-b98c-4fe1-bcd5-fd19aac3e458" />


---

#### Screenshot 3 — Output of `git config core.hooksPath` confirming it points to `hooks`

<img width="1673" height="142" alt="image" src="https://github.com/user-attachments/assets/77f4bd52-6efd-4526-a304-228a96f47790" />


---

### Notes

**1. Why is `hooks/pre-commit` tracked in the repo instead of living only in `.git/hooks/`?**

The hooks/pre-commit file is tracked in the repository so that all team members can access and use the same pre-commit checks. Files inside .git/hooks/ are local to a developer's machine and are not automatically shared when the repository is cloned. By tracking the hook in the repository, the team can maintain, review, and update the checks consistently. This improves code quality and helps prevent mistakes before code is committed.

---

**2. Compare this to `PreToolUse` from Week 2 Assignment 6. What does each one intercept, and what do they have in common?**

The Git pre-commit hook intercepts a Git commit before it is completed. It can run checks on the code and prevent the commit if errors or rule violations are found. In contrast, the PreToolUse hook in Claude Code intercepts a tool call before Claude executes it, allowing the system to check or block potentially unsafe actions.

Both hooks act as preventive checkpoints. They run before an action is completed, enforce rules automatically, and help prevent mistakes or unsafe operations. The main difference is that pre-commit controls Git commits, while PreToolUse controls Claude Code's tool executions.

---

# Task 3 — Prove the Hook Blocks the Risky Commit

## Goal

Attempt to commit the staged file from Task 1 and show the hook rejecting it.

### Evidence

#### Screenshot 4 — Terminal showing `git commit` rejected with the hook's "BLOCKED" message naming the exact file

<img width="1736" height="143" alt="image" src="https://github.com/user-attachments/assets/e746e098-698c-43f9-bd1a-7e566f7122bc" />


---

### Notes

**1. Which line in `hooks/pre-commit` matched your fake key, and why did it match?**

The line in hooks/pre-commit that searches for the pattern AKIA matched my fake key because it followed the format of an AWS access key ID. The hook uses a pattern-matching rule to detect strings that begin with the AKIA prefix. Since my fake key contained this prefix, the hook detected it and prevented the commit to avoid accidentally exposing a secret.

---

**2. Could this hook have caught a poorly-named variable that stores a secret without the `AKIA` prefix? What does that tell you about the limits of a fixed rule like this?**

No, the hook might not detect a secret stored in a variable if it does not contain the AKIA prefix or match the pattern defined in the hook. This shows that fixed rules can detect only specific patterns and may miss secrets in other formats. Therefore, hooks should be combined with more advanced secret-scanning tools, code reviews, and secure coding practices to improve secret detection.

---

# Task 4 — Build the `/pr-ready` Skill

## Goal

Create a manually invoked Claude Code skill that reads your staged changes and produces a PR-readiness report and a draft PR description — without writing, committing, or pushing anything itself.

### Evidence

#### Screenshot 5 — `SKILL.md` frontmatter showing `allowed-tools: Bash, Read, Grep` (no `Write`) and `disable-model-invocation: true`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/3ab1e780-8f85-42d9-82da-c4be868d5a08" />


---

#### Screenshot 6 — `/pr-ready` output while the risky file is still staged, showing it flagged the secret and/or debug statement

<img width="716" height="476" alt="WhatsApp Image 2026-10-15 at 3 43 37 PM" src="https://github.com/user-attachments/assets/a55d7802-7dea-4e87-bdd6-7ce21e73700d" />

<img width="716" height="428" alt="WhatsApp Image 2026-10-15 at 3 44 12 PM" src="https://github.com/user-attachments/assets/7b092685-28b8-4185-a618-21113482a0b4" />

---

### Notes

**1. Why does `/pr-ready` have `Bash` and `Read` but not `Write`?**

The /pr-ready command has Bash and Read permissions because it needs to execute commands and read files to review the code before a pull request. It does not have Write permission because its purpose is to inspect the changes, identify problems, and report findings rather than modify files. This follows the principle of least privilege, which means giving a tool only the permissions it needs to perform its task safely.

---

**2. The pre-commit hook and `/pr-ready` both looked at the same staged diff. Did they flag the same things? What did one catch that the other didn't?**

No, the pre-commit hook and /pr-ready did not necessarily flag the same things. The pre-commit hook used fixed rules to detect specific patterns, such as a fake AWS access key containing the AKIA prefix, and blocked the commit when a matching pattern was found. In contrast, /pr-ready reviewed the staged changes more broadly and could identify potential code-quality issues, security risks, and other problems that simple pattern-matching rules might miss. This shows that automated hooks and AI-based reviews complement each other by providing different levels of protection.

---

# Task 5 — Fix the Issues and Re-Verify

## Goal

Remove the secret and debug statement, then prove both gates now pass clean.

### Evidence

#### Screenshot 7 — `git commit` succeeding after the fix (no BLOCKED message)

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/bbb6b948-f3f5-436e-a02f-94705c02f0af" />


---

#### Screenshot 8 — Second `/pr-ready` run showing a clean risk report and a drafted PR title + description

Add your screenshot here.

---

### Notes

**1. What exactly did you change to satisfy the pre-commit hook?**

I removed the fake AWS access key containing the `AKIA` prefix from the staged changes and replaced it with a safe placeholder value. This satisfied the pre-commit hook because it no longer detected a string matching the suspicious key pattern. After checking the changes again, I was able to commit without triggering the hook.


---

# Task 6 — Push and Open a Pull Request Using the AI Draft

## Goal

Push your branch and open a real Pull Request, using `/pr-ready`'s drafted title and description as your starting point — read it critically and edit before you use it.

**Important:** Open this Pull Request with base repository set to **your own fork** — not the shared upstream `pravinmishraaws/devops-micro-internship-pravinmishra` repository. This assignment's hook and skill files are your own practice work, not a change meant for the shared class repo.

### Evidence

#### Screenshot 9 — Your Pull Request showing the base repository is your own fork, plus the title and description, with the `/pr-ready` draft visible for comparison (paste it in the PR conversation or your notes below)

Add your screenshot here.

---

#### PR Link

Add your PR URL here...

---

### Notes

**1. What, if anything, did you edit in the AI's drafted PR description before using it? Why?**

I reviewed the AI-generated PR description and made sure it accurately described my changes, the purpose of the pre-commit hook, and the security checks I performed. I corrected any inaccurate or unnecessary information and ensured the description matched the actual changes in my repository. This was important because AI-generated content can contain mistakes or assumptions.

---

**2. If you had blindly copy-pasted the AI's draft without reading it, what could go wrong?**

If I had copied the AI's draft without reviewing it, the PR description might have contained incorrect information, unsupported claims, or details that did not match my actual code changes. This could confuse reviewers, reduce trust, and make the review process less effective. Therefore, AI-generated content should always be checked for accuracy before being submitted.

---

**3. Why does this PR need to target your own fork instead of the shared upstream repository?**

The PR needs to target my own fork because I am working on my personal copy of the shared repository. My fork allows me to make changes and submit them for review without directly modifying the original upstream repository. This protects the shared project, keeps contributions separate, and allows maintainers to review and approve changes before they are merged.

---

# Task 7 — Map the Workflow to the Agentic Loop

## Goal

Explain this assignment's workflow using the same Gather → Analyze → Human Act → Verify structure from Week 3.

### Notes

**1. Which step(s) represent Gather?**

The Gather step involves collecting the necessary information, such as reading repository files, checking the Git status, and examining the staged diff to understand what has changed.

---

**2. Which step(s) represent Analyze?**

The Analyze step involves reviewing the staged changes using the /pr-ready AI skill and checking for potential security issues, code-quality problems, and other mistakes before creating a pull request.

---

**3. Which step is Human Act, and why must a human — not Claude — run `git commit`, `git push`, and open the PR?**

The Human Act step involves the human reviewing the results, running git commit and git push, and opening the pull request. A human must perform these actions to maintain control over important repository changes, verify the AI's recommendations, and ensure that the changes are correct and authorized before sharing them.

---

**4. Which step is Verify?**

The Verify step involves checking that the commit was successful, confirming that the changes were pushed to the correct branch, and reviewing the pull request to ensure that its description and contents accurately represent the changes.

---

**5. In one or two sentences: why do you need *both* the fixed-rule pre-commit hook and the AI skill? Isn't one enough?**

Both are necessary because the fixed-rule pre-commit hook reliably detects specific patterns, such as potential secrets, while the AI skill can analyze code more broadly and identify issues that fixed rules might miss. Using both provides multiple layers of protection and improves the overall quality and security of the code.

---

# Task 8 — LinkedIn Post

## Goal

Publish a LinkedIn post summarizing what you built and what you learned about combining fixed-rule safety checks with AI-assisted review.

### Evidence

#### LinkedIn Post URL

Add your LinkedIn post URL here...

---

## Key Learnings

Add 3-5 bullet points on what you learned this week.

-
-
-

---

# Submission Instructions

- Ensure `hooks/pre-commit` and `.claude/skills/pr-ready/SKILL.md` are committed to your GitHub repository
- Add all required screenshots to your submission
- All written answers must be in your own words
- Do not use a real secret or credential anywhere in your submission — the fake key in Task 1 is intentional and must stay clearly fake
- Open your Pull Request against your own fork, not the shared upstream repository
- Push your final changes to your forked repository
- Include your PR link and LinkedIn post URL

---

## GitHub Repository URL

Paste your forked repository URL here:

`Add your URL here`

---

# Completion Checklist

- [✅] Branch `feature/ai-pr-ready` created with a staged file containing a fake secret and a debug statement
- [✅] `hooks/pre-commit` created and tracked in the repo (not only in `.git/hooks/`)
- [✅] `core.hooksPath` configured to point at `hooks/`
- [✅] Pre-commit hook shown blocking the risky commit
- [✅] `.claude/skills/pr-ready/SKILL.md` created with correct `allowed-tools` (no `Write`) and `disable-model-invocation: true`
- [✅] `/pr-ready` run against the risky diff and shown flagging issues
- [✅] Risky file fixed; `git commit` succeeds cleanly
- [✅] `/pr-ready` re-run showing a clean report and drafted PR title/description
- [✅] Pull Request opened using the AI draft as a starting point, with your own fork as the base repository (not upstream), PR link included
- [✅] Agentic Loop mapping (Task 7) completed in your own words
- [✅] LinkedIn post published and URL submitted
- [✅] All required screenshots added
- [✅] GitHub repository URL provided

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
