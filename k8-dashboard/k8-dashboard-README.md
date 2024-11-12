# 1. Deploy the Kubernetes Dashboard

kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml


# To enable the Kubernetes Dashboard on a local kind cluster, you’ll need to deploy the Kubernetes Dashboard resources and then access the Dashboard using kubectl proxy. Here’s how to set it up:

1. Deploy the Kubernetes Dashboard
Run the following command to deploy the official Kubernetes Dashboard in your kind cluster:

# kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml

This will create the necessary resources (Deployment, Service, etc.) to run the Dashboard in your cluster. You can verify that the kubernetes-dashboard Pod is running in the kubernetes-dashboard namespace:


# kubectl get pods -n kubernetes-dashboard

# 2. Create a Service Account for Dashboard Access
To access the Dashboard, you’ll need a Service Account with appropriate permissions. Here’s how to create an admin-user Service Account with cluster-admin privileges.

# Create a Service Account YAML (e.g., dashboard-admin.yaml):

# kubectl apply -f dashboard-admin.yaml

# 3. Get the Access Token for the Dashboard
Retrieve the token for the admin-user Service Account to log into the Dashboard:

# kubectl -n kubernetes-dashboard create token admin-user
Copy the token output, as you’ll use it to log in to the Dashboard.

# 4. Access the Dashboard
Start the kubectl proxy to securely access the Dashboard:

# kubectl proxy
Open your browser and go to the following URL:

# http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
You’ll be prompted to log in. Use the token you copied in Step 3.

# 5. Alternative: Expose the Dashboard with a Port Forward (Optional)
If you prefer to access the Dashboard directly on a port without using kubectl proxy, you can port-forward the service:

# kubectl -n kubernetes-dashboard port-forward svc/kubernetes-dashboard     8443:443

Then open your browser to https://localhost:8443.

# Security Note
Exposing the Kubernetes Dashboard with cluster-admin access gives full control over the cluster. Be careful with access, and consider restricting it in production environments or when deploying to shared clusters.

# run k8 dashboard service in background
# nohup kubectl proxy > /dev/null 2>&1 & >/home/akymsi/Downloads/k8.log
# - access dashboard 
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/workloads?namespace=default

# stop background serivce
If you used kubectl proxy or kubectl port-forward in the background, locate the process using ps and grep:

# ps aux | grep 'kubectl proxy\|kubectl port-forward'

kill <PID>

# If the process doesn’t stop immediately, you can force-terminate it with:
kill -9 <PID>
