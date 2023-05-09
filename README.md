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

## Deployment to EKS (AWS Elastic Kubernetes Service)

1. Create EKS cluster

    ```bash
    eksctl create cluster --name eks-cluster --version 1.14 --region us-east-1 --nodegroup-name standard-workers --node-type t2.micro --nodes 3 --nodes-min 1 --nodes-max 4
    ```
   After cluster is created, `eksctl` will automatically configure `kubectl` to use it.

2. Apply configuration file with described deployments and services for MongoDB and Mongo-Express images from Docker HUB:

    ```bash
   kubectl apply -f mongo-express-k8s.yaml
   ```
   
3. Check that all pods are running:

    ```bash
    kubectl get pods
    kubectl get deployments
    kubectl get services
    ```
   
4. Open minikube service in browser

    ```bash
    kubectl get services
    kubectl get service mongo-express-service -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'
    ```
