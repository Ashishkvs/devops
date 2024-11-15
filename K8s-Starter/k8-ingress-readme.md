IP
======
178.16.137.196

docker start $(docker ps -a -q)

docker stop $(docker ps -a -q)


minikube start 
minikube stop

minikube addons enable ingress


https://minikube.sigs.k8s.io/docs/tutorials/nginx_tcp_udp_ingress/

https://www.youtube.com/watch?v=DfmxNzbGPzY&list=PLY63ZQr2Y5BHkJJhwPjJuJ41CIyv3m7Ru&index=25

Ingress setup
================

minikube start


kubectl get ns
kubectl get all -n ingress-nginx


Ingress controller
 -- NGINX
 
 
 # kind installation on vps
 ====================
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-amd64
# For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind



# for port forwarding and cofnig 
kind create cluster --name=ingress-cluster --config=kind-ingress-config.yml

# create ingress controller
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

# create deployment
kubectl create deploy sample-1 --image=devopsprosamples/next-path-sample-1
kubectl create deploy sample-2 --image=devopsprosamples/next-path-sample-2
kubectl create deploy sample-3 --image=devopsprosamples/next-sample-1
kubectl create deploy sample-4 --image=devopsprosamples/next-sample-2
# create service
kubectl expose deploy sample-1 --type=ClusterIP --port=3000
kubectl expose deploy sample-2 --type=ClusterIP --port=3000
kubectl expose deploy sample-3 --type=ClusterIP --port=3000
kubectl expose deploy sample-4 --type=ClusterIP --port=3000

# create ingress resource yml
kubectl apply -f ingress-resource.yml

# certificate installation
kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.7.1/cert-manager.yaml


# apply certificate
kubectl apply -f prod_issuer.yml

# check secret
kubectl get secret
kubectl get certificate