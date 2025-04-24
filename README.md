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

   ```bash
   ```
   
2. Install kubectl

   ```bash
   ```
   
3. Check the status of Minikube
   
   ```bash
   ```
   
4. Check current nodes
   
   ```bash
   ```
   
5. Check current services
   
   ```bash
   ```
   

### Deploying MongoDB and Mongo-Express
1. Create the mongo-secret.yaml file.
   
   ```bash
   ```
   
2. Encode the MongoDB username and password using Base64.
   
   ```bash
   ```
   
3. Update mongo-secret.yaml with the encoded credentials.
   
   ```bash
   ```
   
4. Apply the secret file and verify that the secret was created.
    
   ```bash
   ```
   
5. Create the mongo.yaml deployment file.
    
   ```bash
   ```
   
6. Reference the secret in mongo.yaml.

    
   ```bash
   ```

   <img src="" width=800 />
   
7. Apply the mongo.yaml file.
    
   ```bash
   ```

   <img src="" width=800 />
   
8. Verify that all components were created.
    
   ```bash
   ```

   <img src="" width=800 />
   
9. Confirm that the MongoDB pod is running.
    
   ```bash
   ```

   <img src="" width=800 />
   
10. Inspect the MongoDB pod details.
    
   ```bash
   ```

   <img src="" width=800 />
   
11. Add a MongoDB service definition to mongo.yaml.
    
   ```bash
   ```

   <img src="" width=800 />
   
12. Reapply the mongo.yaml file.
    
   ```bash
   ```

   <img src="" width=800 />
   
13. Verify that the service is created.
    
   ```bash
   ```

   <img src="" width=800 />
   
14. Ensure the service points to the correct pod.
    
   ```bash
   ```

   <img src="" width=800 />
   
15. Create the ConfigMap.yaml file.
    
   ```bash
   ```

   <img src="" width=800 />
   
16. Create the mongo-express.yaml deployment file and reference the ConfigMap from MongoExpress container.
    
   ```bash
   ```

   <img src="" width=800 />
   
17. Verify pods.
    
   ```bash
   ```

   <img src="" width=800 />
   
18. Verify that all pods are running.
    
   ```bash
   ```

   <img src="" width=800 />
   
19. Verify the logs of the Mongo-Express pod to ensure it started successfully.
    
   ```bash
   ```

   <img src="" width=800 />
   
20. Verify that the necessary services have been created.
    
   ```bash
   ```

   <img src="" width=800 />
   
21. <details><summary><strong>External IP when using Minikube</strong></summary>
    📝 Note: When using Minikube, external IPs are handled differently. Use the following command to access Mongo-express.

    ```bash

    ````

    <img src="" width=800 />
      
</details>

22. Access Mongo Express using the External IP address. If you're using Minikube, use the URL provided by the minikube service mongo-express --url command.

  <img src="" width=800 />
