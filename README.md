📌 Project Overview

This project demonstrates a complete DevOps workflow starting from containerization using Docker, moving into Kubernetes orchestration, and ending with cluster-wide monitoring using a DaemonSet.

The application is a Node.js app connected to a MySQL database, deployed and managed inside Kubernetes with production-like practices.
🏗️ Architecture Diagram
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/b5afe375-953f-44ad-9e3f-60d9fbdff72b" />
🧱 Tech Stack
Docker & Docker Compose
Kubernetes (Minikube)
Node.js
MySQL
Prometheus Node Exporter (Monitoring)
⚙️ 1. Docker Setup
Build Application Image
docker build -t nodejs-app .
Run with Docker Compose
docker-compose up -d
This sets up:
Node.js container
MySQL container
Internal networking
Environment variables

☸️ 2. Kubernetes Setup
Start Cluster
minikube start
Enable Add-ons
minikube addons enable metrics-server
minikube addons enable dashboard


🚀 3. Deploy to Kubernetes
Create Namespace
kubectl create namespace ivolve
Apply Configurations
kubectl apply -f k8s/

🧪 Labs Implementation
🔹 Lab 10: Node Taints
kubectl taint nodes <node-name> key=value:NoSchedule

🔹 Lab 11: Namespace & Resource Quotas
kubectl apply -f quota.yaml

🔹 Lab 12: ConfigMaps & Secrets
kubectl apply -f quota.yaml -n ivolve

🔹 Lab 13: Persistent Volumes
kubectl apply -f pv.yaml -n ivolve
kubectl apply -f pvc.yaml -n ivolve

🔹 Lab 14: StatefulSet (MySQL)
kubectl apply -f mysql-statefulset.yaml

🔹 Lab 15: Services & Internal Communication
Expose the Node.js application
kubectl apply -f service.yaml -n ivolve
kubectl get svc -n ivolve
minikube service nodejs-service -n ivolve
