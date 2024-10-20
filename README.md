terraform apply
gcloud compute disks create pvtest --size=10GB --zone=us-central1-a 
gcloud container clusters get-credentials gke-cluster-pv --zone us-central1 --project perfect-science-437706-m0 
kubectl apply -f k8s/pvc.yaml
kubectl apply -f k8s/pvc.yaml 
kubectl apply -f k8s/pod.yaml 
kubectl apply -f k8s/deploy.yaml 
kubectl apply -f k8s/service.yaml 
kubectl exec -it <pod-name> -- /bin/bash
echo "Hello from Persistent Volume!" > /usr/share/nginx/html/index.html
