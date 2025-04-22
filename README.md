# ☸️ Kubernetes
This demo project is part of Module 9: AWS Services from Nana DevOps Bootcamp. They cover deploying services into a local Kubernetes cluster using tools like **Minikube**, and managing configurations with **ConfigMap** and **Secrets**

## 📦 Demo 1: Deploy MongoDB and Mongo Express into Local K8s Cluster
In this demo, we set up a local Kubernetes cluster using **Minikube** and deploy **MongoDB** along with its UI tool **Mongo Express**. Application configuration and credentials are managed using **ConfigMaps** and **Secrets**.

## 🚀 Technologies Used
- **Kubernetes (minikube)**: Container orchestration
- **Docker**: Conatiners
- **MongoDB**: Database
- **Mongo Express**: UI for MongoDB
  
## 🎯 Features

- **Setup local K8 cluster using Minikube**
- **Deploy MongoDB and Mongo-Express using ConfigMap and Secret**.


## 🏗 Project Architecture

<img src=""/>

## ⚙️ Project Configuration

### Setting up Minikube
1. Start Minikube
2. Install kubectl
3. Check the status of Minikube
4. Check current nodes
5. Check current services

### Deploying MongoDB and Mongo-Express
1. Create a mongo-secret.yaml file
5. encode tge username and password using base64
6. Update the mongo-scret.yaml file with the encoded username and password
7. Verify that the secret has been created
8. Create the deployment mongo.yaml file
9. Reference the secret file from mongo.yaml
10. Apply the mongo.yaml file
11. Check all components
12. Verify the mongo pod
13. Check the details of the pod
14. Add the mongo service
15. Reapply the mongo yaml file
16. Verify services
17. Verify that the service is pointing to the right pod
18. create a ConfigMap.yaml file
19. 
