## Project Overview

This project sets up a Kubernetes cluster using Minikube with Docker deploys an Nginx Ingress Controller & a sample Hello World application, all automated using Ansible.

## Prerequisites

- An EC2 instance running Amazon Linux with Docker installed. (Min 2CPUs, 2GB RAM, 20GB Storage)
- Minikube and kubectl installed

 ## How to Run

1. Update the Linux system and Plan your directory structure.
2. Install the necessary tools.
3. Start Minikube with 2 nodes.
4. Run the Ansible playbook:

# playbook
ansible-playbook ansible/k8s-setup.yml   (Inclusive of application deployment TASK & Ingress deployment TASK)

# Manifests
 hello-world-deployment.yaml
 hello-world-ingress.yaml

## Directory Structure
**INSIDE ** K8_Ingress_Project Directory
.
├── ansible
│   ├── k8s-setup.yml
├── manifests
│   ├── hello-world-deployment.yaml
│   ├── hello-world-ingress.yaml
├── tls
│   ├── tls.crt
│   ├── tls.key
└── README.md

# VERIFY the Project:

1. Verify Minikube is running
 -> minikube status

2. Check Kubernetes Nodes (Ideally should have 2 nodes)
-> kubectl get nodes

3. Verify Nginx Ingress Controller
-> kubectl get pods -n default -l app.kubernetes.io/name=ingress-nginx

4. Verify Deployments(As defined by the Manifest):
-> kubectl get deployments

5. Verify Pods (hello-world pods)
-> kubectl get pods

6. Verify Services (To expose the application to the Internet)
-> kubectl get services

7. Verify Ingress (for routing configuration validation):
-> kubectl get ingress

8. Check Logs (in case of any issues)
Inspect logs of the hello-world pod & Nginx Ingress Controller for errors or issues:
-> kubectl logs hello-world
-> kubectl logs nginx-ingress -n default (As the resources are created in the default namespace)

9. Access the Application
-> minikube ip  &  (http://192.168.58.2/hello-world)

10. Verify TLS/SSL (check that HTTPS is working):
GET -> minikube ip
Navigate to https://192.168.58.2/hello-world and ensure a secure connection.

11. Test Ansible Playbook Idempotency
- Run your Ansible playbook again to ensure it is idempotent and no errors are encountered:
-> ansible-playbook k8s-setup.yml

12. Check Cluster Resources
- List all resources in the default namespace to ensure everything is deployed correctly:
-> kubectl get all -n default



