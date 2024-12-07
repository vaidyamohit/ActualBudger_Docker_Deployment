# ActualBudger_Docker_Deployment

Docker | Actual Budget Documentation
actualbudget.org

Project Report: Deploying Actual Budget Using Docker on Windows

1. Introduction

This project focuses on deploying Actual Budget, an open-source, privacy-focused personal finance application, using Docker on a Windows platform. The deployment leverages Docker containers to ensure a consistent and efficient setup process.

2. About Actual Budget

Actual Budget is a local-first personal finance tool designed to offer users complete control over their financial data. It provides features such as budgeting, expense tracking, and synchronization across devices, all while ensuring data privacy by storing information locally.

3. Objectives

Deploy Actual Budget on a Windows system using Docker.
Ensure data persistence and accessibility through proper configuration.
Facilitate synchronization across multiple devices.
4. Prerequisites

Before proceeding with the deployment, ensure the following are installed on your Windows system:

Docker Desktop: Provides the Docker Engine and Docker Compose necessary for container management.
Windows Subsystem for Linux 2 (WSL2): Enhances Docker's performance on Windows.
5. Steps to Set Up Actual Budget Using Docker

Step 1: Install Docker Desktop

Download Docker Desktop from the official website.
Run the installer and follow the on-screen instructions.
Ensure Docker Desktop is configured to use WSL2 as the backend.
Step 2: Pull the Actual Budget Docker Image

Open Command Prompt or PowerShell.
Execute the following command to pull the latest Actual Budget image:
bash
Copy code
docker pull actualbudget/actual-server:latest
Step 3: Create a Directory for Data Persistence

Determine a suitable location on your system for storing Actual Budget data, e.g., C:\ActualBudgetData.
Create the directory using File Explorer or by running:
bash
Copy code
mkdir C:\ActualBudgetData
Step 4: Run the Actual Budget Container

In Command Prompt or PowerShell, execute:
bash
Copy code
docker run --pull=always --restart=unless-stopped -d -p 5006:5006 -v C:\ActualBudgetData:/data --name actual_budget actualbudget/actual-server:latest
--pull=always: Ensures the latest image is used.
--restart=unless-stopped: Automatically restarts the container unless explicitly stopped.
-d: Runs the container in detached mode.
-p 5006:5006: Maps port 5006 of the host to port 5006 of the container.
-v C:\ActualBudgetData:/data: Mounts the host directory to the container's /data directory for data persistence.
--name actual_budget: Names the container "actual_budget".
Step 5: Access Actual Budget

Open a web browser and navigate to http://localhost:5006.
Follow the on-screen instructions to complete the initial setup.
6. Conclusion

Deploying Actual Budget using Docker on a Windows system provides a streamlined approach to managing personal finances with enhanced data privacy. The use of Docker containers ensures consistency across different environments and simplifies the deployment process.

7. Future Enhancements

Automated Backups: Implement scheduled backups of the data directory to prevent data loss.
SSL Configuration: Set up SSL certificates to enable secure HTTPS access.
Mobile Access: Configure network settings to allow access from mobile devices within the local network.
