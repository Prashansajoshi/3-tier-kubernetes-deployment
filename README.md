# 3-tier-kubernetes-deployment
# Quotes Application on Kubernetes  

This project deploys a Quotes application on Kubernetes, consisting of:  
- **MySQL Database**: Stores quotes data.  
- **Backend API**: Serves quotes via RESTful endpoints.  
- **Frontend**: Displays quotes fetched from the backend.  
- **Ingress Controller**: Manages external access.  

## Prerequisites  
- Docker & Kubernetes (Minikube/K3s/K8s)  
- `kubectl` & `helm` installed  
- Container registry (Docker Hub or similar)  

## Setup Instructions  

### 1. Build & Push Docker Images 

docker build -t <your-docker-username>/quotes-db:latest ./mysql
docker build -t <your-docker-username>/quotes-api:latest ./backend
docker build -t <your-docker-username>/quotes-frontend:latest ./frontend

docker push <your-docker-username>/quotes-db:latest
docker push <your-docker-username>/quotes-api:latest
docker push <your-docker-username>/quotes-frontend:latest


### 2. Deploy to Kubernetes

kubectl apply -f manifests/database
kubectl apply -f manifests/backend
kubectl apply -f manifests/frontend
kubectl apply -f manifests/ingress


### 3. Verify Deployment

kubectl get pods -n database
kubectl get pods -n backend
kubectl get pods -n frontend
kubectl get ingress -n frontend
### 4. Access the Application
Retrieve the ingress IP and open it in a browser.

kubectl get ingress -n frontend

### Cleanup

kubectl delete -f manifests/

## Notes
Ensure mysql-secret and mysql-config exist before deploying the database.

Adjust Ingress rules if needed based on your Kubernetes setup.


This keeps the README short, clear, and actionable. Let me know if you want any refinements! 🚀