## 1. Overview

### 1.1 Introduction

This documentation describes the setup used to connect my GitHub repository with an AWS EC2 server through a self-hosted GitHub Actions runner. The purpose of this setup is to allow GitHub workflows to execute directly on the EC2 instance whenever code changes are pushed to the repository.

The self-hosted runner is installed and configured on an Ubuntu-based EC2 instance. The instance operates in a private configuration without assigning a public IP address, ensuring that the server remains isolated and secure while still being able to communicate with GitHub over outbound connections.

Whenever a commit is pushed to the GitHub repository, the configured GitHub Actions workflow is triggered automatically. The runner listens for incoming jobs from GitHub and executes them on the EC2 server. After successful execution, the latest repository files along with commit-related information are stored locally on the server at the following path:

/root/latest_commit

### 1.2 Key Points

- The GitHub repository and workflows are managed from my own GitHub account  
- A self-hosted GitHub Actions runner is configured on an AWS EC2 instance running Ubuntu  
- The EC2 instance is set up without a public IP address  
- No direct inbound access to the EC2 server is required  
- GitHub Actions workflows are triggered automatically on every push  
- The latest code and commit details are stored locally on the EC2 server
  
### Steps



<img width="1896" height="1030" alt="2" src="https://github.com/user-attachments/assets/5590b714-ef73-4512-9ec8-825fd4d50358" />

**Self-Hosted GitHub Actions Runner Registration on EC2**

- A self-hosted GitHub Actions runner was set up on an Ubuntu-based AWS EC2 instance.
- The official GitHub Actions runner package was downloaded and validated to ensure file integrity.
- The runner environment was extracted and prepared within a dedicated directory on the server.
- Root-level execution was enabled to allow the runner to perform all required workflow operations.
- The runner was authenticated using a repository-specific registration token from GitHub.
- Default settings were used during registration, including:
  - Runner group
  - Runner name
  - Runner labels
  - Working directory
- The runner was successfully registered with the GitHub repository.
- After registration, the EC2 instance became available to receive and execute GitHub Actions workflow jobs.
- This confirms that the EC2 server is now securely connected to GitHub Actions and actively listening for workflow triggers.






 
