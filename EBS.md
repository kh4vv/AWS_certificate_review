# AWS EBS - Elastic Block Store
## What is AWS EBS?
Amazon Elastic Block Store is a persistent block-level storage (volume) service designed to be used with [`Amazon EC2 instances`](./EC2.md). EBS is AZ specific and automatically replicated within its AZ to protect from component failure, offering high availability and durability

## Types of EBS
- SSD Type: optimized for transactional workloads
    - General Purpose SSD - gp2
        - 1 GB ~ 16 TB
        - IOPS: 3000 to 20000 Max / volume
        - Boot volumes
        - Development/Test
        - Low-latency Apps
        - Virtual Desktops
    - Provisioned IOPS SSD (io1)
        - low-latency or high-throughput
        - Consistent IOPS (16,000 + IOPS)
        - Transcational workloads
        - MongoDB/NoSQL
        - MySQL/RDS
        - Latency Critical Apps
- HDD Type: low-cost throughput-intensive workloads
    - Throughput Optimized HDD (st1)
        - Low Cost
        - Frequently accessed, throughput-intensive & Large-Sequential O/I (500 MB/s)
        - Stream Processing
        - Big data processing
        - Data Warehouse
    - Cold HDD (sc1)
        - Lowest cost - less frequenctly
        - accessed data
        - Throughput 250 MB/s
        - Colder data requires
        - fewer scans per day

## Features
- High performance, high scalable
- encryption of data at rest through [`Amazon KMS`](./KMS.md)
- Automate Backups through data lifecyle policies using EBS Snapshots to [`S3 Storage`](./S3.md)
- EBS can detach from old instance and attach to new instance quickly
- Backup/Migration: to move a volume across AZs, need to take a snapshot first
- Provisioned capacity: needs to be provisioned in advanced (GBs and IOPS)
- able to increase the capacity of the drive over time
- EBS volume can be mounted parallely using RAID settings
- virtual drive with AZ specific
- Unencrypted volume can be encrypted using an encrypted snapshot
- When share an encrypted snapshot, must also share the [`customer-managed CMK`](./KMS.md) used to encrypt the snapshot

## EBS vs Instance Store
- Instance Store (ephemeral storage):
    - Ideal for temporary block-level storage like buffers, caches, temporary content
    - volatile storage: lose data if stop the instance
    - **Physically attached to EC2 instance**: lowest possible latency
    - Massive IOPS - high performance
    - Once the instance is up and running, instance store volume cannot be attached
    - Not able to create a snapshot
- EBS:
    - Persistent storage
    - Reliable & durable storage
    - boots faster than instance stores
