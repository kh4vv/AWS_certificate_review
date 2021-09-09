# AWS EFS-  Elastic File Storage
## What is AWS EFS?
Amazon Elastic File System provides scalable, fully managed elastic distributed file system based on NFS. It is persistent file storage and can be easily scaled up to petabytes. It is a regional service automatically replicated across mulitpole AZs to provide high availability and durability

## Types
- Standard Storage : for frequenctly accessed files
- Infrequent Access Storage (EFS-IA): For files not accessed everyday and very cost- optmized. 

## Mode
- Performance modes
    - General Purpose: low latency at the cost of lower throughput
    - Max I/O : high throughput at the cost of higher latency
- Throughtput modes
    - Bursting (default): throughput grows as the file sytstem grows
    - Provisioned: specify throughput in advance (fixed capacity)

## Features
- NFS distributed file system. 
- [`EC2`](./EC2.md) instance can access EFS across AZs, regions, [`VPCs`](./VPC.md) & on-premises through [`AWS Direct Connect`](./DC.md) or AWS VPN
- provides EFS lifecycle management for the better price-performance ratio
- EFS makes easy to migrate applications to AWS Cloud/ on-premise (AWS DataSync)
- Support automatic/scheduled backups of EFS (AWS Backups)
- Integrate with [`cloudWatch`](./Cloudwatch.md) and [`cloudTrail`](./CloudTrail.md) for monitoring and tracking
- supports encryption at trasnsit (TLS) and rest both. ([`AWS KMS`](./KMS.md))
- read-after-write consistency for data access
- Integrate with [`IAM`](./IAM.md) for access rights and security

## Use Case (sharing files across instances/containers)
- mission critical business applications
- microservice based applications
- container storage
- web serving and content management
- media and entertainment file storage
- database backups
- analytics and machine learning

## Note
- mount targets can be created in each AZ seperatly
- EFS is only compatible with Linux
- EFS is more expensive then [`EBS`](./EBS.md)
- Once it is created, not able to change performance mode
- Not suitable for boot volume & highly transactional data (SQL/NoSQL database)

