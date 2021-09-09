# Amazon Aurora
## What is Amazon Aurora?
Aurora is the fully managed RDS Services offered by AWS. It's only compatible with PostgreSQL/MySQL.

## Features
- Aurora is only supported by regions withch have minimum 3 AZs
- High availablity. Data in Aurora is kept as 2 copies in each AZ with a mn 3 AZ's (total 6)
- Up to 15 read replicas and up to 128 TB per database instance
- Two types of instances
    - Primary DB instance: support both read/write operations and one primary DB instance is always present in the DB cluster
    - Aurora Replica: support only read operation. Aurora automatically fails over to its replica in less time in case a primary DB instance is not available. 
- read replicas fetch the same result as the primary instance with a laog of no more than 100 ms
- Data is highly secure as it resides in [`VPC`](./VPC.md). Encryption at rest is done by [`AWS KMS`](KMS.md) and encryption in transit is done by SSL
- **Aurora Global Database**: span multiple AWS regions for low latency access across the globe
- **Aurora Multi master**: new feature only compatible with MySQL edition. 
- **Aurora Serverless**: grant flexiblity to scale in and out on the basis of database load. 
- Falut tolerance and Self-Healing feature

