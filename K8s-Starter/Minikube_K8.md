https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download

Uninstall minkube
=============
# minikube delete --all


Install minikube debian package
====================
# curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb


Start k8
============
# minikube start


logs will be like this 
--------------
* minikube v1.33.1 on Ubuntu 24.04 (kvm/amd64)
* Automatically selected the docker driver. Other choices: none, ssh
* Using Docker driver with root privileges
* Starting "minikube" primary control-plane node in "minikube" cluster
* Pulling base image v0.0.44 ...
* Creating docker container (CPUs=2, Memory=3900MB) ...
* Preparing Kubernetes v1.30.0 on Docker 26.1.1 ...
  - Generating certificates and keys ...
  - Booting up control plane ...
  - Configuring RBAC rules ...
* Configuring bridge CNI (Container Networking Interface) ...
* Verifying Kubernetes components...
  - Using image gcr.io/k8s-minikube/storage-provisioner:v5
* Enabled addons: storage-provisioner, default-storageclass
* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default

List all the pod running
================
# kubectl get po -A
NAMESPACE     NAME                               READY   STATUS    RESTARTS      AGE
kube-system   coredns-7db6d8ff4d-pztmg           1/1     Running   0             41s
kube-system   etcd-minikube                      1/1     Running   0             56s
kube-system   kube-apiserver-minikube            1/1     Running   0             56s
kube-system   kube-controller-manager-minikube   1/1     Running   0             56s
kube-system   kube-proxy-lvd5s                   1/1     Running   0             41s
kube-system   kube-scheduler-minikube            1/1     Running   0             56s
kube-system   storage-provisioner                1/1     Running   1 (10s ago)   54s

# set sortcut 
==================
# alias kubectl="minikube kubectl --"

# Minikube dashboard
===============================
 # minikube dashboard

http://178.16.137.196:37985/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/

# Create a sample deployment and expose it on port 8080:
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
kubectl expose deployment hello-minikube --type=NodePort --port=8080

# verify service pods and ports using below command
------------------------------------------------------------------------------
# kubectl get nodes
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   18m   v1.30.0
# kubectl get deploy
NAME             READY   UP-TO-DATE   AVAILABLE   AGE
hello-minikube   1/1     1            1           9m44s
# kubectl get pod
NAME                              READY   STATUS    RESTARTS   AGE
hello-minikube-5c898d8489-47xkf   1/1     Running   0          9m59s
# kubectl get svc
NAME             TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
hello-minikube   NodePort    10.109.40.148   <none>        8080:32220/TCP   11m
kubernetes       ClusterIP   10.96.0.1       <none>        443/TCP          19m
# kubectl get svc -o wide
NAME             TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE   SELECTOR
hello-minikube   NodePort    10.109.40.148   <none>        8080:32220/TCP   11m   app=hello-minikube
kubernetes       ClusterIP   10.96.0.1       <none>        443/TCP          20m   <none>
# minikube service hello-minikube --url
http://192.168.49.2:32220

# curl http://192.168.49.2:32220
Request served by hello-minikube-5c898d8489-47xkf

HTTP/1.1 GET /

Host: 192.168.49.2:32220
Accept: */*
User-Agent: curl/8.5.0

