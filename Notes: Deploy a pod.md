## Deploy a pod
1. install kubectl (refer kubectl documentation)
2. install local cluster (minikube, kind, k3s, *kind is better*)
3. create a cluster 
```powershell
   minikube start
```
   minikube will create VM first then create a single node K8s cluster 
   for that you need hypervisor as well, install that --driver

4. install/create pod (refer k8s documentation for YAML file: https://kubernetes.io/docs/concepts/workloads/pods/)

## Create a pod using a YAML file:
```powershell
 kubectl apply -f pod.yaml
```
## check if its running:
```powershell
 curl IP address
```

<img width="411" height="356" alt="image" src="https://github.com/user-attachments/assets/a0337593-51cd-4a7e-88ff-e11e2b224038" />

<img width="593" height="323" alt="image" src="https://github.com/user-attachments/assets/56456b94-8385-4291-80e1-eb26a2a25880" />

<img width="452" height="284" alt="image" src="https://github.com/user-attachments/assets/ca2edfa3-d330-4d90-8df7-3ad15b6f0b2a" />


NOTE: kubectl Quick Reference : https://kubernetes.io/docs/reference/kubectl/quick-reference/

#kubectl apply -f pod.yaml → Creates the resource if it doesn't exist, and updates it if it does.
#kubectl create -f pod.yaml → Creates the resource only once. It will fail if the resource already exists.
