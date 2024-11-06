# Minikube
### To Setup Minikube and access the kubernetes using kubectl

Pre-req

    Ubuntu 22 machine with t3.medium (2 vCPU & 2 RAM)
    20 GB storage

To install minikube on machine

Launch ubuntu22 with t3.medium instance and SSH to machine

You can refer this doc

https://minikube.sigs.k8s.io/docs/start/

Install docker

sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install docker.io -y
sudo usermod -aG docker ubuntu
sudo chmod 777 /var/run/docker.sock
newgrp docker
sudo systemctl restart docker

Install minikube

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start --driver=docker

![image](https://github.com/user-attachments/assets/c78e691d-607f-4c8d-92dd-30d0bf1a93b2)

Minikube start documentation
https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download

To install kubectl on machine (Cli for Minikube - Kubectl)

you can refer this doc

https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

Method2: I'm going to Install using native package management

sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
kubectl cluster-info

![image](https://github.com/user-attachments/assets/1c402f0c-3f16-437c-b2c9-ef21a2815c27)

Deployment our single pod in kubernetes cluster

![image](https://github.com/user-attachments/assets/b86d4bef-e769-4af1-a739-d1a22fd35e8b)

To setup Kubernetes cluster using minikube and access it using kubectl
https://github.com/kohlidevops/minikube-kubectl-setup/blob/main/README.md

Deploy our first pod in Kubernetes cluster
We are going to deploy our first pod in cluster using below doc.
https://kubernetes.io/docs/concepts/workloads/pods/

To copy the simple-pod.yaml and start work on it.
SSH to minikube instance and work on it
$minikube start --driver=docker
//don’t forget to start minikube
$sudo nano simple-pod.yml
//paste the yaml and run it
$kubectl create -f simple-pod.yml

Remember! How do you run in docker? 
$docker run -d nginx:1.14.2 --name nginx -p 80:80

To list the pods
$kubectl get pods


To list the pods in details
$kubectl get pods -o wide
 
My pod is running successfully. To make ensure perform below command

To ssh to minikube from minikube cluster
$minikube ssh
$curl 10.244.0.4
$exit
 
Perfect!



To describe a pod or How do you debug your pods
$kubectl describe pod nginx
 

To check the pod logs or How do you debug your pods
$kubectl logs nginx

To check the live pod logs
$kubectl logs -f nginx
 
$kubectl get pods
$kubectl describe pod <containername>
$kubectl delete pod <containername>
$kubectl get pods
$minikube ssh --> enterinto pod
$curl <cluster-ip addr>  --> enter into cluster

You can refer kubectl cheatsheet
https://kubernetes.io/docs/reference/kubectl/quick-reference/
