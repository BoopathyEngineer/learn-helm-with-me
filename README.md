# 🚀 Helm Deployment on Kubernetes (AWS EKS)

This project demonstrates how to deploy a **FastAPI application on Kubernetes using Helm**.  
The deployment runs on **AWS EKS** and exposes the application using a **LoadBalancer service**.

---

# 📌 Project Overview

Helm is the **package manager for Kubernetes**. Instead of managing multiple YAML files manually, Helm allows us to package applications into reusable **Helm Charts**.

In this project we:

- Created a custom Helm chart
- Parameterized configuration using `values.yaml`
- Deployed the application on Kubernetes
- Exposed it using a LoadBalancer
- Managed releases using Helm lifecycle commands

---

# 🏗 Architecture

```
Docker Image (FastAPI)
        ↓
     Helm Chart
        ↓
Kubernetes Deployment
        ↓
Kubernetes Service (LoadBalancer)
        ↓
AWS Elastic Load Balancer
        ↓
     Public Access
```

---

# 📂 Project Structure

```
my-chart/
│
├── Chart.yaml
├── values.yaml
└── templates/
    ├── deployment.yaml
    └── service.yaml
```

---

# ⚙️ Chart Configuration

## Chart.yaml

Defines metadata for the Helm chart.

```yaml
apiVersion: v2
name: mychart
description: A simple Helm chart for Kubernetes
version: 0.1.0
appVersion: "1.0"
```

---

# ⚙️ values.yaml

Used to parameterize the deployment.

```yaml
replicaCount: 2

image:
  repository: sboopathysdevops/devops-fastapi
  tag: v6

service:
  type: LoadBalancer
  port: 80
```

This file controls:

- Number of replicas
- Docker image
- Service type
- Port configuration

---

# 🚀 Deployment Steps

## 1️⃣ Install Helm Chart

```bash
helm install myapp .
```

Verify deployment:

```bash
kubectl get pods
kubectl get svc
```

---

# 🌐 Access Application

If using **LoadBalancer service**, Kubernetes automatically provisions an external endpoint.

Check the service:

```bash
kubectl get svc
```

Example output:

```
NAME    TYPE           EXTERNAL-IP
myapp   LoadBalancer   <AWS-ELB-DNS>
```

Access the application using the **ELB DNS name**.

---

# 📈 Scaling the Application

Helm makes scaling simple.

Example:

```bash
helm upgrade myapp . --set replicaCount=5
```

Check pods:

```bash
kubectl get pods
```

---

# 🔍 Helm Validation

Validate the Helm chart:

```bash
helm lint .
```

Expected output:

```
1 chart(s) linted, 0 chart(s) failed
```

---

# 📜 Helm Release History

Helm tracks deployment revisions.

```bash
helm history myapp
```

Example:

```
REVISION  STATUS      DESCRIPTION
1         superseded  Install complete
2         deployed    Upgrade complete
```

---

# 🔄 Rollback Deployment

If an upgrade fails, rollback easily.

```bash
helm rollback myapp 1
```

---

# 🧰 Tools Used

- Kubernetes
- Helm
- AWS EKS
- Docker
- FastAPI

---

# 🎯 Key Benefits of Helm

- Versioned deployments
- Easy scaling
- Parameterized configuration
- Rollback support
- Reusable Kubernetes templates

---

# 👨‍💻 Author

**Boopathy S**  
DevOps & Cloud Engineer  

Skills:
- Kubernetes
- AWS
- Terraform
- CI/CD
- MLOps

📧 Email: sboopathys98@gmail.com  
🔗 LinkedIn: https://www.linkedin.com/in/boopathy-subramani/

---

⭐ If you found this project useful, feel free to star the repository!
