# Lab 1

## Title: Version Control and Collaboration Using Git in Azure Repos – 2h

---
---
---

**After logging in with your credentials:**

---

### **Task 1: Create an Azure DevOps Organization**

1. Open a web browser and go to [https://dev.azure.com/](https://dev.azure.com/).
2. Select **Create new organization** and proceed if any confirmation prompts appear.
3. Enter a globally unique organization name and choose a preferred region.
4. Complete the setup process and proceed to the organization dashboard.

---

### **Task 2: Configure Git and Visual Studio Code**

1. Launch Visual Studio Code.

2. From the menu, select **Terminal > New Terminal**.

3. Ensure the terminal is using **PowerShell**.

4. Run the following command to configure the Git credential helper:

   ```bash
   git config --global credential.helper wincred
   ```

5. Configure your Git username and email:

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email you@example.com
   ```

---

### **Task 3: Create a Team Project**

1. In your Azure DevOps organization, click **New Project**.
2. Enter `eShopOnWeb` as the project name.
3. Select **Scrum** as the Work Item process.
4. Click **Create**.

---

### **Task 4: Import the eShopOnWeb Repository**

1. In Azure DevOps, open the **eShopOnWeb** project.

2. Navigate to **Repos > Files**, then click **Import**.

3. Enter the following repository URL:

   ```
   https://github.com/MicrosoftLearning/eShopOnWeb.git
   ```

4. Click **Import**.

---

### **Task 5: Configure Default Branch**

1. Navigate to **Repos > Branches**.
2. Confirm that the **main** branch is listed.
3. If it is the only branch, it is already the default branch.

---

### **Task 6: Clone the Repository Locally**

1. In Azure DevOps, go to **Repos > Files**.
2. Click **Clone**, select **HTTPS**, and copy the URL.
3. Generate and copy the credentials if prompted.
4. Open Visual Studio Code.
5. Use **Ctrl+Shift+P** or **F1** to open the Command Palette.
6. Run `Git: Clone`.
7. Paste the copied repository URL.
8. Choose or create a folder (e.g., `C:\Git`) as the destination.
9. Enter the credentials when prompted.
10. Click **Open** to open the cloned repository in VS Code.

---

### **Task 7: Make and Commit Changes**

1. In VS Code, open `/eShopOnWeb/src/Web/Program.cs`.
2. Add the comment `// My first change` at the top and save.
3. Open the **Source Control** tab.
4. Enter `My commit` as the commit message.
5. Use **Ctrl+Enter** to commit the change.
6. Click the **Synchronize Changes** icon to push the commit.

---

### **Task 8: Stage Specific Changes**

1. Modify `Program.cs` to `// My second change` and save.
2. Open `/eShopOnWeb/src/Web/Constants.cs`, add `// My third change`, and save.
3. In the **Source Control** tab, stage only `Program.cs`.
4. Enter `Added comments` as the commit message.
5. Use the **Commit Staged** option from the ellipsis menu.
6. Click **Synchronize Changes** to push the changes.

---

### **Task 9: Review Commits in Azure DevOps**

1. In Azure DevOps, go to **Repos > Commits**.
2. Confirm your commits are visible in the list.
3. Use **Browse Files** to view committed files.

---

### **Task 10: Create a New Branch**

1. In VS Code, click the current branch label in the lower-left corner.
2. Select **+ Create new branch from…**.
3. Choose **main** as the reference.
4. Name the new branch `dev` and press Enter.

---

### **Task 11: Delete a Branch**

1. In VS Code, publish the `dev` branch.
2. In Azure DevOps, go to **Repos > Branches > Mine**.
3. Hover over the `dev` branch and delete it using the ellipsis menu.
4. In VS Code, view the branch list and confirm the branch status.
5. In Azure DevOps, use the **All** tab and search for `dev`.
6. Locate the deleted branch and restore it.

---

### **Task 12: Set Branch Policies**

1. In Azure DevOps, go to **Repos > Branches**.
2. Hover over the **main** branch and select **Branch Policies**.
3. Enable **Require minimum number of reviewers** and set it to 1.
4. Enable **Check for linked work items**.

---

### **Task 13: Test Branch Policies**

1. In **Repos > Files**, ensure **main** is selected.
2. Open `/src/Web/Program.cs` and attempt to commit a change.
3. Observe the warning that changes must be made via Pull Request.
4. Cancel the commit.

---

### **Task 14: Create and Link a Pull Request**

1. In Azure DevOps, go to **Boards > Work Items**.
2. Create a new item titled `Testing my first PR`.
3. In **Repos > Files**, switch to the **dev** branch.
4. Edit `/src/Web/Program.cs` to add `// Testing my first PR`.
5. Commit the changes.
6. Click **Create a Pull Request** when prompted.
7. In the pull request, link the newly created work item.
8. Review the changes under the **Files** tab.

---

### **Task 15: Apply a Git Tag**

1. Go to **Repos > Tags**.
2. Click **New tag**.
3. Name the tag `v1.1.0-beta`, base it on `main`, and add a description.
4. Click **Create**.

---

### **Task 16: Remove Branch Policies**

1. In **Repos > Branches**, hover over **main** and open **Branch Policies**.
2. Disable:

   * **Require minimum number of reviewers**
   * **Check for linked work items**

---

**Delete all the resources.**

---
---
---

## **Lab Summary: Version Control and Collaboration Using Git in Azure Repos**

---

### 🧭 **Purpose of the Lab**

This lab is designed to provide hands-on experience with **version control**, **collaborative development**, and **branch management** using **Azure DevOps** and **Git**. Learners will explore how to:

* Create and manage a Git repository in Azure Repos
* Use Visual Studio Code and Git commands for committing and pushing code
* Create branches and manage pull requests
* Enforce collaboration and quality through branch policies
* Link work items to code changes for traceability
* Tag versions for release management

The ultimate goal is to simulate a real-world DevOps workflow where team members collaborate on source code in a controlled and trackable manner using Azure services and Git-based tooling.

---

## 🛠️ **Azure Tools Used in the Lab**

Each tool below plays a specific role in enabling DevOps practices and collaborative source control.

---

### 1. **Azure DevOps**

**Description:**
A cloud-based DevOps platform by Microsoft that provides services for source control, CI/CD, agile planning, testing, and more.

**Role in Lab:**
Used to create and manage the DevOps organization, host the Git repository (`eShopOnWeb`), manage branches, create work items, configure branch policies, and perform pull requests.

---

### 2. **Azure Repos**

**Description:**
A Git-based version control service within Azure DevOps that allows for collaborative code development and source management.

**Role in Lab:**
Used to host and manage the `eShopOnWeb` project’s source code. Enables importing repositories, cloning them, committing changes, managing branches, and reviewing code via pull requests.

---

### 3. **Azure Boards**

**Description:**
An agile project management service within Azure DevOps for planning, tracking, and discussing work items across teams.

**Role in Lab:**
Used to create and link work items (e.g., Product Backlog Items) to commits and pull requests, enabling traceability between code changes and project tasks.

---

### 4. **Branch Policies**

**Description:**
Configuration settings in Azure Repos that enforce code quality rules before changes can be merged into protected branches.

**Role in Lab:**
Applied to the `main` branch to require approvals and linked work items before merging pull requests. This ensures collaborative code review and process discipline.

---

### 5. **Pull Requests**

**Description:**
A mechanism to propose, review, and merge code changes in Git repositories.

**Role in Lab:**
Used to simulate collaborative development by requiring developers to submit changes from feature branches (`dev`) to the protected `main` branch via a structured review process.

---

### 6. **Git**

**Description:**
A distributed version control system used to track changes in source code during software development.

**Role in Lab:**
Configured within Visual Studio Code to manage code changes, commits, branches, and to push/pull code to/from Azure Repos.

---

### 7. **Tags in Azure Repos**

**Description:**
Labels used to mark specific points in a Git repository’s history, typically for versioning releases.

**Role in Lab:**
A tag (`v1.1.0-beta`) was created to represent a beta release of the codebase, helping with version control and deployment reference.

---

### 8. **Visual Studio Code (VS Code)**

**Description:**
A lightweight and powerful source code editor with Git integration and support for development tools.

**Role in Lab:**
Used to edit source files, commit changes, stage files, manage branches, and sync code with Azure Repos via Git.

---

### 9. **Git Credential Helper**

**Description:**
A helper tool to securely store and reuse Git credentials.

**Role in Lab:**
Configured in VS Code using `git config` to avoid repeated login prompts while working with Azure Repos.

---

### 10. **Work Items**

**Description:**
Individual units of work in Azure Boards (e.g., tasks, bugs, features).

**Role in Lab:**
Created and linked to pull requests to ensure development tasks are tracked and traceable to code changes.

---

## ✅ Summary Outcome

By completing this lab, learners become proficient in:

* Setting up Azure DevOps environments for Git-based collaboration
* Managing source code and branches efficiently
* Enforcing team practices with policies
* Tracing code changes to project tasks
* Navigating real-world Git workflows for modern DevOps

This lab effectively demonstrates the **integration of project tracking, source control, and quality assurance** using Azure DevOps and Git.

---
---
---
Here's a practical and professional **real-world scenario** that demonstrates the purpose and tasks of the lab in an engaging and easy-to-follow narrative style. This makes it easier to understand **why** each step is important and how it connects to a **real business goal**.

---

## 📘 **Scenario: Improving Team Collaboration and Code Quality in a Growing Startup**

**Meet Elena**, a software engineer at a fast-growing e-commerce startup called **QuickKart**. The company has recently expanded its engineering team, and code management has become chaotic. Developers are working on different versions of code, bugs are creeping into production, and no one knows who changed what or why.

Elena's CTO tasks her with **setting up a professional version control system** that supports:

* **Team collaboration**
* **Code traceability**
* **Branching and merging best practices**
* **Policy-based code reviews**

Elena decides to use **Azure DevOps** and **Git** to bring structure and discipline to the development workflow.

---

## 🔧 **Step-by-Step Journey: How Elena Solves the Problem**

### 🔹 **Step 1: Create an Azure DevOps Organization**

Elena creates an **Azure DevOps organization** for QuickKart so the team can centralize their project workflows. This acts as their **collaboration hub** — developers, testers, and project managers can now work in a shared space.

### 🔹 **Step 2: Configure Git & VS Code**

She sets up **Git** on her machine and configures **Visual Studio Code** for development. By setting her **Git credentials**, she ensures every commit is properly tagged with the author's identity — critical for **audit trails** and **accountability**.

### 🔹 **Step 3: Create a Team Project**

Elena creates a new project called **eShopOnWeb** and selects the **Scrum process** so that future work items can be tracked in sprints. This aligns the development team with **agile methodologies**.

### 🔹 **Step 4: Import the Codebase**

She imports a sample .NET app from GitHub to give her team a jumpstart. This allows her to demonstrate how to work with **existing codebases** and adopt Azure DevOps seamlessly into their current workflow.

### 🔹 **Step 5: Clone and Modify the Repo**

Elena clones the repo into her local system using **Visual Studio Code**. She edits a file, adds a comment, and commits it with a clear message. By doing this, she shows how **developers can work independently** and still maintain **version control**.

### 🔹 **Step 6: Push Changes & Sync**

She uses the **Synchronize Changes** feature to push her updates to the central repository. This allows others on her team to **pull the latest code** and avoid conflicts — reducing errors in production.

### 🔹 **Step 7: Branching for Safety**

Elena creates a **dev branch** to isolate her feature work. This ensures that the **main branch remains stable** while she experiments. She later deletes and restores branches to demonstrate flexibility in managing **short-lived feature branches**.

### 🔹 **Step 8: Enforce Branch Policies**

To improve quality, Elena applies **branch policies**: requiring at least one reviewer and linking commits to work items. This ensures that **every change is reviewed and traceable to a business need** — no more mystery bugs!

### 🔹 **Step 9: Pull Request and Code Review**

She edits the code in the **dev** branch and opens a **Pull Request (PR)** to merge it into **main**. Azure DevOps reminds her that a **work item must be linked**, reinforcing good habits like **documentation and traceability**.

She links the work item, completes a self-review, and merges the PR. Now every change is:

* Reviewed
* Tracked
* Documented

### 🔹 **Step 10: Use Tags for Versioning**

Elena tags the current codebase as **v1.1.0-beta**, preparing it for a **beta release**. This helps the QA team and business users **test specific versions** without confusion about which code is deployed.

---

## 🎯 **Outcome: A Professional, Scalable DevOps Workflow**

By the end of her setup:

* QuickKart’s developers work confidently using **branches and commits**
* Reviewers know exactly **what code was changed and why**
* Business stakeholders can track **feature progress** via linked work items
* The codebase is **stable, traceable, and secure**

The tools Elena used—**Azure DevOps, Azure Repos, Git, VS Code, Pull Requests, Tags, Branch Policies**—aren’t just for labs; they are real-world tools used by high-performing teams to ship quality software, fast.

---

**This lab simulates Elena’s journey.**
And now, **you** can apply the same principles to your projects — whether you're managing a small app or a full-scale enterprise product.

---
---
---
## Lab-Based Conceptual MCQs

### 1. What is the primary benefit of using branches in a Git-based workflow within Azure Repos?

(a) It prevents unauthorized users from accessing the repository  
(b) It allows developers to isolate changes without affecting the main codebase  
(c) It automatically creates backups of all files  
(d) It enables editing code directly on the production environment  

**Correct answer: (b)**  
**Explanation:** Branches are used to isolate feature development or bug fixes, allowing developers to work independently without impacting the main branch stability.

---

### 2. Why are branch policies important in a collaborative development environment?

(a) They enable automatic deployment of branches  
(b) They reduce the need for code reviews  
(c) They enforce quality gates such as peer reviews and work item linking  
(d) They allow unreviewed code to bypass the main branch  

**Correct answer: (c)**  
**Explanation:** Branch policies enforce quality control by requiring actions like code reviews and linking work items before merging into a protected branch.

---

### 3. What is the role of pull requests in Azure Repos?

(a) They automatically build and deploy the project  
(b) They allow developers to bypass branch policies  
(c) They facilitate code review and controlled merging of changes  
(d) They track bugs in the repository  

**Correct answer: (c)**  
**Explanation:** Pull requests provide a mechanism for reviewing and approving changes before they are merged, ensuring collaboration and code quality.

---

### 4. Why is linking work items to commits considered a best practice in DevOps?

(a) It increases the repository size  
(b) It prevents others from editing the code  
(c) It provides traceability between code changes and business requirements  
(d) It disables commit history  

**Correct answer: (c)**  
**Explanation:** Linking work items creates traceability, helping teams understand the context of changes and ensuring alignment with project goals.

---

### 5. What is the purpose of using Git tags like `v1.1.0-beta` in a repository?

(a) To increase commit frequency  
(b) To revert the repository to the first version  
(c) To mark specific points in history for releases or milestones  
(d) To delete older versions of code  

**Correct answer: (c)**  
**Explanation:** Tags are used to label important commits, such as release versions, enabling easy identification and deployment tracking.

---

### 6. How does using Visual Studio Code with Git integration benefit developers?

(a) It eliminates the need for version control  
(b) It prevents branching  
(c) It simplifies source control operations through a user-friendly interface  
(d) It automatically commits changes to production  

**Correct answer: (c)**  
**Explanation:** VS Code offers integrated Git support, making tasks like committing, branching, and syncing accessible through an intuitive UI.

---

### 7. What is a practical outcome of enforcing “minimum number of reviewers” in branch policies?

(a) It delays feature delivery unnecessarily  
(b) It ensures that changes are reviewed for quality before merging  
(c) It allows only team leads to commit code  
(d) It locks the main branch permanently  

**Correct answer: (b)**  
**Explanation:** Requiring reviewers helps catch errors early, encourages knowledge sharing, and improves overall code quality before integration.

---

### 8. What does the `git config --global credential.helper wincred` command do?

(a) It deletes all previous credentials  
(b) It sets up Git to use a Windows credential store for authentication  
(c) It installs Git on the system  
(d) It removes repository access  

**Correct answer: (b)**  
**Explanation:** This command configures Git to use Windows Credential Manager to store and retrieve credentials securely.

---

### 9. In a DevOps workflow, why should changes be committed with meaningful messages?

(a) To reduce repository size  
(b) To allow commit messages to auto-generate build numbers  
(c) To provide context and improve collaboration and auditing  
(d) To prevent Git from asking for a password  

**Correct answer: (c)**  
**Explanation:** Meaningful commit messages help team members understand the purpose of a change, making collaboration and troubleshooting more effective.

---

### 10. What is the benefit of using work items in Azure Boards alongside Azure Repos?

(a) They serve as placeholders for backup data  
(b) They enable real-time code compilation  
(c) They allow developers to track progress and connect changes to tasks or bugs  
(d) They override branch policies  

**Correct answer: (c)**  
**Explanation:** Work items help manage tasks, bugs, and features, and when linked to code changes, they offer end-to-end traceability from planning to delivery.

---

