# Node.js Application Deployment on Kubernetes

This repository contains the codebase and deployment configurations for a Node.js application deployed on a local Kubernetes cluster. The deployment includes horizontal pod autoscaling (HPA), resource limits, stress testing, monitoring, and documentation.

## Getting Started

### Prerequisites

- Docker
- Minikube
- kubectl
- Hey (or any other load testing tool)

### Installation

1. Clone the repository:
   git clone <repository_url>
   cd nodejs-kubernetes-deployment
   
## Build and push the Docker image to Minikube's Docker daemon: ##

docker build -t my-node-app .
docker tag my-node-app:latest minikube/my-node-app:latest
docker push minikube/my-node-app:latest

## Apply the Kubernetes deployment manifest ##

kubectl apply -f deployment.yaml

## Enable metrics server and configure HPA ##

minikube addons enable metrics-server
kubectl apply -f hpa.yaml

 ## Perform stress testing using Hey or similar tool ##

 https://github.com/rakyll/hey

 hey -n 1000 -c 10 http://<minikube_ip>:3000

