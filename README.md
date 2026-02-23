# Cloud-Deployment-Pipeline-Vagrant-to-AWS-via-Docker
I have successfully built, containerized, and deployed a web application, moving from a local virtualized environment to a live cloud infrastructure on AWS.


🎯 Project Objective : The goal was to create a reproducible workflow that ensures an application runs identically on a developer's local machine and a production cloud server.

🛠 Tech Stack
Infrastructure: AWS (EC2, VPC, Security Groups)
Local Virtualization: Vagrant, VirtualBox
Containerization: Docker, Docker Hub
Web Server: Nginx
OS: Ubuntu 22.04 LTS (Jammy Jellyfish)

🏗 Phase 1: Local Development (Vagrant)
I started by isolating my development environment to ensure "it works on my machine" translates to "it works everywhere."

Environment: Provisioned an Ubuntu VM using a Vagrantfile.
Web Setup: Installed Nginx and hosted a custom index.html.
Validation: Verified local access via the VM's private IP address.

📦 Phase 2: Containerization (Docker)
To make the app portable, I moved away from manual installs to containerization.

Dockerfile: Created a custom image using nginx:alpine for a tiny footprint.
Build & Tag: ```bash
docker build -t mahmmadakhil/my-app:v1 .
Registry: Pushed the image to Docker Hub.

☁️ Phase 3: Cloud Deployment (AWS)
Finally, I deployed the container to a live production environment.
<img width="1185" height="681" alt="http" src="https://github.com/user-attachments/assets/93e2cac7-be46-4e9a-bb36-66405f8558e7" />

EC2 Provisioning: Launched a t2.micro instance using the Default VPC.
Networking: Configured Security Groups to allow inbound traffic on Port 80 (HTTP) and Port 22 (SSH).
Deployment:
Connected via SSH.
Installed Docker Engine.
Pulled the image from Docker Hub.

Live Command:
Bash
docker run -d --name web-server -p 80:80 mahmmadakhil/my-app:v1
