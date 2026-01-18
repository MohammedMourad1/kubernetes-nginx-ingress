# 🚀 Kubernetes Nginx Deployment with Ingress

This project demonstrates a clean and production-oriented Kubernetes setup using Nginx, exposed internally via a ClusterIP Service and externally through an Ingress.

The focus of this project is to demonstrate correct Kubernetes architecture and traffic flow, not just running a container.

---

##  Architecture

Client  
→ Ingress (hostname-based routing)  
→ Service (ClusterIP)  
→ Pods (Nginx)

Ingress routes traffic to Services, and Services route traffic to Pods.

---

##  Project Structure

k8s-project/
- app/
- docs/
- k8s/
  - config/
  - deployment/
    - nginx-deployment.yaml
  - service/
    - nginx-service.yaml
  - ingress/
    - nginx-ingress.yaml
- README.md

---

## ⚙️ Kubernetes Components

Deployment  
Manages the Nginx Pods, ensures availability, and supports scaling.

Service (ClusterIP)  
Provides a stable internal endpoint and abstracts Pod IP changes.

Ingress  
Exposes the application via HTTP using hostname-based routing and forwards traffic to the Service.

---

## 🔍 Why ClusterIP and Ingress

ClusterIP is used for internal communication inside the cluster.  
Ingress is used to expose HTTP traffic in a structured and production-like way.  
This approach avoids NodePort and mirrors real-world Kubernetes setups.

---

##  Requirements

- Linux environment
- Minikube
- kubectl
- curl

---

##  How to Run

Start Minikube:

minikube start

Enable Ingress:

minikube addons enable ingress

Wait until the ingress controller is running:

kubectl get pods -n ingress-nginx

Apply Kubernetes manifests:

kubectl apply -f k8s/deployment/nginx-deployment.yaml  
kubectl apply -f k8s/service/nginx-service.yaml  
kubectl apply -f k8s/ingress/nginx-ingress.yaml

---

##  Local Hostname Configuration

Get Minikube IP:

minikube ip

Add the following entry to /etc/hosts inside the VM:

<MINIKUBE_IP> nginx.local

Example:

192.168.49.2 nginx.local

---

##  Test

curl http://nginx.local

Expected result:

Welcome to nginx!

---

##  Notes

Hostname resolution using /etc/hosts is local to the system where it is configured.  
This setup is intentionally minimal and designed for learning Kubernetes networking fundamentals.

---

## 👤 Author

Mohamed – DevOps and Kubernetes learning project
