# Welcome to the Dockerized TypeScript Minikube Application!

This repository contains a complete setup for running a Dockerized TypeScript application in a Kubernetes cluster. We'll use Minikube for local development.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Quick Start](#quick-start)
3. [Building the Docker Image](#building-the-docker-image)
4. [Deploying to Minikube](#deploying-to-minikube)
5. [Testing the Application](#testing-the-application)
6. [Additional Notes](#additional-notes)

## Prerequisites

Before starting, make sure you have the following installed on your system:

- [Node.js](https://nodejs.org/en/download/)
- [Docker](https://docs.docker.com/get-docker/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## Quick Start

To quickly test out the application, run the following commands:

git clone https://github.com/username/your-repo.git
cd your-repo
minikube start
eval $(minikube docker-env)
docker build -t your-app .
kubectl apply -f deployment.yaml
minikube service your-app

optional:
run `yarn install`
create a SQL database with `docker run -p 3306:3306 -e MYSQL_ROOT_PASSWORD=test -e MYSQL_DATABASE=test -e MYSQL_USER=test -e MYSQL_PASSWORD=test -d mariadb:5.5`
run `yarn typeorm migration:run`
open `http://localhost:3000/posts` and see an empty list
test with `curl`, `postman` or similar tools

## Building the Docker Image
To build the Docker image, navigate to the root directory of the repository and run the following command:

1. docker build -t your-app .
2. This command will build a Docker image named "your-app" using the Dockerfile located in the repository.

## Deploying to Minikube
Once the Docker image is built, you can deploy it to your local Minikube cluster. First, ensure that Minikube is running by executing the following command:

1. minikube start

apply the Kubernetes deployment configuration using kubectl:

1. Copy code
2. kubectl apply -f deployment.yaml
This command will create a Deployment, a Service, and an Ingress resource for your application.

## Testing the Application
After the deployment is complete, you can access the application using the following command:

minikube service your-app
This command will open a web browser and navigate to the application's URL.

## Additional Notes

To view the logs of your application running inside the Docker container, you can use the docker logs command. For example:

docker logs <container_id>

To clean up your local Minikube environment, you can run the following commands:

kubectl delete -f deployment.yaml
minikube stop
minikube delete

These commands will remove the deployed application, stop the Minikube virtual machine, and delete the Minikube cluster.

I hope you find this repository helpful! If you have any questions or need assistance, feel free to open an issue or contact me directly.