🎲 Rolling the Dice on DevOps: CI/CD and Kubernetes for a Board Game Web App
Project Overview
This project demonstrates the end-to-end CI/CD pipeline implementation for deploying a Board Game Web Application using modern DevOps practices. The deployment leverages Jenkins, Docker, Kubernetes, and AWS, along with robust monitoring using Prometheus and Grafana. The infrastructure ensures automated builds, deployments, and continuous monitoring, embodying best practices in DevOps and cloud-native architecture.

Key Features
CI/CD Pipeline: Automated build, test, and deployment using Jenkins.
Containerization: Application packaged using Docker for consistent deployments.
Orchestration: Kubernetes clusters manage and scale application containers.
Monitoring: Integrated Prometheus and Grafana for performance and health monitoring.
Cloud Deployment: Deployed on AWS EC2 instances with security configurations.
Tools and Technologies
Version Control: Git
Containerization: Docker
CI/CD: Jenkins
Orchestration: Kubernetes (with kubeadm, NGINX, and Calico)
Monitoring: Prometheus, Grafana, Node Exporter, Blackbox Exporter
Cloud Infrastructure: AWS EC2, Security Groups, Storage Allocation
Code Quality: SonarQube
Build Tool: Apache Maven
Project Architecture
plaintext
Copy code
+--------------------------------------------------+
|                  Jenkins Server                  |
+--------------------------------------------------+
           |                      |              
           v                      v              
+------------------+     +-----------------+       
|     Docker       |     |     SonarQube   |       
+------------------+     +-----------------+       
           |                      |              
           v                      v              
+------------------+   +-------------------------+
|    Kubernetes    |<->|    Prometheus/Grafana   |
|      Cluster     |   | (Monitoring & Alerts)   |
+------------------+   +-------------------------+
           |
           v
+--------------------+
|    AWS EC2 Nodes   |
+--------------------+
Project Setup
Follow these steps to set up and deploy the project.

Prerequisites
Ensure you have the following installed:

Git
Docker
Jenkins
Kubernetes (kubeadm)
AWS CLI
Maven
Prometheus & Grafana
SonarQube
1. Clone the Repository
bash
Copy code
git clone https://github.com/abhishekporwal-836/Board-Game-CICD.git
cd Board-Game-CICD
2. Set Up Jenkins
Install Jenkins on your AWS EC2 instance:

bash
Copy code
sudo apt-get update
sudo apt-get install openjdk-11-jdk -y
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins -y
sudo systemctl start jenkins
Access Jenkins via http://<your-ec2-public-ip>:8080 and complete the setup wizard.

Install necessary plugins in Jenkins:

Docker Pipeline
Kubernetes
Prometheus
SonarQube Scanner
3. Configure Docker and Kubernetes
Install Docker:

bash
Copy code
sudo apt-get install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
Install Kubernetes:

bash
Copy code
sudo apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
Initialize Kubernetes Cluster:

bash
Copy code
sudo kubeadm init
Set Up kubectl Access:

bash
Copy code
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
4. CI/CD Pipeline Configuration
Jenkins Pipeline Configuration:

In Jenkins, create a new pipeline job and use the following Jenkinsfile:

groovy
Copy code
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t board-game-app .'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
            }
        }
        stage('Monitoring Setup') {
            steps {
                sh 'kubectl apply -f k8s/monitoring.yaml'
            }
        }
    }
}
Add Credentials for Docker, Kubernetes, and SonarQube in Jenkins.

5. Monitoring Setup
Install Prometheus and Grafana on your Kubernetes cluster:

bash
Copy code
kubectl apply -f k8s/prometheus.yaml
kubectl apply -f k8s/grafana.yaml
Access Grafana to visualize metrics:

plaintext
Copy code
http://<your-cluster-ip>:3000
Usage
Trigger a Build: Go to Jenkins and run the pipeline job.

Monitor Deployment: Check the status of the Kubernetes pods:

bash
Copy code
kubectl get pods
View Metrics: Access Grafana dashboards for application and cluster metrics.

Screenshots
CI/CD Pipeline in Jenkins

Grafana Monitoring Dashboard

Future Enhancements
Implement automated rollback on deployment failure.
Integrate Helm charts for simplified Kubernetes deployment.
Add Slack notifications for pipeline status updates.
License
This project is licensed under the MIT License.
