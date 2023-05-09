# Mongo-Express image deployment example

In this example we will deploy a Mongo-Express image to a Kubernetes cluster along with a Mongo database.

## Prerequisites

* A Kubernetes cluster with kubectl configured
* A Docker Hub account

## Steps

1. Start minikube locally

    ```bash
    minikube start
    ```
   
2. Switch kubectl context to use minikube

    ```bash
    kubectl config use-context minikube
    ```

3. Apply configuration file with described deployments and services for MongoDB and Mongo-Express images from Docker HUB:

    ```bash
   kubectl apply -f mongo-express-k8s.yaml
   ```
   
4. Check that all pods are running:

    ```bash
    kubectl get pods
    ```
   
5. Check that all services are running:

   ```bash
    kubectl get services
    ```
   
6. Check that all deployments are running:

    ```bash
    kubectl get deployments
    ```

7. Open minikube service in browser

    ```bash
    minikube service mongo-express-service
    ```
