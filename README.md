Rolling the Dice on DevOps
Project Description
"Rolling the Dice on DevOps" is a comprehensive CI/CD workflow and full-stack implementation project aimed at deploying and managing a scalable board game web application. This project automates the entire lifecycle of application development, from code quality checks to containerization, security audits, and performance monitoring.

The application is deployed on AWS using Kubernetes, with advanced monitoring tools like Prometheus and Grafana, ensuring performance and reliability. Jenkins is utilized for continuous integration, while SonarQube and Nexus manage code quality and artifact storage.

Architecture Diagram
The architecture of the project showcases a seamless CI/CD pipeline with robust monitoring and security features, as illustrated below:
![image](https://github.com/user-attachments/assets/764ffa90-94d7-4b6c-b2b5-09acea7ab87b)

Features
User Management:
Users can add board games and reviews.
Managers can edit/delete reviews with additional privileges.
Automation:
Jenkins pipeline automates build, testing, deployment, and monitoring.
Security:
Kubeaudit ensures a secure Kubernetes cluster.
Scalability:
Kubernetes and Docker for containerized deployments.
Monitoring:
Real-time performance insights using Prometheus and Grafana.
Architecture Diagram

CI/CD Workflow
The workflow automates the development lifecycle:

Requirement Change: End-user raises a ticket.
Development: Developers commit code to GitHub.
Quality Assurance:
Unit Tests: Executed via Maven.
Code Quality: Verified with SonarQube.
Vulnerability Scanning: Performed using Trivy.
Artifact Management:
Artifacts built using Maven are pushed to Nexus.
Containerization:
Docker images are built, scanned, and pushed to the Docker registry.
Deployment:
Deployed on Kubernetes with security checks by Kubeaudit.
Monitoring:
Real-time performance tracked by Prometheus and Grafana.

Technology Stack
DevOps Tools:
Jenkins: CI/CD automation.
SonarQube: Code quality checks.
Nexus: Artifact storage.
Docker: Containerization.
Kubernetes: Orchestration and scaling.
Kubeaudit: Security audit.
Monitoring Tools:
Prometheus: Real-time metrics collection.
Grafana: Visualization and dashboards.
Black Box Exporter: Endpoint monitoring.
Application Stack:
Frontend: HTML, CSS, JavaScript
Backend: Node.js, Express
Database: MongoDB
Deployment Steps
1. AWS Setup
Create a VPC and configure Security Groups.
Launch 3 EC2 instances (1 Master, 2 Slaves).
2. Kubernetes Configuration
Install Kubernetes on all instances.
Deploy Calico Networking and NGINX Ingress Controller.
3. Jenkins and CI/CD Pipeline
Set up Jenkins on the master node.
Configure pipeline stages:
Build with Maven.
Run tests.
Quality check (SonarQube).
Push Docker images.
Deploy on Kubernetes.
4. Monitoring
Install Prometheus, Grafana, and Black Box Exporter.
Create Grafana dashboards for insights.
Monitoring Dashboard

Access the Application
Access the deployed application via the Kubernetes ingress endpoint:

arduino
Copy code
http://<LoadBalancer-IP>
Project Insights
Performance Metrics:

Jenkins build time and health monitored via Grafana.
Application latency tracked by Prometheus.
Security Audits:

Regular scans with Trivy and Kubeaudit.
Continuous Deployment:

Fully automated pipeline from development to production.
Future Scope
Add advanced analytics for user behavior.
Implement role-based access control (RBAC) for better security.
Introduce load testing with tools like JMeter.
Contributors
[Anurag Raut] 
