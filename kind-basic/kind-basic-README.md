# Create pod inside kind cluster
# Use kubectl to apply the manifest and create the pod:
kubectl apply -f nginx-pod.yaml
# Verify the Pod is Running
kubectl get pods
# Access the Pod
kubectl port-forward pod/nginx-pod 8080:80
# delete the pod
kubectl delete -f nginx-pod.yaml

# Check logs of pod 
kubectl logs <nginx-pod>
kubectl logs <nginx-pod> -c <container-name>

# Run command inside Pod
kubectl exec -it nginx-pod -- sh
kubectl exec -it nginx-pod -- bash
kubectl exec -it nginx-pod -- /bin/sh

# run a single command without opening an interactive session,
kubectl exec nginx-pod -- ls /usr/share/nginx/html


# chat gpt explain pod.yml 
https://chatgpt.com/share/673045d3-34e4-8002-8f06-1cc97f42afa7


