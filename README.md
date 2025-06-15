# Simple Scalable Web App on DigitalOcean Kubernetes

This project demonstrates how to deploy a simple containerized web application using DigitalOcean Kubernetes (DOKS). 
The app is packaged with Docker and deployed to a Kubernetes cluster with autoscaling and load balancing enabled.

The Kubernetes setup includes a `Deployment` for running the app in pods, a `Service` of type LoadBalancer to expose it to the internet, 
and a `HorizontalPodAutoscaler` that automatically adds or removes pods based on CPU usage. This ensures scalability and performance as traffic increases.

To deploy, just clone this repo, build and push your Docker image to Docker Hub, and apply the Kubernetes YAML files using `kubectl`. 
A DigitalOcean Load Balancer will handle incoming traffic, and your app will scale automatically as needed.

This setup is cost-conscious, easy to maintain, and ideal for teams wanting to learn how to run containerized apps in a production-ready cloud environment. 
See the `k8s/` folder for deployment files and follow the README instructions to get started quickly.

Attached Presentation file shows the step by step process on how to implement the same.


# Deployment Guide for refernce


# Deploying a Scalable Web App on DigitalOcean Kubernetes (DOKS)

This guide explains how to deploy this containerized web app using DigitalOcean Kubernetes (DOKS) with a load balancer and autoscaling.

---

## Prerequisites

- Docker installed  
- A Docker Hub account  
- A DigitalOcean account  
- `kubectl` installed  
- (Optional) `doctl` CLI for automation  

---

## Step 1: Clone the Repository

```bash
git clone https://github.com/<your-username>/<this-repo>.git
cd <this-repo>
```

---

## Step 2: Build and Push Docker Image

```bash
docker build -t yourdockerhubusername/myapp .
docker push yourdockerhubusername/myapp
```

> **Update** the image name in `k8s/deployment.yaml`:
```yaml
image: yourdockerhubusername/myapp
```

---

## Step 3: Create a Kubernetes Cluster on DigitalOcean

1. Go to the [DigitalOcean Kubernetes Dashboard](https://cloud.digitalocean.com/kubernetes).  
2. Click **Create Cluster**:  
   - Choose a region (e.g., NYC1)  
   - Use at least 2 nodes (e.g., `s-2vcpu-4gb`)  
   - Click **Create**  

---

## Step 4: Connect `kubectl` to Your Cluster

1. In DigitalOcean dashboard → Cluster → click **Download Config File**  
2. In your terminal:

```bash
export KUBECONFIG=/path/to/your/kubeconfig.yaml
kubectl get nodes
```

You should see the nodes listed.

---

## Step 5: Deploy the App to Kubernetes

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
kubectl apply -f k8s/hpa.yaml
```

---

## Step 6: Access the App

Check the external IP of your LoadBalancer:

```bash
kubectl get svc
```

Open the `EXTERNAL-IP` in your browser to access the app.

---
