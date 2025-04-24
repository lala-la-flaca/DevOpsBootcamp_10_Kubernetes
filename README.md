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
     minikube start
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/1%20start.png" width=800 />
   
2. Install kubectl

   ```bash
     sudo snap install kubectl --classic
   ```
   
3. Check the status of Minikube
   
   ```bash
     minikube status
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/2%20status.png" width=800 />
   
4. Check current nodes
   
   ```bash
     kubectl get node
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/3%20get%20status%20node.png" width=800 />
   
5. Check current services
   
   ```bash
     kubectl get service
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/4%20get%20services.png" width=800 />
   

### Deploying MongoDB and Mongo-Express
1. Create the mongo-secret.yaml file.
   
   ```bash
       apiVersion: v1
      kind: Secret
      metadata:
        name: mongodb-secret
      type: Opaque
      data:
        mongo-root-username: xxxxx
        mongo-root-password: xxxxx
     
   ```
   <img src="" width=800 />
   
2. Encode the MongoDB username and password using Base64.
   
   ```bash
     echo -n 'username' | base64
     echo -n 'password' | base64
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/2%20Secret%20file%20enconding%20base64.png" width=800 />
   
3. Update mongo-secret.yaml with the encoded credentials.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/3%20SECRET%20FILE%20YAML%20WITH%20ENCODED%20PASSWORD%20EX.png" width=800 />
   
4. Apply the secret file and verify that the secret was created.
    
   ```bash
     kubectl apply -f mongo-secret.yaml
     kubectl get secret
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/4%20APPLYING%20MONGO-SECRET%20YAML%20FILE.png" width=800 />
   
5. Create the mongo.yaml deployment file.
    
   ```bash
   ```
   <img src="" width=800 />
   
6. Reference the secret in mongo.yaml.

   ```bash
      apiVersion: apps/v1 
      kind: Deployment
      metadata:
        name: mongodb-deployment
        labels:
          app: mongodb
      spec:
        replicas: 1
        selector:
          matchLabels:
            app: mongodb
        template: 
          metadata:
            labels:
              app: mongodb
          spec:
            containers:
            - name: mongodb
              image: mongo:4.4
              ports:
              - containerPort: 27017
              env:
              - name: MONGO_INITDB_ROOT_USERNAME
                valueFrom:
                  secretKeyRef:
                    name: mongodb-secret
                    key: mongo-root-username
              - name: MONGO_INITDB_ROOT_PASSWORD
                valueFrom:
                  secretKeyRef:
                    name: mongodb-secret
                    key: mongo-root-password
   ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/6%20referencing%20the%20secret%20file%20from%20mongo%20yaml%20file.png" width=800 />
   
7. Apply the mongo.yaml file.
    
   ```bash
     kubectl apply -f mongo.yaml
   ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/8%20deployment%20created.png" width=800 />
   
8. Verify that all components were created.
    
   ```bash
     kubectl get all
   ```

   <img src="" width=800 />
   
9. Confirm that the MongoDB pod is running.
    
   ```bash
   kubectl get pod
   ```
   
10. Inspect the MongoDB pod details.

    ```bash
      kubectl describe pod mongodb-deployment-7bfd7c5cc8-4jt2q
     ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/11%20to%20check%20pod%20%20info%20and%20if%20it%20is%20ok.png" width=800 />
   
11. Add a MongoDB service definition to mongo.yaml.

    <details><summary><strong>📝 3 Dashes</strong></summary>
    📝 Note: In a YAML file, three dashes (---) indicate the start of a new document. This allows multiple resource definitions to be included in a single file.

    ```bash
      ---
      apiVersion: v1
      kind: Service
      metadata:
        name: mongodb-service
      spec:
        selector:
          app: mongodb
        ports:
          - protocol: TCP
            port: 27017
            targetPort: 27017
     ```

   <img src="" width=800 />
   
12. Reapply the mongo.yaml file.

    ```bash
     ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_10_Kubernetes/blob/main/Img/13%20applying%20mongo%20yaml%20file%20with%20service.png" width=800 />
   
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
