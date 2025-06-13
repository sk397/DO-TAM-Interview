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
