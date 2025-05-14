# K8S-DEMO-Kubernetes-MongoDB-WebApp-Deployment
This project demonstrates a simple Kubernetes deployment using: 
- A MongoDB instance 
- A Node.js-based web application (`nanajanash/k8s-demo-apps`) 
- Kubernetes Secrets and ConfigMaps for secure configuration 
- Minikube for local development

📁 Project Structure

    K8S-DEMO/
     ├── mongo-config.yml # ConfigMap for MongoDB connection URL
     ├── mongo-secret.yml # Kubernetes Secret (excluded values)
     ├── mongo.yml # MongoDB Deployment and Service
     ├── webapp.yml # Web Application Deployment and Service

⚙️ Prerequisites

- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- Docker (if using Minikube with Docker driver)

🚀 Getting Started

 1. Start Minikube

```bash
minikube start --driver=docker

2. Create Kubernetes resources
Apply them in order to ensure dependencies are resolved.

bash
kubectl apply -f mongo-config.yml
kubectl apply -f mongo-secret.yml
kubectl apply -f mongo.yml
kubectl apply -f webapp.yml

🔐 Secret File Warning
For security, the mongo-secret.yml in this repo excludes base64-encoded credentials.
You need to add them manually before deploying.

apiVersion: v1
kind: Secret
metadata:
  name: mongo-secret
type: Opaque
data:
  mongo-user: <base64-encoded-username>
  mongo-password: <base64-encoded-password>

To encode your values:

echo -n 'your-username' | base64
echo -n 'your-password' | base64

🌐 Accessing the Web App
Start the service and open it in your browser:

minikube service webapp-service
This opens a browser window with your web app running on port 30100

or use 
minikubeIP/nodePort(30000-32767)

🧹 Clean Up
To stop and delete the cluster:

minikube stop
minikube delete



