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
1. Create the mongo-secret.yaml file.
5. Encode the MongoDB username and password using Base64.
6. Update mongo-secret.yaml with the encoded credentials.
7. Apply the secret file and verify that the secret was created.
8. Create the mongo.yaml deployment file.
9. Reference the secret in mongo.yaml.
10. Apply the mongo.yaml file.
11. Verify that all components were created.
12. Confirm that the MongoDB pod is running.
13. Inspect the MongoDB pod details.
14. Add a MongoDB service definition to mongo.yaml.
15. Reapply the mongo.yaml file.
16. Verify that the service is created.
17. Ensure the service points to the correct pod.
18. Create the ConfigMap.yaml file.
19. Create the mongo-express.yaml deployment file and reference the ConfigMap from MongoExpress container.
20. Verify pods.
21. Verify that all pods are running.
22. Verify the logs of the Mongo-Express pod to ensure it started successfully.
23. Verify that the necessary services have been created.
24. <details><summary><strong>External IP when using Minikube</strong></summary>  > :memo: **Note:** When using Minikube, external IPs are handled differently. Use the following command to access the service.
  ```bash
    
  ```
</details>
26. Access Mongo Express using the External IP address. If you're using Minikube, use the URL provided by the minikube service mongo-express --url command.
