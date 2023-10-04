kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pod
kubectl port-forward service/web-app-service 31000:31000


Kubernetes Tasks
This repository documents the steps I took to complete two Kubernetes tasks: creating a basic NodePort service and setting resource requests and limits for a deployment.

Task 1: Creating a Basic NodePort Service
Objective
My objective was to create a basic Kubernetes service using NodePort.

Scenario
I had a simple web application running in a Kubernetes pod. My task was to expose this application to the external world using a NodePort service.

Steps Taken
Created a YAML file for the pod: I created a YAML file named web-app-pod.yaml for a pod named "web-app-pod" running a web server container with the image "nginx:latest."

Deployed the pod: I deployed the pod to the cluster using the following command:

bash
Copy code
kubectl apply -f web-app-pod.yaml
Created a NodePort service: I created a NodePort service named "web-app-service" to expose the pod on port 31000 using the web-app-service.yaml file.

Applied the service configuration: I applied the service configuration to the cluster using the following command:

bash
Copy code
kubectl apply -f web-app-service.yaml
Accessed the service: I ensured that the service was accessible from outside the cluster using the Node's IP address and the allocated NodePort (e.g., http://<Node_IP>:31000).

Task 2: Setting Resource Requests and Limits for a Deployment
Objective
My objective was to set resource requests and limits for a Kubernetes deployment.

Scenario
I had a Kubernetes deployment named "my-app-deployment" running a critical application. To ensure resource utilization, I needed to configure resource requests and limits.

Steps Taken
Described the current state: I used the following command to describe the current state of the "my-app-deployment" deployment and checked for any existing resource requests and limits:


kubectl describe deployment my-app-deployment
Modified the deployment YAML file: I updated the deployment YAML file (e.g., my-app-deployment.yaml) to set resource requests for CPU to "100m" and memory to "128Mi" for the application containers.

Set resource limits: I set resource limits for CPU to "200m" and memory to "256Mi" in the deployment YAML file.

Applied the changes: I applied the changes to the deployment using the following command:

bash
Copy code
kubectl apply -f my-app-deployment.yaml
Verified configuration: I verified that the resources were configured correctly for the containers in the "my-app-deployment" by describing the deployment again:

bash
Copy code
kubectl describe deployment my-app-deployment
