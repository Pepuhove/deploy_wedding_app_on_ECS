#  Workflow succeed 
![Screenshot (122)](https://github.com/user-attachments/assets/f8ce0ba3-5852-4e44-bbde-6c56283ad3d0)
<br/>
<br/>





#  Wedding_app 

![Uploading Screenshot (121).png…]()




# 🚀 Deploy Static Website to AWS ECS with Nginx (CI/CD Pipeline)

This project automates the deployment of a static website using **Docker**, **Nginx**, and **AWS ECS (Elastic Container Service)**.

It features a fully integrated CI/CD pipeline using **GitHub Actions**, which includes code quality analysis, vulnerability scanning, 

and automatic deployment, followed by a Slack notification upon successful deployment.

---

# 📦 Features

- 🔍 **Code Analysis** with [SonarQube](https://www.sonarsource.com/products/sonarqube/)
- 🐳 **Docker Image Build & Push** to AWS ECR
- 🔐 **Vulnerability Scanning** with [Trivy](https://aquasecurity.github.io/trivy/)
- 🚢 **Deployment to AWS ECS**
- 📣 **Slack Notifications** on successful deployment
- 🌐 Hosted on **public ECS IP** (without load balancer)

---

# 🛠️ Tech Stack

- AWS ECS & ECR
- GitHub Actions
- Docker
- Nginx
- SonarQube
- Trivy
- Slack (via Webhook)

---

# 📁 Project Structure

```bash
.
├── Dockerfile

├── index.html

├── .github

│   └── workflows

│       └── main.yml    # GitHub Actions workflow

└── README.md

# 🚀 How It Works

Push to main branch triggers GitHub Actions.

Runs SonarQube for code quality analysis.

Builds a Docker image and pushes to Amazon ECR.

Scans the image for vulnerabilities using Trivy.

Deploys the image to AWS ECS.

Sends a Slack message with the live endpoint once deployed.

# 🔐 Secrets Required

To run this workflow, the following secrets must be configured in your GitHub repository:


# Secret Name	Description

SONAR_TOKEN	SonarQube authentication token
SONAR_HOST_URL	SonarQube server URL
AWS_ACCESS_KEY_ID	AWS access key for deploying to ECS
AWS_SECRET_ACCESS_KEY	AWS secret access key
AWS_REGION	AWS region (e.g., us-east-1)
AWS_ACCOUNT_ID	Your AWS account ID
REPOSITORY	ECR repository name
IMAGE_TAG	Docker image tag (e.g., latest)
REGISTRY	Full ECR registry URL
ECS_CLUSTER	ECS cluster name
ECS_SERVICE	ECS service name
SLACK_WEBHOOK	Slack webhook URL for notifications
ECS_ENDPOINT	Public IP of ECS task (if static)

# 🐳 Dockerfile Overview

Dockerfile
Copy
Edit
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
A minimal Dockerfile using Nginx to serve a static index.html file.

✅ Slack Notification
At the end of the pipeline, a Slack message is sent like this:

✅ Deployment Complete! Your app is live at: http://your-ecs-public-ip

# 📌 To-Do
 Add support for dynamic ECS public IP retrieval

 Add health checks or monitoring integration

 Add Terraform for IaC provisioning (optional)

# 📷 Screenshot

# 🤝 Contributions
Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.
