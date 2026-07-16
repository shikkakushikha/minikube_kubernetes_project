# Project 01: Deploy MongoDB and Mongo Express on Kubernetes

## Project Overview

This project demonstrates the deployment of a two-tier application on Kubernetes using Minikube.

The application consists of:
- MongoDB (Database)
- Mongo Express (Web Interface)

<img width="603" height="460" alt="image" src="https://github.com/user-attachments/assets/2c7e1085-fd7d-4bce-9f7a-9e627c1ac771" />

## Project Workflow

1. Create MongoDB Secret.
2. Deploy MongoDB Pod.
3. Create MongoDB ClusterIP Service.
4. Create ConfigMap containing the database service name.
5. Deploy Mongo Express.
6. Reference Secret and ConfigMap in the Mongo Express Deployment.
7. Create a LoadBalancer Service for Mongo Express.
8. Access the application using Minikube.

# Create resources
kubectl apply -f <file>.yaml

# Verify resources
kubectl get pods
kubectl get services
kubectl get deployments

# Inspect resources
kubectl describe pod <pod-name>
kubectl logs <pod-name>

# Access Mongo Express
minikube service mongo-express-service

# Delete resources
kubectl delete -f <file>.yaml

# Troubleshooting

## Issue: Mongo Express connected to MongoDB but failed to display databases

### Problem

After deploying MongoDB and Mongo Express on Minikube, Mongo Express started successfully and connected to the database.

Logs showed:

```text
Database connected
Admin Database connected
```

However, it failed to display the databases and produced the following error:

```text
MongoError: Unsupported OP_QUERY command: listDatabases
```

---

## Root Cause

This issue was caused by an **incompatible combination of Docker image versions**.

The project initially used the latest MongoDB image, while the Mongo Express image was built for an older MongoDB protocol.

As a result, Mongo Express attempted to use the deprecated `OP_QUERY` command, which is no longer supported by newer MongoDB versions.

---

## Solution

Use compatible image versions instead of the `latest` tag.

### MongoDB

```yaml
image: mongo:6.0
```

### Mongo Express

```yaml
image: mongo-express:1.0.2
```

After updating the image versions and recreating the resourses the issue was resolved. and below screen is displayed

<img width="1918" height="1022" alt="image" src="https://github.com/user-attachments/assets/6092aaba-852e-408c-85b4-831d083409d7" />



