# Amazon Redshift
## What is Amazon Redshift?
Amazon redshift is a fast and poweful, fully managed, PB-scale data warehouse service in the cloud. This service is highly scalable. 

- Single node (160 GB)
- Multi node
    - Leader node: manages client connections and receives queries
    - Compute node: store data and perform queries and computations. up to 128 compute nodes

## Features
- advance compression
- 1- day retention period (by default) and up to 35 days. 
- asynchronosuly replicate snapshots to [`S3`](./S3.md) in another region for disaster recovery

## Security 
- Data encrypted in transit using SSL
- Encrypted at rest using AES-256 encryption
- By default, Redshift takes care of key management
    - manager own keys thorugh HSM
    - AWS KMS