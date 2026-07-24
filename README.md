# Kubernetes Local Setup using Minikube + Docker

This repository contains my local Kubernetes learning environment using **Minikube** with the **Docker driver** on Windows 11.

---

## 📋 Prerequisites

- Docker Desktop
- Minikube
- kubectl
- Windows PowerShell

---

## 🚀 Verify Installation

### install/Check Docker (WSL-ubuntu)

Steps <br>
Install/Open Docker Desktop. <br>
Go to Settings → Resources → WSL Integration. <br>
Enable: <br>
✅ Enable integration with my default WSL distro <br>
✅ Ubuntu <br>
Click Apply & Restart. <br>

```powershell
docker version
docker info
docker ps
```

### Install/ Check Minikube (WSL-ubuntu)

```powershell
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
minikube version
```

### install/Check kubectl (WSL-ubuntu)

```powershell
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
kubectl version --client
```

---

## ▶️ Start Minikube

```powershell
minikube start --driver=docker
```

---

## ✅ Verify Cluster

```powershell
minikube status
```

Expected Output

```text
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

Check Kubernetes Nodes

```powershell
kubectl get nodes
```

Expected Output

```text
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   2m    v1.xx.x
```

---

## 📦 Useful Commands

Start Cluster

```powershell
minikube start --driver=docker
```

Stop Cluster

```powershell
minikube stop
```

Delete Cluster

```powershell
minikube delete
```

Check Cluster Status

```powershell
minikube status
```

Open Kubernetes Dashboard

```powershell
minikube dashboard
```

SSH into Minikube

```powershell
minikube ssh
```

---

# Troubleshooting

## Issue 1

### Error

```text
Profile "minikube" not found.
```

### Cause

No Minikube cluster has been created.

### Solution

```powershell
minikube start --driver=docker
```

---

## Issue 2

### Error

```text
Unable to connect to the server:
dial tcp [::1]:8080
```

### Cause

The Kubernetes API Server is not running because Minikube has not started.

### Solution

```powershell
minikube start --driver=docker
```

Verify

```powershell
kubectl get nodes
```

---

## Issue 3

### Error

```text
failed to connect to the docker API...
```

### Cause

Docker Desktop is not running or Docker Engine is unavailable.

### Solution

1. Start Docker Desktop.
2. Wait until Engine Running is displayed.
3. Retry:

```powershell
docker ps
```

---

## Issue 4

### Error

```text
GUEST_DRIVER_MISMATCH
The existing "minikube" cluster was created using the "virtualbox" driver.
```

### Cause

An old Minikube cluster was created using VirtualBox, but Docker is now being used as the driver.

### Solution

Delete the old cluster and recreate it using Docker.

```powershell
minikube delete
```

```powershell
minikube start --driver=docker
```

---

## 📚 References

- https://minikube.sigs.k8s.io/docs/
- https://kubernetes.io/docs/
- https://kubernetes.io/docs/tasks/tools/

---

## 👩‍💻 Author

**Shikha Singh**
