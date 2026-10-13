# Assignment 5 — Bash Script Automation Drill (OPS Checklist)

Part of the DevOps Micro Internship (DMI) with Agentic AI

---

## Purpose

In this assignment, you will practice Bash scripting by building a series of small automation scripts covering environment setup, variables, arrays, loops, file conditionals, if-else logic, and functions. These scripts form the foundation of real-world Linux automation used in DevOps, cloud, and production support environments.

---

# Task 1 — Bash Environment & Workspace Setup

## Goal

Verify that Bash is available on your system and create a clean workspace for this assignment.

### Evidence

#### Screenshot 1 — Output of `echo $SHELL` and `bash --version`

<img width="1777" height="358" alt="image" src="https://github.com/user-attachments/assets/68142c0b-fefe-4562-86d6-08b2608a0266" />


---

#### Screenshot 2 — Output of `pwd` and `ls -lah` showing the scripts director 

<img width="1835" height="496" alt="image" src="https://github.com/user-attachments/assets/6cdc585d-19f6-48a2-9beb-0243cef03c3f" />
     
---

### Notes

Answer the following in your own words:

**1. What is Bash?**

Bash stands for Bourne Again SHell. It is a command-line shell used in Linux and other operating systems to run commands, manage files, execute programs, and automate tasks using scripts.


**2. What is the difference between shell and Bash?**

A shell is a general program that provides a command-line interface between the user and the operating system. Bash is one specific type of shell. Other shells include Zsh, Fish, and the Korn shell. Therefore, Bash is a shell, but not every shell is Bash.


**3. Why is it important to confirm the Bash version before writing scripts?**

It is important to check the Bash version because different versions may support different features and syntax. Knowing the version helps ensure that the commands and features used in a script are compatible with the target system and prevents unexpected errors when the script runs.


# Task 2 — Your First Bash Script

## Goal

Create your first Bash script, make it executable, and run it from the terminal.

### Evidence

#### Screenshot 1 — Content of `first-script.sh`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/cc97a1d0-cd00-44bb-b80a-9f779cac9be5" />


---

#### Screenshot 2 — Output of `./first-script.sh`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/b0af740c-18fe-4104-af8e-4d6c426880c9" />


---

#### Screenshot 3 — Output of `ls -l first-script.sh` showing executable permission

<img width="791" height="82" alt="image" src="https://github.com/user-attachments/assets/934f298f-ea41-47ef-b60c-c325edc478a3" />


---

### Notes

Answer the following in your own words:

**1. What is the purpose of `#!/bin/bash`?**

#!/bin/bash is called a shebang. It tells the operating system to use the Bash interpreter to execute the script when the script is run directly.

**2. Why do we use `chmod +x` before running a script?**

chmod +x gives the script execute permission. Without this permission, the script usually cannot be run directly using ./script.sh.

**3. What is the difference between running a script using `./script.sh` and `bash script.sh`?**

./script.sh runs the script directly, so the system uses the interpreter specified in the shebang, such as #!/bin/bash. It also requires the script to have execute permission.

bash script.sh explicitly starts Bash and passes the script to it, so execute permission is not required and the shebang is not used to choose the interpreter.

# Task 3 — Variables: User Information Script

## Goal

Use variables to store and display user-related information.

### Evidence

#### Screenshot 1 — Content of `user-info.sh`

<img width="650" height="113" alt="image" src="https://github.com/user-attachments/assets/c2ecee6a-5fc0-4643-baa6-3249b7ed8691" />


---

#### Screenshot 2 — Output of `./user-info.sh`

<img width="728" height="155" alt="image" src="https://github.com/user-attachments/assets/566a6f94-83c5-43ee-a1d6-d2f0bde91dcb" />


---

### Notes

Answer the following in your own words:

**1. What is a variable in Bash?**

A variable in Bash is a named place used to store a value, such as text, numbers, or other information. The value can be used later in the script.

**2. Why should we avoid spaces around the `=` sign when creating variables?**

Bash does not allow spaces around the = sign when assigning a value to a variable. For example, name="John" is correct, while name = "John" is interpreted as a command and causes an error.

**3. How do you access the value stored inside a Bash variable?**

You access the value of a Bash variable by placing a $ before its name. For example, if name="John", using $name will return the value John.

# Task 4 — Arrays & Loops: Tools Checklist Script

## Goal

Use arrays and loops to print a checklist of tools used in Bash scripting.

### Evidence

#### Screenshot 1 — Content of `tools-checklist.sh`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/50c7fabd-9ea0-4373-a751-cfd3b6890f5e" />


---

#### Screenshot 2 — Output of `./tools-checklist.sh`

<img width="907" height="152" alt="image" src="https://github.com/user-attachments/assets/8917f6e5-d5da-4e00-aba2-67eb676406a1" />


---

### Notes

Answer the following in your own words:

**1. What is an array in Bash?**

An array in Bash is a variable that can store multiple values under one name. Each value is stored at a different index, starting from 0.


**2. Why are arrays useful in scripts?**

Arrays are useful because they allow a script to store and manage multiple related values together. This makes it easier to process a list of items without creating a separate variable for each one.


**3. What does `"${tools[@]}"` mean?**

"${tools[@]}" refers to all the elements stored in the tools array. When used inside quotes, each array element is treated as a separate value, which is useful for safely processing every item.


**4. What is the purpose of the `for` loop in this script?**

The for loop is used to go through each item in the array one at a time and perform the required commands on each item. This avoids repeating the same code manually for every value.


# Task 5 — Loops: Number Counter Script

## Goal

Use loops to repeat a task multiple times.

### Evidence

#### Screenshot 1 — Content of `counter.sh`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/76bad106-db11-409c-b239-382374c9a44c" />


---

#### Screenshot 2 — Output of `./counter.sh`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/1bfeb942-0598-4bd0-8f80-c82e2ca5f9e5" />


---

### Notes

Answer the following in your own words:

**1. What is a loop?**
A loop is a programming structure that repeatedly executes a set of commands until a specified condition is met or a certain number of repetitions is completed.


**2. Why do we use loops in Bash scripting?**

Loops are used in Bash scripting to repeat tasks automatically. They reduce the need to write the same commands multiple times and make scripts shorter, easier to maintain, and more efficient.


**3. How many times did the loop run in your script?**

The loop ran 5 times in my script, once for each iteration specified in the loop.


**4. What would you change if you wanted the loop to run 10 times?**

I would change the loop's range or condition so that it goes from 1 to 10 instead of 1 to 5. For example, in a Bash for loop, I could use for i in {1..10}.


# Task 6 — Files & Conditionals: File Validation Script

## Goal

Use file checks and conditionals to verify whether files and directories exist.

### Evidence

#### Screenshot 1 — Output of `ls -lah ../test-folder`

<img width="647" height="105" alt="image" src="https://github.com/user-attachments/assets/a4a13452-e61d-4ba7-b535-cc89f5fb73b9" />


---

#### Screenshot 2 — Content of `file-check.sh`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/98451be7-a2e0-4061-85e9-870548955b77" />


---

#### Screenshot 3 — Output of `./file-check.sh`

<img width="692" height="171" alt="image" src="https://github.com/user-attachments/assets/3a9eb0d6-ead8-4df3-82e1-038ce67f8bc6" />


---

### Notes

Answer the following in your own words:

**1. What does `-d` check in Bash?**

The -d option checks whether a specified path exists and is a directory. It returns true if the directory exists.

**2. What does `-f` check in Bash?**

The -f option checks whether a specified path exists and is a regular file. It returns true if the file exists and is a normal file.

**3. Why should file and directory paths be stored in variables?**

Storing file and directory paths in variables makes scripts easier to read, update, and maintain. If a path changes, it only needs to be changed in one place instead of throughout the entire script.


**4. What happens if the file does not exist?**

If the file does not exist, the -f condition returns false. The script can then use an else statement or another condition to display a message or handle the missing file appropriately.


# Task 7 — Conditionals: Pass or Retry Script

## Goal

Use if-else conditionals to make decisions based on a variable value.

### Evidence

#### Screenshot 1 — Content of `score-check.sh` with `score=85`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/15740820-205a-4bb0-902a-6fc038475733" />


---

#### Screenshot 2 — Output showing `Result: Pass`

<img width="753" height="222" alt="image" src="https://github.com/user-attachments/assets/cf21e44b-4c16-4450-b016-29381666c943" />


---

#### Screenshot 3 — Content of `score-check.sh` with `score=55`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/8c1cbbc8-ed6c-43d0-840c-8584c1b075c9" />


---

#### Screenshot 4 — Output showing `Result: Retry`

<img width="888" height="190" alt="image" src="https://github.com/user-attachments/assets/e8909145-e3d3-43a1-bdf2-740081e2b001" />


---

### Notes

Answer the following in your own words:

**1. What is the purpose of if-else in Bash?**

A function in Bash is a named group of commands that performs a specific task. It can be called whenever that task is needed in a script.


**2. What does `-ge` mean?**

Functions help organize a script into smaller, reusable sections. They reduce repeated code, make the script easier to understand, and make it simpler to maintain or modify.


**3. Why should conditions be tested with different values?**

In this script, I created functions to perform the specific tasks required by the program, such as displaying information and checking the required files or directories.


**4. How can conditionals help in automation scripts?**

The final script uses variables to store information, arrays to hold multiple related values, and loops to process those values repeatedly. It uses conditionals to make decisions based on whether files or directories exist. Functions organize the different tasks into reusable sections, while file operations allow the script to check and work with files. Together, these features make the script more organized, efficient, and easier to maintain.


# Task 8 — Functions: Final Bash Automation Script

## Goal

Create a final Bash script using functions to organize reusable code.

### Evidence

#### Screenshot 1 — Content of `final-automation.sh`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/525ff111-4b39-4706-a782-db74723dd52d" />


---

#### Screenshot 2 — Output of `./final-automation.sh`

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/fa6410d7-dd1d-4fe1-9d39-6669ff728410" />


---

#### Screenshot 3 — Output of `ls -lah` showing all created scripts

Add your screenshot here.

---

### Notes

Answer the following in your own words:

**1. What is a function in Bash?**

A function in Bash is a named block of commands that is created to perform a particular task. The function can be called whenever that task needs to be performed.


**2. Why are functions useful in scripts?**

Functions make scripts more organized and easier to manage. They allow us to reuse the same commands without writing them repeatedly and make it easier to find and fix problems.


**3. Which functions did you create in this script?**

I created functions for the main tasks in the script, such as checking files or directories and displaying the required information. These functions helped divide the script into smaller and reusable sections.


**4. How does this final script combine variables, arrays, loops, conditionals, files, and functions?**

The final script uses variables to store values, arrays to store multiple related items, and loops to process those items. Conditionals are used to make decisions, such as checking whether a file or directory exists. File operations allow the script to work with files, while functions organize these tasks into reusable blocks. Combining all these concepts makes the script more structured, efficient, and easier to maintain.


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
- All script files must be created and run successfully
- Required notes must be answered clearly for every task
- Do not expose sensitive information (keys, passwords, credentials)

---

# Completion Checklist

- [✅] Task 1: Environment setup verified, workspace created (Screenshots 1–2, Notes answered)
- [✅] Task 2: First script created, executed, permissions verified (Screenshots 1–3, Notes answered)
- [✅] Task 3: Variables script created and run (Screenshots 1–2, Notes answered)
- [✅] Task 4: Arrays and loops script created and run (Screenshots 1–2, Notes answered)
- [✅] Task 5: Counter loop script created and run (Screenshots 1–2, Notes answered)
- [✅] Task 6: File validation script created and run (Screenshots 1–3, Notes answered)
- [✅] Task 7: Pass/Retry conditional script tested with both values (Screenshots 1–4, Notes answered)
- [✅] Task 8: Final automation script created and run (Screenshots 1–3, Notes answered)
- [✅] All scripts run without errors
- [✅] Full Name visible in all required screenshots
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
