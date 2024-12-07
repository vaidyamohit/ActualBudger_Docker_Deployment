# Actual Budget Docker Deployment

For comprehensive instructions, refer to the [Docker | Actual Budget Documentation](https://actualbudget.org/docs/install/docker/).

## Project Report: Deploying Actual Budget Using Docker on Windows

### 1. Introduction

This project outlines the deployment of **Actual Budget**, an open-source, privacy-focused personal finance application, on a Windows platform using Docker. Utilizing Docker containers ensures a consistent and efficient setup process, enabling users to manage their finances securely and privately.

### 2. About Actual Budget

**Actual Budget** is a local-first personal finance tool that empowers users with complete control over their financial data. Key features include:

- **Budgeting:** Create and manage budgets to monitor spending and savings goals.
- **Expense Tracking:** Record and categorize expenses to understand spending habits.
- **Synchronization:** Sync data across multiple devices seamlessly.
- **Data Privacy:** Store data locally, ensuring privacy and security.

By focusing on local data storage, Actual Budget minimizes reliance on third-party services, enhancing user privacy.

### 3. Objectives

- Deploy Actual Budget on a Windows system using Docker.
- Ensure data persistence and accessibility through proper configuration.
- Facilitate synchronization across multiple devices.

### 4. Prerequisites

Before proceeding with the deployment, ensure the following are installed on your Windows system:

- **Docker Desktop:** Provides the Docker Engine and Docker Compose necessary for container management. [Download Docker Desktop](https://www.docker.com/products/docker-desktop/)
- **Windows Subsystem for Linux 2 (WSL2):** Enhances Docker's performance on Windows.

**Installing WSL2:**

1. **Enable the WSL Feature:**
   - Open PowerShell as Administrator.
   - Run:
     ```powershell
     dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
     ```

2. **Enable the Virtual Machine Platform Feature:**
   - In the same PowerShell window, run:
     ```powershell
     dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
     ```

3. **Update the WSL Kernel:**
   - Download the latest WSL2 kernel update from the [Microsoft WSL2 Kernel Update](https://aka.ms/wsl2kernel).
   - Run the installer.

4. **Set WSL2 as the Default Version:**
   - In PowerShell, run:
     ```powershell
     wsl --set-default-version 2
     ```

5. **Install a Linux Distribution:**
   - Open the Microsoft Store.
   - Search for and install your preferred Linux distribution (e.g., Ubuntu).
   - Launch the distribution and complete the initial setup.

For detailed instructions, refer to the [Microsoft WSL Installation Guide](https://learn.microsoft.com/en-us/windows/wsl/install).

### 5. Steps to Set Up Actual Budget Using Docker

**Step 1: Install Docker Desktop**

- Download Docker Desktop from the [official website](https://www.docker.com/products/docker-desktop/).
- Run the installer and follow the on-screen instructions.
- Ensure Docker Desktop is configured to use WSL2 as the backend.

**Step 2: Pull the Actual Budget Docker Image**

- Open Command Prompt or PowerShell.
- Execute the following command to pull the latest Actual Budget image:
  ```bash
  docker pull actualbudget/actual-server:latest

**Step 3: Create a Directory for Data Persistence**

 -Determine a suitable location on your system for storing Actual Budget data, e.g., C:\ActualBudgetData.
 -Create the directory using File Explorer or by running:

mkdir C:\ActualBudgetData

**Step 4: Run the Actual Budget Container**

In Command Prompt or PowerShell, execute the following command:

```bash
docker run --pull=always --restart=unless-stopped -d -p 5006:5006 -v C:\ActualBudgetData:/data --name actual_budget actualbudget/actual-server:latest
```


**Step 5: Access Actual Budget**

 -Open a web browser and navigate to ```http://localhost:5006.```
 -Follow the on-screen instructions to complete the initial setup.

### Video



### 6. Conclusion
Deploying Actual Budget using Docker on a Windows system provides a streamlined approach to managing personal finances with enhanced data privacy. The use of Docker containers ensures consistency across different environments and simplifies the deployment process.

### 7. Future Enhancements
 -Automated Backups: Implement scheduled backups of the data directory to prevent data loss.
 -SSL Configuration: Set up SSL certificates to enable secure HTTPS access.
 -Mobile Access: Configure network settings to allow access from mobile devices within the local network.
