# installation
===========
1. kubectl
2. kind
3. docker

cluster(physical or virtual logical group )
node
namespace


# kind commands
kind get clusters 
kind create cluster --name=<cluster_name>

kind delete cluster --name=<cluster_name>

# multinode cluster config
kind create cluster --name=<cluster_name> --config=<multi-node-config.yml>

# switch between multiple cluster
1. kubectl config get-contexts
2. kubectl config use-context <kind-name>


# kubectl commands
1. kubectl get no
2. kubectl get ns

# ingress deployment
kubectl get all -n ingress-nginx


# ref
https://github.com/devopsproin/certified-kubernetes-administrator/tree/main/Namespace
https://stackoverflow.com/questions/63346728/issuing-certificate-as-secret-does-not-exist
