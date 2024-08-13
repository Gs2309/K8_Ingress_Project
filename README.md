## How to Run

1. Clone the repository.
2. Install the necessary tools.
3. Start Minikube with 2 nodes.
4. Run the Ansible playbook:

# playbook

ansible-playbook ansible/k8s-setup.yml

# Kubernetes Project with Ansible Automation

## Project Overview

This project sets up a Kubernetes cluster using Minikube with Docker, deploys an Nginx Ingress Controller, and a sample Hello World application, all automated using Ansible.

## Prerequisites

- An EC2 instance running Amazon Linux with Docker installed.
- Minikube and kubectl installed.

## Directory Structure

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

