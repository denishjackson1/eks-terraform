Terraform AWS EKS Cluster Provisioning
Overview
This repository contains Terraform configurations to provision an Amazon EKS (Elastic Kubernetes Service) cluster. Amazon EKS simplifies the process of deploying, managing, and scaling containerized applications using Kubernetes.

Prerequisites
AWS Account: Ensure you have an AWS account and necessary credentials configured.

Terraform: Install Terraform on your local machine. You can download it from Terraform Downloads.

kubectl: Install kubectl to interact with your Kubernetes cluster. You can download it from kubectl Install Instructions.

Usage
1. Clone the Repository
bash
Copy code
git clone https://github.com/yourusername/terraform-eks-cluster.git
cd terraform-eks-cluster
2. Initialize Terraform
bash
Copy code
terraform init
3. Configure Variables
Copy the terraform.tfvars.example file to terraform.tfvars and update the variables with your own values:

bash
Copy code
cp terraform.tfvars.example terraform.tfvars
4. Provision the EKS Cluster
bash
Copy code
terraform apply
Review the proposed changes, type yes to confirm, and Terraform will provision your EKS cluster.

5. Configure kubectl
After provisioning, update your kubectl configuration to use the new EKS cluster:

bash
Copy code
aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)
6. Verify the Cluster
bash
Copy code
kubectl get nodes
kubectl get pods --all-namespaces
Clean Up
To destroy the EKS cluster and associated resources, run:

bash
Copy code
terraform destroy