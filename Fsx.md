# Amazon FSx for Windows File Server
## What is amazon FSx for Windows File Server
Amazon FSx for Windows File Server is an FSx solution that offers a scalable and shared file storage system on the Microsoft Window server. Uing the Server Message Block (SMB) protocol with Amazon FSx can access file storage systems from multiple windows servers.

## Integration:
- Using SMB protocall, FSx can connet file systems to 
    - [`Amazon EC2`](./EC2.md)
    - [`Amazon ECS`](./ECS.md)
    - Amazon WorkSpaces
    - Amazon AppStream 2.0 instances
    - On-premise servers using AWS DirectConnect or AWS VPN

## Feature
- High availiablity with an active and standby file server in seperate AZs
- Automatically and synchonously replicate data in standby AZ to manage failover
- Using AWs DataSync with Amazon FSx helps to migrate self-managed file systems to Windows storage systems.
- offers identity-based authentication using Microsoft Active Directory (AD)
- Automatically encrypts data at rest with [`AWS KMS`](./KMS.md) and uses SMB Kerberos session keys to encrypt data in transit

## Use Case:
- Large organizations which requires shared access to multople data sets between multiple users can use Amazon FSx for Windows File Server.
- help exectue business-critical Microsoft SQL Server database workloads and automatically handles SQL Server Failover and data replication

# Amazon FSx for Lustre
## What is Amazon FSx for Lustre?
Amazon FSx for Lustre is an FSx solution that offers scalable storage for the Lustre system (parallel and high-performance file storage system). It supports fast processing workloads like custom electronic design automation (EDA) and high-performance computing(HPC). It can be used with existing Linux-based applications without any changes. 

## Integration:
- integrates with ['Amazon S3`](./S3.md). It stores datasets in S3 as files instead of objects and automatically updates with the latest data to run the workload. 
- offers Nacl using POSIX permissions or [`Amazon VPC`](./VPC.md) Sercurity Groups. 
- integrate with SageMaker to process machine learning workloads

## Feature
- provide data-at-rest and in-transit encryption

## Use Case:
- The workloads which requries shared file storage and multiple compute instances use Amazon FSx for Lustre for high hroughput and low latency
- applicable in media and big data workloads to process at large amont of data
