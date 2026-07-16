# minikube_kubernetes_project
this project is documenting the process of setting up kubernetes environment on local machine.

**Setting up minikube**
1- Downloading and installing virtual box
2- Downloading and installing minikube
3- Adding minikube to PATH environmental variable, run powershell as Admin and run below-

$oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine) if ($oldPath.Split(';') -inotcontains 'C:\minikube'){
  [Environment]::SetEnvironmentVariable('Path', $('{0};C:\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine)
}

4- Start your cluster

minikube start
