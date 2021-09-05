# Amazon Elastic Container Registry
## What is Amazon Elastic Container Registry?
Amazon Elastic Container Registry (ECR) is a managed service that allows users to store, manage, share, and deploy container images and artifacts. 

## Features
- Secure, scalable, reliable, and supports private container image repositories using AWS IAM. 
- Integrate with [`ECS`](./ECS.md), [`EKS`](./EKS.md), [`Lambda`](./Lambda.md), and [`AWS Fargate`](./Fargate.md) for easy deployment.
- Encryption can be done via HTTPS and Amazon S3 server-side encryption or by using customer keys managed by [`AWS Key Management System (KMS)`](./KMS.md).

## Components
- Registry: contains repositories and store image
- Authorization token: authentication tool to push or pull
- Repository: contains Docker images. Open Container Initiative (OCI)
- Repository policy: control access to the repositories and the images
- Image: push and pull container images to the repositories and can be used with ECS and EKS

