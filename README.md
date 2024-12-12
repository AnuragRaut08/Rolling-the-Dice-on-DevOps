# **Rolling the Dice on DevOps**

This project revolves around automating the continuous integration/continuous deployment (CI/CD) process using various DevOps tools. The process includes the integration of Docker, Kubernetes, Prometheus, Jenkins, Maven, SonarQube, Nexus, Trivy, Grafana, and KubeAudit.

## **Project Description**
The project focuses on streamlining the deployment process for the Board Game Database Full-Stack Web Application. This web application allows users to view, add, and edit board games and reviews. The application follows a role-based access system where users can add and review games, and managers can edit or delete reviews.

**Deployment Details**
- Deployed on AWS using Kubernetes for orchestration.
- Security managed by Kubeaudit.
- Code quality checked using SonarQube.
- Artifact management handled by Nexus.
- Continuous integration and deployment powered by Jenkins.
- Application monitoring using Prometheus and Grafana.


## **Board Game CI/CD Workflow**
![image](https://github.com/user-attachments/assets/ecdcd84c-41d9-401a-a11e-beeea12daaa9)


## **Implementation Steps**

### 1. **Configure Private Environment in AWS**

- Set up a Virtual Private Cloud (VPC).
- Configure security groups for VM instance traffic control.

### 2. **Configure VMs**

- Launch three VM instances.
- Install Kubernetes and configure master and slave nodes.

### 3. **Kubernetes Cluster Setup**

- Initialize the cluster on the master node using `kubeadm init`.
- Join the slave nodes with `kubeadm join`.

### 4. **Networking and Ingress Setup**

- Deploy Calico for networking.
- Install NGINX as the Ingress Controller.

### 5. **Security Setup**

- Install Kubeaudit to monitor cluster security and run checks.

### 6. **SonarQube and Nexus Configuration**

- Set up SonarQube and Nexus servers.
- Run SonarQube container on port 9000.
- Run Nexus container on port 8081.

### 7. **Jenkins Server Setup**

- Install Jenkins on the server.
- Configure Jenkins to run on port 8080.
- Set up a Jenkins pipeline for building, testing, and deploying the application.

### 8. **Application Monitoring with Prometheus and Grafana**

- Install Prometheus on port 9090 and Grafana on port 3000.
- Configure Grafana to visualize metrics collected by Prometheus.
- Install Black Box Exporter on port 9115 to monitor app availability.
- Set up a Grafana dashboard to monitor Jenkins performance.

**Prerequisites**
Before you start, ensure you have the following tools installed:

Docker
Kubernetes
Jenkins
Maven
SonarQube
Nexus Repository
Prometheus
Grafana
Trivy
KubeAudit
Installation
To get the project up and running locally, follow these steps:

1. Clone the repository
bash
Copy code
git clone https://github.com/AnuragRaut08/Rolling-the-Dice-on-DevOps.git
2. Docker & Kubernetes Setup
Ensure Docker and Kubernetes are installed on your machine. Follow the official installation guides:

Docker installation
Kubernetes installation
3. Start Jenkins, SonarQube, Nexus, Prometheus, and Grafana
Use Docker to run the necessary containers for Jenkins, SonarQube, Nexus, Prometheus, and Grafana.

bash
Copy code
docker-compose up
(Make sure you have a docker-compose.yml for managing the containers.)

4. Kubernetes Cluster Setup
If you're running Kubernetes locally, ensure that kubectl is installed and your cluster is running. Then, apply the necessary Kubernetes manifests to deploy your app.

5. Run the Application
After all setups, you can run the application and visit it in your browser.

**Contributors**
Anurag - Lead Developer -https://linkedin.com/in/anurag-raut-338b8b2b8

**License**
This project is licensed under the MIT License - see the LICENSE file for details.

**Author**
**Anurag Raut**
**B.Tech in AI & Data Science**



## **Conclusion**

This project demonstrates a full CI/CD pipeline deployment on AWS, from security checks with KubeAudit to real-time monitoring via Grafana and Prometheus.

