Overview

This project demonstrates the implementation of a secure CI pipeline between GitHub and an AWS EC2 server using a self-hosted GitHub Actions runner, without exposing the server to the public internet.Instead of relying on GitHub-hosted runners, the pipeline uses a self-hosted runner installed on an Ubuntu EC2 instance, allowing full control over the execution environment, system access, and file persistence. The EC2 instance operates in a private network configuration (no public IP) and communicates with GitHub exclusively through outbound HTTPS (port 443).Every time code is pushed to the GitHub repository, the workflow is automatically triggered. The self-hosted runner pulls the latest code, captures commit metadata, and synchronizes the repository contents into a predefined server path:

/root/latest_commit
