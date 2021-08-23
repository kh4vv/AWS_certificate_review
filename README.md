# AWS Certificate Review

## Introduction

This is a study guide for the AWS certificate exam for ME. However, everyone can look it up as well. I hope these materials can help you to pass the exam.

Here is a free online lecture that I found in YouTube:
[Online Lecture](https://www.youtube.com/watch?v=Ia-UEYYR44s)

## Table of Contents

- [`Amazon Elastic File System (EFS)`](#EFS)
- [`API Gateway`](#API)


## Material and Problem Review

### EFS
- Elastic File System (EFS) supports NFSv4 protocol.
- Paying storage unit of GB/month and volume can go up to petabyte size (Elastic).
- Supoport concurrent connections over NFS.
- Store across multiple AZs within a region
- Able to mount EC2 instance to a single EFS in same VPC
- Create Mount Point in all VPC subnets : able to mount from anywhere within VPC
- Provide Read after Write Consistency
- Performance modes: 1) General purpose : ideal for latency-sensitive use cases. 2) Max I/O : scale to higher levels of aggregate throughput and operations per second with a tradeoff of slightly higher latencies. 
- Throughput modes: 1) Bursting : scale as the amount of data stored in the EFS Standard or One Zone storage class grows 2) provisioned: high throughput to storage (MiB/s per TiB) ratios, or with requirements greater than those allowed by the Bursting Throughput mode. 

#### Example Problems
Q1. You have two VPCs in different regions (VPC A and VPC B) peered with each other. You have created an EFS for VPC-A. When you tried to mount the EFS on EC2 instances on VPC B, you are getting a connection timed out error. What can cause this?

A. Security group is improperly configured for the EFS mount target.

A. Security group on mount targets does not have inbound NFS port open to VPC B's EC2 instances.


Q2. You have created AWS EFS with default settings and mounted on an EC2 instance. Due to regulatory policies, your organization had asked you to encrypt data during transit to EFS. What would you do to enable encryption during transit?

A. Enable encryption during mounting on EC2 using Amazon EFS mount helpder. Unmount unencrypted mount and remount using mount helper encryption during transit option.

### API
- api endpoints at up to **10,000** requests per second (able to increase via service request through AWS support).
- **Stages** : mulitple publish versions of your API. Each stage has an **Invoke URL** which is the endpoint to interact with API. Able to use custom domian for Invoke URL. 
- Publish API via Deploy API. 
- Resource: URLs and able to have child resource.
- Able to define multiple Methods on Resources eg. GET, POST, DELETE.
- CORS issues are common with API gateway and always enforced by the client.
- Caching improves latency and reduces amont of calls from endpoint
- Cache Setting: Cache capacity, Encrypt cache data, and Flush entire cache. 
- Same Origin Polices prvent XSS attacks and ignore tools like postman or curl.
- Able to require authorization to API via AWS Cognito or a custom Lambda.

#### Example Problems

Q1. A company ABC has 100 REST APIs exposed to the internet from their on-premise network. They have already integrated with AWS through DirectConnect. They have approached you asking for a cost-effective way of making these REST APIs available through AWS API Gateway because of the resiliency and cost reductions provided by it. What solution would you provide?

A. Use VPC Link to intergate on-premises backend solutions through DirectConnect and private VPC

Q2. Which of following are not access control mechanisms for AWS API Gateway?

A. Server-side certificates, VPC Route Tables.


Q3. In AWS API Gateway, which of the following security measures is provided default by AWS to protect the backend systems?

A. Protection from DDos attacks







