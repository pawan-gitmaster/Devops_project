# Devops_project

🔥 **Project Title**

“Production-Ready CI/CD Pipeline for Microservices on AWS using Jenkins, Terraform, Docker, Kubernetes, and Ansible”

🎯 **Objective**

To design and implement a fully automated, secure, and scalable CI/CD pipeline for deploying a microservices-based web application on AWS, using modern DevOps tools and practices.

🧰 **Tools & Technologies Used**

Category Tools/Technologies
Source Code Management Git, GitHub (with Webhook Integration)
CI/CD Orchestration Jenkins (Multibranch Pipeline + Shared Libraries)
Infrastructure as Code Terraform (with Remote Backend – S3 + DynamoDB)
Configuration Management Ansible + Ansible Vault
Containerization Docker, DockerHub / AWS ECR
Container Orchestration Kubernetes (AWS EKS)
Secrets Management Ansible Vault or HashiCorp Vault
Monitoring & Logging Prometheus, Grafana, ELK Stack (Elasticsearch, Kibana)
Notification/Alerting Slack, Email, or MS Teams via Jenkins plugins
Deployment Strategy Rolling Updates


🔧 **Detailed Project Workflow (Point-Wise)**

1. ✅ **GitHub Repository & Branching Strategy**
 • Set up a GitHub repository with branches: main, dev, and feature/*.
 • Created separate directories for frontend, backend, and other microservices.
 • Enabled GitHub Webhooks to notify Jenkins on each push or PR.
 • Configured Multibranch Pipeline in Jenkins to auto-discover and build each branch.

2. 🏗️ **Infrastructure Provisioning with Terraform**
 • Defined reusable Terraform modules for:
     • VPC (with public/private subnets)
     • Internet Gateway & NAT Gateway
     • EC2 (for Jenkins and Ansible control node)
     • RDS (PostgreSQL or MySQL DB)
     • S3 Bucket (for Terraform backend)
     • DynamoDB (for state locking)
     • EKS (Elastic Kubernetes Service)
     • Used terraform plan and terraform apply to deploy infrastructure in AWS.
     • Managed remote state using S3 and DynamoDB for collaboration and locking.

3. 🔐 **Configuration Management with Ansible**
 • Wrote Ansible playbooks to:
     • Install Docker, Kubernetes tools (kubectl, kubeadm, etc.)
     • Install Jenkins on EC2 (with plugins and initial setup)
     • Configure Jenkins security, global tools, and credentials
     • Set up monitoring stack (Prometheus + Grafana)
     • Used Ansible Vault to encrypt sensitive data like DB credentials, AWS keys.

4. 🐳 **Dockerization of Microservices**
 • Created separate Dockerfiles for:
     • Frontend ( Angular )
     • Backend APIs ( Spring Boot )
     • Auth & Payment microservices
     • Used docker-compose for local testing.
     • Built and pushed images to DockerHub or AWS ECR using CI pipeline.

5. ☸️ **Kubernetes Deployment ( EKS )**
 • Wrote YAML manifests for:
     • Deployments, Services, Ingress, ConfigMaps, and Secrets
     • Configured Ingress Controller and external load balancer.
     • Used kubectl and Helm charts for deploying microservices.
     • Enabled horizontal pod autoscaling and rolling updates.

6. 🛠️ **CI/CD with Jenkins (Pipeline-as-Code)**
 • Wrote a Jenkinsfile with the following stages:
     1. Checkout code from GitHub
     2. Build Docker image
     3. Run unit tests
     4. Push image to DockerHub/ECR
     5. Deploy to Kubernetes using kubectl
     6. Post-build actions (notifications, cleanup)
     • Enabled:
     • Multibranch Pipeline for feature/PR builds
     • Shared libraries for DRY code (e.g., pipeline-library@dev)
     • Parameterized jobs (e.g., select environment: dev, stage, prod)

7. 📈 **Monitoring & Logging Setup**
 • Installed and configured:
 • Prometheus for real-time metrics
 • Grafana for dashboards (e.g., CPU, memory, HTTP errors)
 • ELK Stack (Elasticsearch, Logstash, Kibana) for application logs
 • Configured alert rules and notifications to Slack or Email.

8. 🔐 **Security Best Practices**
 • Managed secrets using Ansible Vault and environment variables.
 • Configured IAM roles and policies for least privilege on AWS.
 • Enabled audit logging and role-based access control (RBAC) in Kubernetes.
 • Enforced access restrictions via NACLs and Security Groups in AWS.
