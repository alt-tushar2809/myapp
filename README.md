# myapp 
# My App - CI/CD Pipeline

This repository contains the code for a Node.js application deployed using a CI/CD pipeline with Jenkins, Docker, and Kubernetes.

## Files

- `app.js`: The Node.js application.
- `package.json`: Defines the app dependencies.
- `Dockerfile`: Instructions to build the Docker image.
- `deployment.yaml`: Kubernetes manifests for deployment and service.
- `Jenkinsfile`: Pipeline script for Jenkins.

## Prerequisites

- Jenkins server with Docker installed.
- Kubernetes cluster with `kubectl` configured.
- Docker Hub account for pushing images.

## Steps

1. Clone this repository.
2. Build and push the Docker image.
3. Deploy the app to Kubernetes using `kubectl apply -f deployment.yaml`.
