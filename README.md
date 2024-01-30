# Provisioning Amazon EKS with Terraform
This repository contains Terraform configurations to provision an Amazon EKS (Elastic Kubernetes Service) cluster. Amazon EKS simplifies the process of deploying, managing, and scaling containerized applications using Kubernetes.

## Prerequisites
    `AWS Account:` Ensure you have an AWS account and necessary credentials configured.

    `Terraform:` Install Terraform on your local machine. You can download it from Terraform Downloads.

    `kubectl:` Install kubectl to interact with your Kubernetes cluster. You can download it from kubectl Install Instructions.

## Usage
    1. Clone the Repository
        ```bash
        git clone https://github.com/denishjackson1/eks-terraform.git
        cd eks-terraform
        ```
    2. Initialize Terraform
        ```bash
        terraform init
        ```
    3. Configure Variables

        Update the variables with your own values.

    4. Check and confirm the Terraform Plan

        ```bash
        terraform plan
        ```

    4. Provision the EKS Cluster
        ```bash
        terraform apply
        ```
        Review the proposed changes, type yes to confirm, and Terraform will provision your EKS cluster.

    5. Configure kubectl on client
        After provisioning, update your kubectl configuration to use the new EKS cluster.

        ```bash
        aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)
        ```
    6. Verify the Cluster is up running by passing in some commands
        ```bash
        kubectl get nodes
        kubectl get pods --all-namespaces
        ```
## Clean Up
    To destroy the EKS cluster and associated resources, run:

    ```bash
    terraform destroy --auto-approve
    ```