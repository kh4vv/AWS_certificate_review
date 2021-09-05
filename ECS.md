# Amazon Elastic Container Service
## What is Amazon ECS?
Amazon Elastic Container Service is a regional container orchestration service like Docker that allows to execute, stop and manage containers on cluster. 

- Task definition: JSON format defines which container images run across the clusters. 
- ECS cluster is combination of tasks or services via [`EC2`](./EC2.md) or [`Fargate`](./Fargate.md), a serverless compute for containers. 

## Application Load Balancer with ECS
- enables containers to use dynamic host port mapping
- supports path-based routing and priority rules 

## Integration Service
- [`AWS IAM`](./IAM.md)
- [`Amazon EC2 Auto Scaling`](./AS.md)
- [`Elastic Load Balancing`](./ECR.md)
- [`Amazon Elastic Container Registry`](./ECR.md)
- [`AWS CloudFormation`](./CF.md)

## Use Case
1. Microservices: by architectural method that decomposes or decuoples complex applications into smaller and independent services
2. Batch Jobs: short-lived packages processed under Docker image.
