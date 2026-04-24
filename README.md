# 🚀 Kubernetes End-to-End Project (Docker → K8s → Monitoring)

This project demonstrates a complete journey from containerization to Kubernetes orchestration, covering real-world DevOps concepts including deployments, storage, networking, security, and monitoring.

---

# 📌 Project Overview

The application is a **Node.js app with MySQL database**, deployed step-by-step through multiple labs:

* Docker & Docker Compose
* Kubernetes core objects
* Storage (PV/PVC)
* ConfigMaps & Secrets
* Init Containers
* Resource Management
* Network Policies
* Monitoring using DaemonSet

---

# 🧱 Tech Stack

* Docker & Docker Compose
* Kubernetes (Minikube)
* Node.js
* MySQL
* Prometheus Node Exporter

---

# 📂 Project Structure

```
K8S LABS/
│
├── nodejs-deployment.yaml
├── nodejs-service.yaml
├── mysql-statefulset.yaml
├── mysql-service.yaml
├── mysql2-service.yaml
├── configmap.yaml
├── secret.yaml
├── pv.yaml
├── pvc.yaml
├── quota.yaml
├── network-policy.yaml
├── node-exporter.yaml

```
#🏗️ Architecture Diagram
```

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/3f1aeef8-9273-4079-8c68-163e8dcaede1" />


---

# 🧪 Labs Breakdown

## 🔹 Lab 10–12: Docker & Compose

* Built Node.js application image
* Created Dockerfile
* Used Docker Compose to run:

  * Node.js container
  * MySQL container
* Configured environment variables for DB connection

---

## 🔹 Lab 13–14: Kubernetes Basics

* Created Kubernetes cluster using Minikube
* Deployed Node.js app using:

  * Deployment
  * Service (NodePort / ClusterIP)
* Verified application accessibility

---

## 🔹 Lab 15: Multi-tier App Deployment

* Connected Node.js app to MySQL inside Kubernetes
* Tested service-to-service communication
* Used test pods (busybox) for debugging

---

## 🔹 Lab 16: Init Containers & Database Setup

* Added Init Container to:

  * Wait for MySQL readiness
  * Initialize database
* Used:

  * ConfigMap (DB_HOST, DB_USER)
  * Secret (DB_PASSWORD)

---

## 🔹 Lab 17: Resource Management

* Added CPU & Memory:

  * Requests: `1 CPU`, `1Gi RAM`
  * Limits: `2 CPU`, `2Gi RAM`
* Verified using:

  ```bash
  kubectl describe pod
  kubectl top pod
  ```

---

## 🔹 Lab 18: Network Policy (Security)

* Created NetworkPolicy:

  * Allowed only Node.js pods to access MySQL
  * Restricted traffic to port `3306`
* Implemented zero-trust networking inside cluster

---

## 🔹 Lab 19: Monitoring with DaemonSet

* Created `monitoring` namespace
* Deployed Node Exporter using DaemonSet
* Ensured:

  * One pod per node
  * Metrics exposed on `:9100/metrics`

---

# 🔐 Key Concepts Covered

* Kubernetes Deployments & Services
* StatefulSets
* Persistent Volumes & Claims
* ConfigMaps & Secrets
* Init Containers
* Resource Requests & Limits
* Network Policies
* DaemonSets
* Cluster Debugging

---

# 🧪 How to Run

### 1. Start Minikube

```bash
minikube start
```

### 2. Apply Resources

```bash
kubectl apply -f .
```

### 3. Check Pods

```bash
kubectl get pods -A
```

---

# 📊 Monitoring Access

To check Node Exporter metrics:

```bash
kubectl port-forward -n monitoring <node-exporter-pod> 9100:9100
```

Then open:

```
http://localhost:9100/metrics
```

---

# ⚠️ Challenges Faced

* PVC stuck in Terminating state
* MySQL permission issues inside init containers
* ResourceQuota limiting pod creation
* Service name mismatches (DNS resolution issues)
* NetworkPolicy blocking unintended traffic

---

# 💡 Lessons Learned

* Kubernetes is state-sensitive (especially with storage)
* Service naming is critical for internal communication
* Init containers should be simple and focused
* Network policies enforce strong security boundaries
* Debugging requires checking logs, events, and resources together

---



---

# 👩‍💻 Author

**Zakya Akram**
DevOps & Cloud Enthusiast

---

# ⭐ If you found this helpful

Give this repo a star ⭐
