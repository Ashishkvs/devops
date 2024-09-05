# installation
===========
kubectl
kind
docker

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
kubectl config get-contexts
kubectl config use-context <kind-name>


# kubectl commands
kubectl get no
kubectl get ns

# ingress deployment
kubectl get all -n ingress-nginx

# docker group add
sudo usermod -aG docker $USER

# docker command
docker stop $(docker ps -a -q)

# ref
https://github.com/devopsproin/certified-kubernetes-administrator/tree/main/Namespace
https://stackoverflow.com/questions/63346728/issuing-certificate-as-secret-does-not-exist