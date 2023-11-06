# YoloApp Deployment on Google Kubernetes Engine (GKE)

This repository contains the configuration files and instructions to deploy the YoloApp application on Google Kubernetes Engine (GKE). YoloApp is a multi-container application consisting of a MongoDB database, a backend service, and a client application.

## Prerequisites

Before deploying the YoloApp on GKE, make sure you have the following prerequisites in place:

- A running Google Kubernetes Engine cluster.
- `kubectl` CLI tool configured to access your GKE cluster.
- Docker installed to build and push custom Docker images if needed.

## Deployment Steps

Follow the steps below to deploy the YoloApp on your GKE cluster:
### 1. Create Persistent Volumes (Optional)

If you want to use persistent storage for the MongoDB database, create a Persistent Volume (PV) and a Persistent Volume Claim (PVC) by modifying the provided YAML files:

- `yolo-pv.yaml`: Define the Persistent Volume and the Persistent Volume Claim.

Deploy the persistent volume using:
```bash
kubectl apply -f yolo-pv.yaml
```

### 2. Deploy MongoDB StatefulSet and Headless Service

- Apply the MongoDB StatefulSet and Headless Service YAML file using
```bash
 kubectl apply -f yolo-mongo-statefulset.yaml
 ```

### 3. Deploy Yolo Application/Pod

- Apply the Backend Deployment and Service YAML file using:
```bash
 kubectl apply -f yolo-deployment.yaml
 ```

### 4. Deploy Yolo Service

- Apply the Client Deployment and Service YAML file using:
```bash
 kubectl apply -f yolo-services.yaml
 ```


### 5. Verify Deployment

Use the following commands to verify the deployment:

```bash
kubectl get pods
```
![Alt text](<../explanation-images/pods running.png>)


```bash
kubectl get services
```
![Alt text](<../explanation-images/Services and External IP.png>)

You should see the pods and services running successfully.

### 6. Access the YoloApp
To access the YoloApp, use the client's service IP and port (e.g., http://<Client-Service-IP>:3000). You can access the client application in a web browser.
![Alt text](<../explanation-images/app running on IP.png>)

## Application
![Alt text](<../explanation-images/full app with product on GKE.png>)

## Customization
You can customize the YAML files to adjust resources, image versions, and other settings as per your project requirements.

## Clean Up
To clean up the deployment, you can use the `kubectl delete` command for each resource, starting from the services and deployments and ending with the MongoDB StatefulSet.
