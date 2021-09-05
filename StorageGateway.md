# AWS Storage Gateway
## What is the AWS Storage Gateway
AWS Storage Gateway is a **hybrid cloud storage service** that allows on-premise storage & IT infrastructure to seamlessly integrate with AWS Cloud Storage Service. It can be AWS Provided Hardware or Compatible Virtual Machine.

## Purposes
- to fullfill licensing requirements
- to achieve data-compliance requirements
- to reduce storage & management costs
- to achieve application performane need by storing data on-premise
- for easy and effective application storage-lifecycle & backup atuomation
- for hybrid cloud & easy migration

## Types
- Volume Gateway (iSCSI)
    - access virtual block-level storage stored on premise
    - provide low latency and store application data
    - asynchronosuly backed up and store as snapshot on AWS S3 for high reliability and durability
    - two types:
        - Storage Volume Gateway: all applications data stored on-premise and the only backup is stored in [`AWS S3`](./S3.md)
        - Cache Volume Gateway: only HOT data/ cached data is stored on premise and all other application data is stored on [`AWS S3`](./S3.md).
- File Gateway (NFSv4/SMB)
    - access object-based storage 
    - supports NFS Mount Point for accessing [`S3 Storage`](./S3.md) to local system as virtual local file system.
    - leverage the beneifts of [`AWS S3`](./S3.md)
- Tape Gateway (VTL)
    - it is virtual local tape storage and ues the Virtual Tape Library(VTL) by iSCSI protocol.

## Features
- Cost-effective storage management
- archieve low latency on-premise
- compatible and compliance

## Use cases
- cost-effective backups and disaster recovery management
- migration to/from cloud
- managed cache

