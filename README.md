# Assignment-3

# 🚀 GitOps-Style Kubernetes Deployment with Argo CD (Local)

This project demonstrates a **GitOps-style workflow** using **Argo CD** to manage Kubernetes deployments on a **local Minikube cluster**.  
All Kubernetes manifests are stored in Git, and Argo CD continuously synchronizes the cluster state from the repository.

---

## 🎯 Objective

- Install Argo CD locally on Minikube
- Store Kubernetes manifests in Git
- Configure Argo CD to watch and apply manifests automatically
- Make changes via Git and observe automatic deployment without manual kubectl apply
- Simulate a real-world GitOps workflow locally

---

## 🛠 Tech Stack

- Kubernetes
- Minikube
- Argo CD
- Docker
- Git & GitHub
- Python (Flask)

---

## 🧠 GitOps Workflow Overview

Argo CD Setup (Local)
1. Start Minikube
minikube start --driver=docker

2. Install Argo CD
kubectl create namespace argocd

kubectl apply -n argocd \
  -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

3. Access Argo CD UI
kubectl port-forward svc/argocd-server -n argocd 9090:443

Open browser:

https://localhost:9090

Login:

Username: admin

Password:

kubectl get secret argocd-initial-admin-secret \
 -n argocd \
 -o jsonpath="{.data.password}" | base64 -d

 📦 Application Deployment via GitOps
Argo CD Application Configuration

Application Name: python-gitops

Repository: GitHub (this repo)

Path: .

Destination Cluster: https://kubernetes.default.svc

Namespace: default

Sync Policy: Automatic



