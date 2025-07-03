# Lab 2

## Title: Managing Agent Pools and Exploring Pipeline Approaches – 2h

# [2] Managing Agent Pools and Exploring Pipeline Approaches – Step-by-Step Instructions

**After logging in with your credentials:**

---

### **1. Create an Azure DevOps Organization**

1. Navigate to [https://dev.azure.com](https://dev.azure.com) and select **My Azure DevOps Organizations**.
2. Click **Create Organization** and proceed through any prompts or captchas.
3. Once created, you will be redirected to the organization dashboard.

---

### **2. Create and Configure a Team Project**

1. From the organization dashboard, click **New Project**.
2. Enter the project name as `eShopOnWeb` and leave other fields as default.
3. Click **Create Project**.

---

### **3. Import the eShopOnWeb Git Repository**

1. In the `eShopOnWeb` project, navigate to **Repos > Files**.
2. Click **Import**.
3. Paste the URL: `https://github.com/MicrosoftLearning/eShopOnWeb.git`.
4. Click **Import** to complete the repository import.

---

### **4. Confirm Default Branch**

1. Navigate to **Repos > Branches**.
2. Confirm `main` is listed and already set as the default branch.

---

### **5. Create and Connect to a Virtual Machine**

1. Go to **Virtual Machines** in the Azure portal and click **Create**.
2. Select **Azure virtual machine with preset configuration**.
3. Choose **Dev/Test** for workload environment and **General purpose** for workload type.
4. Click **Continue to create a VM**.
5. On the Basics tab, configure:
   - VM Name: `eshoponweb-vm`
   - Region: `East US`
   - Image: `Windows Server 2022 Datacenter`
   - Size: `Standard_DS1_v2`
   - Username: `whizlabs`
   - Password: your preferred password
   - Inbound port: `RDP 3389`
6. Under the **Management** tab, enable **System assigned managed identity**.
7. Click **Review + create**, then **Create**.
8. Once deployed, connect to the VM using **RDP** and log in.

---

### **6. Create an Agent Pool**

1. In the VM, open a browser and go to [https://aex.dev.azure.com](https://aex.dev.azure.com).
2. Open the `eShopOnWeb` project and go to **Project Settings**.
3. Under **Pipelines**, select **Agent Pools** and click **Add pool**.
4. Choose **Self-hosted**.
5. Name the pool `eShopOnWebSelfPool`.
6. Leave **Grant access permission to all pipelines** unchecked and click **Create**.

---

### **7. Download and Extract Agent Installation Files**

1. In Azure DevOps, go to **Agent Pools > eShopOnWebSelfPool > Agents**.
2. Click **New agent**, then download the agent package.
3. In PowerShell, create and navigate to a directory:
   ```powershell
   mkdir agent ; cd agent
   ```
4. Extract the downloaded zip:
   ```powershell
   Add-Type -AssemblyName System.IO.Compression.FileSystem ; `
   [System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win-x64-4.248.0.zip", "$PWD")
   ```

---

### **8. Create a Personal Access Token (PAT)**

1. In the browser, go to **User Settings > Personal Access Tokens**.
2. Click **New Token**.
3. Name it `eShopOnWebToken`, set the expiration, and select **Agent Pools (Read & Manage)** scope.
4. Click **Create** and securely copy the token.

---

### **9. Configure the Agent**

1. In PowerShell, run:
   ```powershell
   .\config.cmd
   ```
2. When prompted:
   - Enter your Azure DevOps org URL.
   - Use `PAT` for auth and enter your token.
   - Use `eShopOnWebSelfPool` for pool name.
   - Use `eShopOnWebSelfAgent` for agent name.
   - Accept default work folder.
   - Choose to run as a service and accept service config defaults.

---

### **10. Install Required Tools on the VM**

1. Install **Azure CLI** from [https://learn.microsoft.com/cli/azure/install-azure-cli-windows](https://learn.microsoft.com/cli/azure/install-azure-cli-windows).
2. Install **.NET 8 SDK** from [https://dotnet.microsoft.com/en-us/download](https://dotnet.microsoft.com/en-us/download).

---

### **11. Create an Azure DevOps YAML Pipeline**

1. In the Azure DevOps portal (outside the VM), go to **Pipelines**.
2. Click **Create Pipeline**.
3. Choose **Azure Repos Git**, then select `eShopOnWeb`.
4. Choose **Existing Azure Pipelines YAML file**.
5. Set:
   - Branch: `main`
   - Path: `/.ado/eshoponweb-ci-pr.yml`
6. Click **Continue**, then **Save**.

---

### **12. Update Pipeline to Use Self-Hosted Agent**

1. Go to **Pipelines > Edit**.
2. Replace the line:
   ```yaml
   vmImage: ubuntu-latest
   ```
   with:
   ```yaml
   pool:
     name: eShopOnWebSelfPool
     demands:
       - Agent.Name -equals eShopOnWebSelfAgent
   ```
3. Click **Validate and Save**, then **Save** again.
4. Click **Run** to execute the pipeline.
5. Monitor job progress to ensure it completes successfully.

---

**Delete all the resources.**

---
---
---
