## Introduction

This documentation describes the setup used to connect my GitHub repository with an AWS EC2 server through a self-hosted GitHub Actions runner. The purpose of this setup is to allow GitHub workflows to execute directly on the EC2 instance whenever code changes are pushed to the repository.

The self-hosted runner is installed and configured on an Ubuntu-based EC2 instance. The instance operates in a private configuration without assigning a public IP address, ensuring that the server remains isolated and secure while still being able to communicate with GitHub over outbound connections.

Whenever a commit is pushed to the GitHub repository, the configured GitHub Actions workflow is triggered automatically. The runner listens for incoming jobs from GitHub and executes them on the EC2 server. After successful execution, the latest repository files along with commit-related information are stored locally on the server at the following path:

/root/latest_commit

### Key Points

- The GitHub repository and workflows are managed from my own GitHub account  
- A self-hosted GitHub Actions runner is configured on an AWS EC2 instance running Ubuntu  
- The EC2 instance is set up without a public IP address  
- No direct inbound access to the EC2 server is required  
- GitHub Actions workflows are triggered automatically on every push  
- The latest code and commit details are stored locally on the EC2 server
  
## Architecture

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/13fae0b6-7394-4360-8a21-7029f2bfb7be" />

## Step-by-Step Implementation (As Shown in Screenshots)

### Step 1: GitHub Repository Setup
- A GitHub repository is created and managed from my GitHub account.
- A GitHub Actions workflow file is added under `.github/workflows`.
- The workflow is configured to trigger automatically on every push to the `main` branch.
  
  <img width="1910" height="923" alt="6" src="https://github.com/user-attachments/assets/efd8c42b-9fbc-4953-888f-c9236ed4f00d" />

### Step 2: EC2 Instance Preparation and Self-Hosted Runner Installation
- An Ubuntu-based EC2 instance is launched inside a private subnet.
- No public IP address is assigned to the EC2 instance.
- Outbound internet access is provided using a NAT Gateway.
- The GitHub Actions self-hosted runner is installed on the Ubuntu EC2 instance.
- The runner is registered with the GitHub repository.
- Default runner group and labels are used during registration.
  <img width="1896" height="1030" alt="2" src="https://github.com/user-attachments/assets/e48a58a7-7afb-4663-ba06-0a0373a56fd1" />

### Step 3: Running the Self-Hosted Runner in Background

- A new `screen` session named `runner` is created before starting the GitHub Actions runner.
- This ensures the runner continues running even if the SSH session is closed.
- The GitHub Actions runner is started inside the `screen` session.
- The runner connects successfully to GitHub and starts listening for jobs.
- The `Ctrl + A` followed by `D` key combination is used to detach from the screen session.
- Detaching allows the runner to keep running in the background without interruption.
  <img width="794" height="232" alt="10" src="https://github.com/user-attachments/assets/837392cd-ba2a-402d-864f-3b50dbf3a7b6" />


### Step 4: Workflow Execution from GitHub
- A code change is pushed to the GitHub repository.
- GitHub Actions automatically triggers the workflow.
- The job is picked up by the self-hosted runner on EC2.
 <img width="1916" height="885" alt="4" src="https://github.com/user-attachments/assets/5618be3e-31a3-4730-90f6-7049de6412a4" />
 <img width="1895" height="565" alt="3" src="https://github.com/user-attachments/assets/26617a60-301c-4b41-8193-5368fb640079" />
 <img width="1918" height="900" alt="8" src="https://github.com/user-attachments/assets/af2450d4-5097-4272-a5d9-044d65a3f4f2" />


### Step 5: Successful Job Completion
- The workflow executes all defined steps successfully.
- Repository files are checked out on the EC2 instance.
- Commit details and file information are generated.
 <img width="893" height="652" alt="9" src="https://github.com/user-attachments/assets/3c28346d-c894-47a5-98b6-6b9978eed0cb" />
 <img width="1912" height="713" alt="7" src="https://github.com/user-attachments/assets/14c1b1da-ff51-459d-ac64-f1e97f71fe0f" />




## Outcome

- GitHub Actions is successfully integrated with an EC2-based self-hosted runner.
- The EC2 instance operates securely without a public IP.
- Every push to GitHub triggers automated execution on the EC2 server.
- The setup is stable and ready for future automation tasks.













 
