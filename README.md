# AWS Certificate Review

## Introduction

This is a study guide for the AWS certificate exam for ME. However, everyone can look it up as well. I hope these materials can help you to pass the exam.

Here is a free online lecture that I found in YouTube:
[Online Lecture](https://www.youtube.com/watch?v=Ia-UEYYR44s)

## Table of Contents

- [`Amazon Elastic File System`](#EFS)
- [`Amazon Machine Image`](#AMI)
- [`API Gateway`](#API)
- [`Elastic Block Store`](#EBS)
- [`Lambda`](#Lambda)
- [`Route 53`](#Route53)


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

### AMI
- Amazon Machine Images are region specific. In order to move in another region, you can copy an AMI into the desination region via **CopyAMI**.
- Able to create AMI from an exisiting EC2 instance regardless of running or stopped.
- **Community AMI** are free AMIs maintained by the community
- **AWS Marketplace** are either free or paid subscription AMIs maintained by vendors.
- AMIs have an **AMI ID**.
- **AMI holds following information:** 1) A template for the root volume for the instance 2) Launch permissions that control AWS accounts. 3) A block device mapping


### EBS
- EBS is a virtual hard disk. Use snapshot to a point-in-time copy of the disk
- Volumes in EBS, Snapshots in S3
- If taking Snapshot of a root volume, EC2 instance should be stopped. 
- Able to Snapshots while the instance is running
- Create AMIs from Volumes or Snapshot
- Volumes durable, block-level storage device that can attach a single EC2 instance
- Instance Store Volumes is temporary located on disks that are physcially attached to a host machine.
- EBS backed instances stop without any data loss
- By default, root volumes are deleted on termination
- Able to encrypt. Encrypted snapshot cannot share.
- EBS Volume Type
    
    SSD
    
        General Purpose SSD: balance price and Performance for a wide variety of workload

        Provisioned IOPS SSD: Highes-performance SSD volume for missioncritical low-latency or high-throughput workload

    HDD

        Throughput Optimized HDD: Low cost HDD volume designed for frequently accessed, throughput-intensive workloads

        Cold HDD: Lowest cost HDD volume designed for less frequently acessed workload

#### Exampel Problems

Q. Which of the following statemetns are correct with respect to the instance store and EBS volume?

A. EBS backed EC2 instances can persist storage across instance stop, terminate, and failures.

A. You canno add instance store volumes once the EC2 instance is launched.

Q. Which of the following statements is true with respect to encryption?

A. You can enable encryption while copying a snapshot from an unencrypted snapshot. 


### Route53
- Route53 is a DNS provider, register and manage domains, create recod sets. 
- Simple Routing: default policy. multiple address in a random endpoint selection
- Weighted Routing: split up traffic based on weight
- Latency-Based Routing: directs traffic based on region. lowest latency as possible.
- Failover Routing: primary site in one location, secondary data recovery site in another.
- Geolocation Routing: directs traffic based on geographic location 
- Geo-proximity Routing: directs traffic based on geographic location by using 'Bias' value
- Multi-value Answer Routing: return mltiple values in response to DNS queries.
- Traffic Flow: visual editor to changing routing policies. 
- AWS Alias Record: detect changed IPs for AWS resources and adjusts automatically
- Route53 Resolver: regionally route DNS quries between VPCs and network. **Hybrid Environments**
- Health checks are available. 
- Not able to create a CNAME record for the Parent, Naked, or Apex domain.

#### Example Problems

Q. Which of the following types can be monitored for heath checks by AWS Route 53?

A. Endpoints and State of CloudWatch alarm.

### Lambda

- Lambda is serverless function : don't need to worry about any underlying architecture
- Good for short running tasks. Longer tasks (>15 mins) consider use **Fargate**
- **7 runtime language environments**: Ruby, Python, Java, Node Js, C#, Powerhsell and Go.
- Pay per invocation. (First 1M requests per month are free)
- The duration timeout for up to **15 min** and memory up to **3008 MB**. 
- Able to trigger Lambdas from the SDK or multiple AWS servcies such as S3, API Gateway, DynamoDB
- By default, run in No VPC. To interact with some services, it has to be in same VPC
- scale up to **1000 of concurrent functions** in seconds
- **Cold Starts** : delay excution
- Services that invoke lambda Functions Synchronously:
        
        ELB, Cognito, Lex, Alexa, API Gateway, CloudFront, Kinesis, AWS Step Function, S3 Batch
- Services that invoke lamdba Funcions Asynchronously:

        S3, SNS, SES, Aws CloudFormation, CloudWatch, CloudWatchEvent, AWS CodeCommit, AWS Config, AWS loT, AWS loT Events, AWS CodePipeline
#### Example problems
Q. Which of the following services does not asynchronously invoke the AWS Lamdba function?

A. AWS Step Functions and AWS API Gateway

Q. When configuring AWS SQS as event source for AWS Lambda function, what is the maximum batch size supported by AWS SQS for ReceiveMessage call?

A. 10

Q. Which of the follwoing are AWS CloundFront events that can trigger AWS Lambda@edge function?

A. Viewer Request/Respond, Origin Request/Respond.

Q. Which of the following are poll-based event sources for AWS Lambda function?

A. AWS Kinesis, AWS SQS, and AWS DynamoDB

Q. Which of following action is required Lambda execution role to write the logs into AWS CloudWatch?

A. logs:CreateLogGroup, logs:CreateLogStream, and logs:PutLogEvent

Q. Which of the following options is not AWS CloudWatch metric for AWS Lamdba function?

A. Memory


