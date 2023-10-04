# Kubernetes Tasks
***
This repository documents the steps I took to complete two Kubernetes tasks: creating a basic NodePort service and setting resource requests and limits for a deployment.

## Task 1: Creating a Basic NodePort Service
### Objective
My objective was to create a basic Kubernetes service using NodePort.


## Steps Taken
1. Created a YAML file for the pod: I created a YAML file named deployment.yaml for a pod named "web-app-pod" running a web server container with the image "nginx:latest."

2. Deployed the pod: I deployed the pod to the cluster using the following command:

```kubectl apply -f deployment.yaml```

3. Created a NodePort service: I created a NodePort service named "web-app-service" to expose the pod on port 31000 using the service.yaml file.

4. Applied the service configuration: I applied the service configuration to the cluster using the following command:

```kubectl apply -f service.yaml```

5. Applied ```minikube service web-app-service``` to get the node IP address and allocated NodePort


## Task 2: Setting Resource Requests and Limits for a Deployment
### Objective
My objective was to set resource requests and limits for a Kubernetes deployment.

## Scenario
I had a Kubernetes deployment named "web-app-pod" running a critical application. To ensure resource utilization, I needed to configure resource requests and limits.

## Steps Taken
1. Described the current state: I used the following command to describe the current state of the "web-app-pod" deployment and checked for any existing resource requests and limits:

```kubectl describe deployment web-app-pod```

2. Modified the deployment YAML file: I updated the deployment YAML file deployment.yaml to set resource requests for CPU to "100m" and memory to "128Mi" for the application containers.

3. Set resource limits: I set resource limits for CPU to "200m" and memory to "256Mi" in the deployment YAML file.

4. Applied the changes: I applied the changes to the deployment using the following command:

```kubectl apply -f deployment.yaml```

5. Verified configuration: I verified that the resources were configured correctly for the containers in the "web-app-pod" by describing the deployment again:

```kubectl describe deployment web-app-pod```

6. To forward the port to localhost

```kubectl port-forward service/web-app-service 31000:31000```