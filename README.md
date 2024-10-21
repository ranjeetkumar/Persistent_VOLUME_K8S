# GKE Persistent Volume Example

This repository demonstrates how to create a Persistent Volume (PV) in Google Kubernetes Engine (GKE) and deploy an Nginx application that serves content from this volume.

## Prerequisites

- A Google Cloud Platform account
- Google Cloud SDK installed and authenticated
- Kubernetes CLI (kubectl) installed
- Terraform (if using infrastructure as code)

## Setup Instructions

### Step 1: Create a Persistent Disk

Run the following command to create a persistent disk in your Google Cloud project:

```bash
gcloud compute disks create pvtest --size=10GB --zone=us-central1-a
```

### Step 2: Get GKE Cluster Credentials

Authenticate your local `kubectl` configuration to point to your GKE cluster:

```bash
gcloud container clusters get-credentials gke-cluster-pv --zone us-central1 --project perfect-science-437706-m0
```

### Step 3: Apply Kubernetes Manifests

Apply the Persistent Volume Claim (PVC), Pod, Deployment, and Service YAML files:

```bash
kubectl apply -f k8s/pvc.yaml   # Create Persistent Volume Claim
kubectl apply -f k8s/pod.yaml   # Create Pod
kubectl apply -f k8s/deploy.yaml # Create Deployment
kubectl apply -f k8s/service.yaml # Create Service
```

### Step 4: Access the Pod

To execute commands inside the running Nginx Pod, use the following command:

```bash
kubectl exec -it <pod-name> -- /bin/bash
```

Replace `<pod-name>` with the name of your running Nginx pod.

### Step 5: Write Content to the Persistent Volume

Inside the Pod, create an HTML file to serve content from the Persistent Volume:

```bash
echo "Hello from Persistent Volume!" > /usr/share/nginx/html/index.html
```

### Access the Nginx Application

Once you have created the HTML file, you can access the Nginx application through the service created in the previous steps.

## Terraform Integration (Optional)

If you wish to automate the setup using Terraform, ensure that you have the necessary Terraform scripts in your repository. You can run the following command to apply the Terraform configurations:

```bash
terraform apply
```

## Conclusion

This setup provides a basic example of using a Persistent Volume with Nginx on GKE. Modify the files and configurations as necessary to suit your project needs.




