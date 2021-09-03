# Amazon Elastic Kubernetes Service (EKS)
## What is Amazon Elastic Kubernetes Service (EKS)?
Amazon Elastic Kubernetes Service (EKS) is a service that enables users to manage Kubernets applications in the AWS cloud or on-premises. Any standard Kubernetes application can be migrated to EKS without altering the code.

- EKS cluster component: Amazon EKS control plane, Amazon EKS nodes
- Highly available (multi AZ, automatic replaces unhelathy control pane instances and automated upgrades and patches for new control planes)

## Creating a new Kubernetes cluster in EKS
- eksctl: a command line utility 
- AWS Management Console and AWS CLI

## Integration
- Images: Amazon ECR for continer images
- Load distribution: Amazon ELB
- Authentication: AWS IAM
- Isolation: Amazon VPC

