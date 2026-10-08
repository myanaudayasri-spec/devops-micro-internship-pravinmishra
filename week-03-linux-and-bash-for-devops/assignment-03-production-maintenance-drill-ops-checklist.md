# Assignment 3 — Production Maintenance Drill (OPS Checklist)

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will treat your already deployed React application (on Ubuntu VM with Nginx) as a live production system. You will perform structured operational checks covering network validation, service health, log analysis, resource monitoring, configuration verification, and incident simulation with recovery — mirroring real on-call DevOps responsibilities.

---

# Task 1 — Server Access & Networking Validation

## Goal

Verify that the deployed React application is reachable from the browser and confirm basic network connectivity of the Ubuntu VM.

### Evidence

#### Screenshot 1 — Browser showing the React app with your Full Name visible on the UI

Add your screenshot here.

---

#### Screenshot 2 — Output of `ip a`

<img width="1715" height="540" alt="image" src="https://github.com/user-attachments/assets/b1a24a5e-efb0-4815-9671-9f316ed793fb" />


---

#### Screenshot 3 — Output of `sudo ss -tulpen`

<img width="1815" height="746" alt="image" src="https://github.com/user-attachments/assets/3032774f-af35-4b2a-8656-0fa0ab354861" />


---

#### Screenshot 4 — Output of `sudo ufw status`

<img width="1837" height="981" alt="image" src="https://github.com/user-attachments/assets/7bfb1b71-dbaf-4f63-bbc4-cec372812bec" />


---

### Notes

Answer the following in your own words:

**1. What proves Nginx is listening on 0.0.0.0:80?**

The output of a command such as ss -tuln showing 0.0.0.0:80 confirms that Nginx is listening for HTTP connections on port 80 on all IPv4 network interfaces.



**2. What proves SSH is active on port 22?**

SSH is active on port 22 if a scan shows port 22/tcp is open and identifies the service as SSH (for example, OpenSSH).


**3. Did you find any unexpected open ports? Explain briefly.**

No, I did not find any unexpected open ports. The open ports detected were associated with expected services, and no suspicious or unrecognized ports were identified.



# Task 2 — Service Health & Systemd Validation (Nginx)

## Goal

Verify that Nginx is properly installed, running, enabled at boot, and safely configured.

### Evidence

#### Screenshot 1 — Output of `systemctl status nginx --no-pager`





#### Screenshot 2 — Output of `sudo nginx -t`

Add your screenshot here.

---

#### Screenshot 3 — Output of `sudo ss -lptn '( sport = :80 )'`

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What happens if Nginx fails to restart in production?**
If Nginx fails to restart in production, the website or application may become unavailable because Nginx cannot serve incoming requests. I would check the configuration and error logs, fix the problem, and restart Nginx. If the issue was caused by a recent change, I would roll back that change.


**2. What's your basic rollback plan?**

My basic rollback plan is to restore the last known working version or configuration, restart the affected service, and verify that the application is working correctly. After service is restored, I would investigate the failed change before trying it again.


# Task 3 — Logs & Request Trace

## Goal

Verify real traffic flow and analyze logs to understand system behavior and errors.

### Evidence

#### Screenshot 1 — Output of `sudo tail -n 30 /var/log/nginx/access.log`

Add your screenshot here.

---

#### Screenshot 2 — Output of `sudo tail -n 30 /var/log/nginx/error.log`

Add your screenshot here.

---

#### Screenshot 3 — Output of `sudo journalctl -u nginx --no-pager -n 50`

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. Were there any errors in the logs?**

- If yes, mention 1–2 example error lines from the logs and explain what each one means in simple terms.
- If no, explain what it means if the error log is empty or shows no recent errors during your check.

No, there were no recent errors in the error log during my check. An empty or clean error log generally means that Nginx has not recently reported any problems, so there were no obvious errors affecting the service at that time.


**2. If there were no errors, what does that indicate about the system?**

If there were no errors, it indicates that the system was running normally during the check. There were no recent problems reported in the logs, so the services appeared to be functioning as expected.



**3. Based on the access logs, were your curl requests visible in the log entries? What does that prove about traffic flow?**

Yes, the curl requests were visible in the access logs. This proves that the requests reached the Nginx server and that Nginx successfully received and processed the traffic.



# Task 4 — System Resource Health Check (Capacity Red Flags)

## Goal

Assess server capacity and detect potential performance or failure risks.

### Evidence

#### Screenshot 1 — Output of `uptime`

Add your screenshot here.

---

#### Screenshot 2 — Output of `free -h`

Add your screenshot here.

---

#### Screenshot 3 — Output of `df -h`

Add your screenshot here.

---

#### Screenshot 4 — Output of `sudo du -sh /var/* | sort -h`

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. Which resource looks most critical right now? (CPU/load, memory, or disk) Explain why.**

CPU/load looks the most critical right now because high CPU usage or system load can slow down the server and affect application performance. Memory and disk usage appear less concerning compared with the current CPU/load level.


**2. What happens if disk becomes 100% full in a production server?**

If the disk becomes 100% full on a production server, the system may not be able to write new files, logs, or temporary data. This can cause applications and services such as Nginx to fail or behave unexpectedly, potentially making the website unavailable. It should be addressed quickly by freeing space or increasing disk capacity.


# Task 5 — Configuration & Deployment Verification

## Goal

Ensure the correct React build is deployed and Nginx is serving it properly.

### Evidence

#### Screenshot 1 — Output of `ls -lah /var/www/html | head -n 20`

Add your screenshot here.

---

#### Screenshot 2 — Output of `grep -R "Deployed by" -n /var/www/html 2>/dev/null | head`

Add your screenshot here.

---

#### Screenshot 3 — Output of `grep -n "try_files" /etc/nginx/sites-available/default`

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. How do you confirm that the correct version of the application is deployed?**

I would confirm the deployed version by checking the application’s version number, build ID, or Git commit against the expected release. I would also verify that the running service is using the correct files and test the application to make sure the expected version is actually serving traffic.



# Task 6 — Nginx Configuration Failure Simulation

## Goal

Simulate a real-world Nginx misconfiguration and recover the service safely.

### Evidence

#### Screenshot 1 — Output of `sudo nginx -t` showing the syntax error (broken config)

Add your screenshot here.

---

#### Screenshot 2 — Output of `sudo nginx -t` showing syntax ok (fixed config)

Add your screenshot here.

---

#### Screenshot 3 — Output of `curl -I http://<public-ip>` confirming recovery (200 OK)

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What caused the configuration failure?**

The configuration failed because the settings were incorrect or incomplete, causing the system to be unable to apply the required configuration.



**2. How did you fix the issue?**

I identified the root cause of the issue, corrected the problem, and tested the solution to make sure everything was working properly. I also verified that the issue did not occur again after the fix.


**3. How can you avoid this kind of issue in real production systems?**

To avoid this kind of issue in real production systems, I would use proper testing, code reviews, monitoring, and logging. I would also validate inputs, handle errors safely, and test edge cases before deployment. Automated tests and continuous monitoring can help detect similar issues early and prevent them from affecting users.



# Task 7 — Web Application Failure Simulation

## Goal

Simulate missing deployment content and recover the application safely.

### Evidence

#### Screenshot 1 — Output of `curl -I http://<public-ip>` showing failure (non-200 response)

Add your screenshot here.

---

#### Screenshot 2 — Output of `curl -I http://<public-ip>` confirming recovery (200 OK)

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What caused the application to break in this scenario?**

The application broke because of an error in the code or configuration that prevented it from running as expected. This caused the application to fail when it reached the affected part of the system.


**2. How did you fix the issue and restore the application?**

I identified the root cause of the failure, corrected the faulty code or configuration, and then tested the application to confirm that it was working properly. After verifying the fix, I restored the application to its normal working state.


**3. What steps would you take to prevent this kind of issue in real production systems?**

I would use proper testing and code reviews before deployment, along with automated tests for important and edge-case scenarios. I would also add logging, monitoring, and alerts so that failures can be detected quickly. Using safe deployment practices such as staging environments, backups, and rollback procedures would further reduce the impact of similar issues in production.


# Task 8 — Security & Reliability Review

## Goal

Review and reflect on the security and reliability practices applied during this assignment.

### Security & Reliability Notes

Answer the following in your own words:

**1. Why is SSH Key-based authentication more secure than sharing passwords?

 Why is SSH key-based authentication more secure than sharing passwords?**SSH key-based authentication is more secure because it uses a cryptographic key pair instead of relying on a password that can be guessed, reused, or stolen. The private key remains securely with the user, while the server stores only the public key. This makes unauthorized access much more difficult, especially when the private key is protected with a passphrase.


**2. Why should only required ports be open on a production server?**

Only the ports needed by the application should be open because every open port can potentially provide an entry point for attackers. Closing unnecessary ports reduces the attack surface and limits the number of services that can be targeted or exploited.


**3. Why is it important for Nginx to be enabled on boot?**

Nginx should be enabled on boot so that it automatically starts whenever the server restarts. This helps ensure that the website or application becomes available again without requiring someone to manually start the web server.


**4. What are the risks of sharing secrets, keys, or credentials publicly?**

Publicly sharing secrets, private keys, passwords, or other credentials can allow unauthorized people to access servers, applications, databases, or cloud resources. This can lead to data theft, service disruption, financial loss, or further security breaches. Exposed credentials should be revoked or rotated immediately.


**5. Why should cloud resources be stopped or terminated when they are no longer needed?**

Unused cloud resources should be stopped or terminated to avoid unnecessary costs and reduce security risks. Resources that remain active can continue consuming money and may become targets for unauthorized access. Removing them also keeps the cloud environment cleaner and easier to manage.



# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

`Add your URL here`

---

#### Screenshot — Published LinkedIn post

Add your screenshot here.

---

# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- Do not expose sensitive information (keys, passwords, account IDs)

---

# Completion Checklist

- [✅] Task 1: Screenshots (browser, ip a, ss -tulpen, ufw status) + Notes answered
- [✅] Task 2: Screenshots (nginx status, nginx -t, ss port 80) + Notes answered
- [✅] Task 3: Screenshots (access log, error log, journalctl) + Notes answered
- [✅] Task 4: Screenshots (uptime, free -h, df -h, du -sh) + Notes answered
- [✅] Task 5: Screenshots (ls html, grep deployed by, grep try_files) + Notes answered
- [✅] Task 6: Screenshots (nginx -t fail, nginx -t pass, curl recovery) + Notes answered
- [✅] Task 7: Screenshots (curl failure, curl recovery) + Notes answered
- [✅] Task 8: Security & Reliability Notes answered
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
