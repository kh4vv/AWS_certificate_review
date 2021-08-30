# AWS Certificate Review

## Introduction

This is a study guide for the AWS certificate exam for ME. However, everyone can look it up as well. I hope these materials can help you to pass the exam.

Here is a free online lecture that I found in YouTube:
[Online Lecture](https://www.youtube.com/watch?v=Ia-UEYYR44s)

## Table of Contents

- [`Amazon Elastic File System`](#EFS)
- [`Amazon Machine Image`](#AMI)
- [`API Gateway`](#API)
- [`Aurora`](#Aurora)
- [`Auto Scaling Groups`](#ASG)
- [`Cloud Front`](#CF)
- [`Cloud Formation`](#CFormation)
- [`Cloud Trail`](#CT)
- [`Cloud Watch`](#CW)
- [`Cognito`](#Cognito)
- [`Command Line Interface and Software Development Kit`](#CLI)
- [`Domain Name System`](#DNS)
- [`DynamoDB`](#DynamoDB)
- [`ElastiCache`](#ElastiCache)
- [`Elastic Beanstalk`](#EB)
- [`Elastic Block Store`](#EBS)
- [`Elastic Compute Cloud`](#EC2)
- [`Elastic Container Service`](#ECS)
- [`Elastic Load Balancer`](#ELB)
- [`Identity Access Management`](#IAM)
- [`Kinesis`](#Kinesis)
- [`Lambda`](#Lambda)
- [`Network Access Control`](#NACL)
- [`Network Address Translation`](#NAT)
- [`Redshift`](#Redshift)
- [`Relational Database Service`](#RDS)
- [`Route 53`](#Route53)
- [`Security Groups`](#SG)
- [`Simple Notification Service`](#SNS)
- [`Simple Queue Service`](#SQS)
- [`Simple Storage Service`](#S3)
- [`Snowball`](#Snowball)
- [`Storage Gateway`](#StorageGateway)
- [`Virtual Private Cloud`](#VPC)


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

### DNS
- Domain Name System: internet service that convert domain names into IP addresses (IPv4 and IPv6)
- Top-level domain: .com and second-level domain: .co
- Domain registrar: 3rd party company
- Name server: the server contain the DNS records
- Start of Authority (SOA): contain information about the DNS zone and associated DNS records
- A Record: convert domain -> IP address
- CNAME Record: convert domain -> domain
- Time to Live (TTL): DNS recrod be cached for. 

### SNS
- Simple Notification Service: fully managed pub/sub messaging service
- **Application Integration**
- **Topic** : logical access point and communication channel
- deliever to multiple protocols and encrypt topic via KMS
- **Publishers** : AWS API via AWS CLI or SDK to push messages to topic. 
- **Subscriptions**
- store across multiple AZ
- following protocols
        
        HTTPs create webhooks into web-application
        Email for internal email notifications (plain text only)
        Email-JSON
        Amazon SQS place sns message to SQS
        AWS Lambda triggers a lambda func
        SMS text message
        Platform application endpoints mobile push

### SQS

- Simple Queue Service (SQS): queuing service using messages with a queue.
- Application Integration. 
- Pull the queue to read SQS using AWS SDK. SQS is **not pushed-based**
- SQS supports both standard and FIFO
- FIFO : 300 limit
- Polling: Short(default) and long (but preferred)
- **Visiblity time-out** : the period of time that messages are invisible in the SQS queue (default 30 sec, 0 sec to 12 hrs)
- retain messages from 60sec to 14 days. default 4 days
- message size between 1 byte to 256 kb. (Java extend to 2 GB)

#### Example Problems

Q. Which of the following is not a feature of AWSSecurity Token Service?

A. STS generate Git Credentials for IAM users. 

STS is a web service that enables to request temporary, limited-privilege credentials for AWS Identity and Access Management (IAM) users or for users that you authenticate (federated users). 

Q. Your organization has an AWS setup and planning to build Single Sign On for users to authenticate with on-premise Microsoft ADFS and let users login to AWS console using AWS STS Enterprise Identity Federation. Which of the following API should be used with AWS STS service after you authenticate with your on-premise?

A. AssumeRoleWithSAML

Q. Your organization has an AWS Setup and wants to have the history of all API calls and the responses given out by AWS SNS for audit purposes. Which of the follwoing logging mechanisms whould you configure?

A. Enable CloudTrail logging for SNS

### ASG
- ASG EC2 instances grouped for scaling (out to add/in to remove server) and management
- Target Scaling Policy: 75% of avg CPU utilization
- Simple Scaling: policy triggers a scaling when alarm
- Scaling Policy with Steps: new verson of SSP to create steps based on eculation alarm value
- Health check run against either on ELB or the EC2 instances
- Launch Configuration: not able to edit once it is created and must be manually updated in by editing the AS setings. 

### ELB

- Network, Application, and Classic Load Balancer
- At least 2 AZ
- NOT ABLE TO go cross-region
- ALB: Listener, Rules and Target Groups to route traffic. HTTP traffic. 
- NLB: Listener and Target Groups to route traffic. TCP/UDP traffic
- CLB: Listener and EC2 instances are directly registered as targets to CLB. recommend to use ALB or NLB
- use X-Forwarded-For (XFF) to get original IP of incoming traffic passing through ELB
- Attach Web Application Firewall (WAF) to ALB but not NLB or CLB
- Attach Amazon Certification Manager SSL to any ELB
- Default Termination Policy

        1. If there are instances in multiple AZ, select the AZ with the most instances and at least one instance that is not protected from scale in. If there is more than one AZ whith this number of instances, select the AZ with the instances that use the oldest launch configuration
        2. Determine which unprotected instances in the selected AZ use the oldest launch configuration. If there is one such instance, terminate it.
        3. If there are multiple instances that use the oldest launch configuration, determine which unprotected instances are closet to the next biling hour. If there is one such instance, terminate it.
        4. If there is more than one unprotected instance closest to the next billing hour, select one of these instances at random.


### Example Problems

Q. Which of the following is not a default metric type for Auto Scaling Group policy?

A. Memory Utilization

Q. In an auto-scaling group setup, with a default termination policy for scale in, which statement is not correct?

A. Determine which unprotected instances in the selected AZ use the newest launch configuration. If there is one such instance, termniate it. 

Q. You had set up an internal HTTP(S) ELB to route requests to two EC2 instances inside a private VPC. However, one of the target EC2 instance is showing Unhealthy status. Which of the following options is NOT a possible reason for showing an unhealthy status?

A. EC2 instance is in different AZ than load balancer.

Q. Which of the followings are features for monitoring application load balancer?

A. CloudWatch metrics, Request tracing, and CloudTrail logs

Q. You have created a VPC with an ALB and selected two EC2 instances as targets. However, when you are trying to make a request to the internet-facing load balancer, the request fails. What could be the reason?

A. The route table associated with the load balancer's subnet does not have a route tot the internet gateway.

Q. Which of the following is a correct way to register a target in ELB target group?

A. IP addresses

### Kinesis 

- Amazon Kinesis: AWS solution for collecting, processing and analyzing **streaming data** in the cloud. "Real-time". Better than AWS SDK.
- **Kinesis Data Streams**: pay per running shard. data persist within the stream (24 hr default to 168 hrs). data is ordered. 
- **Kinesis Firehose**: pay for data ingested only. data immediately disappears. S3, Redshift, Elasticsearch or Splunk
- **Kinesis Video Analytics** SageMaker, Rekognition, or other services to apply ML and video processing
- KPL is Java library. 

### S3

- Simple Storage Service: object-based unlimited storage 
- replicate data across at least 3 AZ (99.99% availiablity and 11' 9s of durability)
- Bucket continas objects can be 0 to 5 TB. Name must be unique across all AWS account. Private bucket by default
- upload file successfully: HTTP 200 code
- **Lifecylce Management**, **versioning**, **MFA Delete**
- **Access control** configures **Bucket Policy**(JSON doc) and **ACL** (legacy method)
- Security in transit (SSL)
- Server Side Encryption (SSE): 3 options. AES(S3 handles the key), KMS (AWS KMS), C (customer key). 
- Client-side Encryption: before upload to s3. 
- Cross Region Replication (CRR): versioning on
- Transfer Acceleration: provide faster and secure uploads. 
- Presigned URL: url generated by AWS CLI and SDK. 
- provides strong read-after-write consistency for PUTs and DELETEs of objects in all AWS region.
- Storage classes:

        Standard
        Intelligent Tiering: Uses ML to analyze your object usage and determine the appropriate storage class
        Standard Infrequently Accessed(IA): when access files less than once a month
        One Zone IA: only one AZ
        Glacier: long-term cold storage
        Glacier Deep Archive: Data retrieval time is 12 hrs.


#### Example problems:

Q. Which of the following default settings are INCORRECT for a newly created S3 bucket?

A. Transfer Acceleration is enable, Versioning is enable.

Q. Which of the following can you configure in the AWS S3 console?

A. Configure Server access logging and configure life cycle policy

Q. Which of the following are system metadata for objects in S3?

A. x-amz-server-side-encryption

A. x-amz-verison-id

A. Content-Length

Q. You are building a web application that will allow authenticated users to upload vidoes to the AWS S3 bucket across multiple domains. However, while testing the application, you found that the upload requests to S3 are being blocked. What should you do to make the upload work?

A. Add configuration in S3 bucket CORS to allow PUT requests from web application URL

Q. You have a version enabled S3 bucket. You have accidently deleted an object which contains 3 versions. You would want to restore the deleted object. What can be done?

A. Delete the delete-marker on the object

### CF
- CloudFront is a CDN (Content Distribution Network).
- cached copy at **Edge Location**
- **TTL** : set cache expire time
- **Origin** -> **Distribution** (Web:static website and RTMP:streaming media)
- **Origin Identity Access**(OAI): private S3 bucket
- content protects via signed urls or signed cookies
- **Lambda@Edge** 

### CW
- CloudWatch: monitoring services: **Dash board, Event, Alarms, Logs** and **Metrics**

        Logs: log data from AWS services. Must belong to a Log Group
        Metrics: represent a time-ordered a set of data points
        Event: trigger an event based on a condition
        Alarms: triggers notifications based on metrics
        Dashboard: create visualizations based on metrics
 
- EC2 monitor: 5 mins interval (default), detailed monitoring (1 mins interval)
- No memory usage and disk size (CloudWatch Agent need to be installed)
- Metrics a sub min intervals all the way down to 1 sec

### CT
- CloudTrail logs call between AWS services. Basically WHO TO BLAME?
- **governance, compliance, operational auditing,** and **risk auditing**
- Event history 90 days default. more than 90 days: create Trail
- able to encrypt by KMS
- set to log across all AWS accounts in all regions
- CloudTrail logs -> CloudWatch logs
- Two types of events: **Management Events** (mamagement operations) and **Data Event**(data operations for resource. Disable as defult)


### RDS
- Relational Database Service (RDS) by AWS: not able to SSH into the VM running the database
- 6 options: Aurora, MySQL, MariaDB, Postgres, Oracle, MS SQL Server.
- Mulit AZ option (ON/OFF): exact copy to another AZ. Automatically synchronizes 
- Read-Replica only allows **reads**. Asyncronous replication. Must be enable for automatic backups. Up to 5 replicas and combine wwith multi AZ
- Two backup solution: automated backups (a retention period 1 to 35 days, no additional cost, define backup window) and database snapshots(create backups by own)
- Able to turn on encryption at-rest for RDS via KMS
- The failover mechanism automatically changes the DNS CNAME record of the DB instance to point to the standby DB instance

### Aurora

- Use for fully-managed Postgres or MySQL database with scale, automatic backups and high availablity and fault tolerance
- Aurora MySQL is 5x faster than regular
- Aurora Postgres is 3x faster than regular
- Cost 1/10 over competitors
- replicates 6 copies aross 3 AZ
- Aurora Global Database to sapn mulitple region
- Aurora Serverless : ideal for new projects or projects with infrequent database usage

### DynamoDB
- DynomoDB: a fully managed NoSQL key/value and document database
- APP contains large amounts of data but require predicatable read and write performance.
- Eventually Consistent Reads (default, return immediately but inconsistent. 1 sec to copy) and Strongly Consistent Reads (wait until data in consistent. latency is higher. guarantee of 1 sec).
- DynamoDB stores 3 copies of data on SSD drives across 3 regions.

#### Example problems

Q. A company is planning to migrate an on-premise 15 TB MySQL database cluster onto AWS. The replication lag needs to be less than 100 ms for the cluster, and the size is expected to double in the next couple of months. Which of the following would be the ideal data store that shouldbe chosen in AWS?

A. AWS Aurora

Q. Your company has got a client whose data is stored in AWS for a 3-tier application. The relational database should be highly durable and support schema changes. Changes to the database should not result in downtime. As a Cloud Architect of the company, which of the following would be the best data storage option for the client?

A. AWS Aurora

Q. You are working in a Research and DEvelopment Department in IT Compnay where you as a Cloud Architect, trying to check the impact on real-time transcations. You created a multi-AZ RDS setup consisting of a Primary instance and a Read-replica. What is the impact of the read-replica on the transactions in the primary instance?

A. Transactions are not impacted

### Redshift

- Data from S3, EMR, DynamoDB, or multiple data sources on remote hosts
- Redshift is columnar store database which can SQL-like quries and is an OLAP. (up to PB size: Data warehousing, only run in 1 AZ.)
- most common use case: Business intelligence
- Run via a single node (160 GB) or multi-node (clusters)
- bill per hour per each node (beside leader node)
- up to 128 compute nodes
- Two node type: Dense Compute and Dense Storage
- able to encrypt via KMS or CloudHSM
- Backup Retention (1 day default and up to 35 days)
- asynchronously back up snapshot to another region delivered to S3
- use Massively parallel processing (MPP) to distribute queries

### Snowball
- Snowball and snowball edge is a rugged container. Peta-scale migration. 
- Snowmobile: 45-foot long ruggedized shipping container (semi-trailer truck) Exabyte-scale migration
- Speed: 100 TB over 100 days to transfer over high speed internet. Snowball takes less than a week
- Snowball: 50 TB and 80 TB
- Snowball Edge : 100 TB and 100 TB Clustered
- Snowmobile : 100 PB
- Both export and import data using snawball and snowmobile and import into S3 and Glacier
- Snowball Edge: cluster ina group of 5 to 10 devices. (storage optimized 24 vCPUs, compute optimized 54 vCPUs, and GPU optimized 54vCpus)

### CLI
- Programmatic Access via IAM console to use CLI and SDK
- AWS configure command to set up AWS credentials for CLI
- CLI install via Python script
- SDK: c++, Go, Java, JS, .Net, NodeJs, Php, Python, Ruby

### EC2
- EC2 is clouding computing service: configure OS, Storage, Memory, Network Trhoughput and launch and SSH into server within a min
- EC2 instance types: 

        General Purpose: balacne of comute, memory  and networking resource
        Compute Optimized: ideal for compute bound applications (high performance processor)
        Memory Optimized: fast performance for workloads (large dataset)
        Accelerated Optimized: co-processor
        Storage Optimized: high, sequential read and write access to very large dataset

- Placement group: logical placement of instances to optimize for communication, performance, or durability.
- UserData: automatically run
- MetaData: meta data about current instance. access via a local endpoint to SSH
- Instance Profiles: a container for IAM role. 
- EC2 4 pricing models:

        On-Demand: low cost/flexible. only pay per hour. Not iterrupted
        Reserved Instance: upto 75% off. steady state or predictable usae. Term(1 or 3 yr)x class offering(standard, convertible, scheduled) x payment option for payment. 
        Spot Pricing: upto 90% off.non-critical background job (can be interrupted) AWS can terminate at anytime. 
        Dedicated Hosting: dedicated server

### ECS
- Features of ECS: Containers and Images, Task Definitions, Tasks and Scheduling, Clusters, Containger Agent
- Task Definition: a JSON file that desribes one or more containers, up to 10, that form application, blueprint for APP. 

#### Example Problems:
Q.  Your organization is planning to use AWS ECS for docker app. However, they would like to apply 3rd party monitoring tools on the ECS instances and self-manage these EC2 instances. What do you suggest?

A. Customers will have control over AWS ECS instances and can setup monitoring like a normal EC2 instane.

Q. Which of the following is a correct statement concerning CS instances when accessing the Amazon ECS service endpoint?

A. Create an interface VPC Endpoint for ECS service and attach to VPC subnet's route table in which ECS instances are running.

A. Container instances have public IP addresses

Q. Which of the following can be used with Amazon ECS to run contianers without managing servers or clusters of Amazon EC2 instances?

A. Fargate

Q. which of the following are the parameters specificed in task definition?

A. The Docker images to use with the contianers in your task.

A. How much CPU and memory to use with each containers

A. The command the continaer shouldr un when it is started

Q. Which of the following are the parameters specified in Service definition?

A. Cluster on which to run your service

A. Full ARN of the task definition to run in your service

A. IAM role that allows Amazon ECS to make calls to your LB on your behalf

Q. You are launching the AWS ECS instance. You would like to set the ECS container agaent configuration during the ECS instance launch. What should you do?

A. Set configuration in the user data parameter of ECS instance.

### VPC
- VPC Flow log monitor in/out traffic of network. Turn on VPC, subnet, network interface level
- Not able to change configuration after it creates
- Not able to tag like other AWS resources
- Not able to flow log peering VPC unless its under same account
- able to deliever to S3 or cloudWatch log
- contains source and IP address
- Not monitored: instance traffic, window license activation traffic, traffic to/from meta data, DHCP traffic, any traffic that is reserved IP address of other VPC router
- VPC endpoint keeps traffic between AWS services within AWS network.
- Two types: Interface endpoint(cost money and support many AWS services) and Gateway endpoint(free and target for specific route in route table and only support S3 and DynamoDB)
- if no public IPv4 address, able to associate an Elastic IP addresses
- AWS IAM role/user used to access the S3 bucket needs to have access granted via IAM poplicy before accessing
- Inbound rule #100 and the OUtbound rule #200 higher number rule
- DataSync allows to configure a source storage location (NFS or SMB share) on-premises and a destination in AWS storage services (S3 or EFS)
- In a VPC peering connection, using the NAT Gateway of another VPC not supported in AWS
- By default, custom VPCs does NOT have DNS Hostnames enabled
- By default, deny all incoming traffic and allow all outbound traffic
- Egress-only internet gateway is a VPC component that allows outboud communitcation over IPv6 from instances in your VPC to the interent, and prevents the internet from initiating an IPv6 connection with your instances. 
- Policy-based VPNs using one or more pairs of security associations drop already existing connections when new connection requests are generated with different security associations-> cause intermittent packet loss and other connectivity failures

### NAT
- Must be diable source and destination checks when create NAT
- NAT instance must exist in a **public subnet**
- a route out of the private subnet to the NAT instance
- High avaiability by auto scaling groups, multiple subnets in different AZ, automate failover between using a script
- NAT Gateway: redundant insdie an AZ
- 1 NAT Gateway inside 1 AZ. (5 GBps to 45 GBps)
- prefer setup for enterprise systems
- no requirement to patch NAT gateway
- automatically assigned a public IP addresses
- Route Tables for NAT Gateway MUST be updated

### NACL
- VPCs are automatically given a defualt NACL (allow all in/out bound traffic)
- Each subnet within a VPC must be associated with a NACL
- Subnets can only be associated with 1 NACL at a time. New NACL will remove the previous association
- subnet automatically associate with default NACL
- Rule: allow or deny traffic
- Stateless (allow in/out bound)
- deny all traffic by default
- NACLs contain a numbered list of rules that gets evaluated in order from lowest to highest (lowest number = strongest rule)

### SG
- Security groups like firewall at the instance level
- inbound traffic is blocked by default/outbound traffic is allowed by default
- specify the source to be either an IP range, single IP address or another security group
- Statefull 
- change effect immediately
- EC2 instance can belong to multiple security grups and vice verse
- CANNOT block specific IP address (NACL is option)
- 10,000 security groups per region (default 2500)
- 60 inbound rules and outbund rules per security group

#### Example problems
Q. Your organization was looking to download patches onto an existing EC2 instance inside a private subnet in an exisiting custom VPC. You created a NAT instance and a NAT Gateway. However, when you try to download patches from the internet onto the EC2 instance, the connection gets timed out. What could be reasons?

A. NAT Gateway created in a private subnet without an internet gateway

A. The route table is NOT updated to direct Internet-bound traffic to the NAT gateway. 

Q. You have a bastion host EC2 instance on AWS VPC public subnet. You would want to SSH to Bastion host EC2 instance. What would be the secure and minimal configuration you need for SSH requests to work? Assume route table is already set up with internet gateway.

A. Allow SSH protocol (port 22) onSecurity Group Inbound. Allow Network ACL inbound and Network ACL outbout for your IP addresses

### CFormation
- CloudFormation: to automate the provisioning of resource, infrastructure as Code (IaC)
- size less than 0.05 MB and import into CloudFormation via S3
- NestedStacks
- At least one resorce included
- MetaData : extra information about the template
- Descirption
- Parameters: user input
- Transforms: applies marcos
- Outputs
- Mapping : maps keys to value
- Resource: define the resources
- Condition

### Cognito
- decentralized managed authentication system. 
- User Pools: user directory via OAuth to IpD such as Facebook, Google, Amazon to connect to web-app.
- JWTs for to prersist authentication
- Identity Pools : temporary AWS credientials
- Cognito Sync: sync user data and preferences across dervices with one line of code (by SNS)
- Web Identity Federation: exchange identity and security information between an identity provider(IdP) and an application
- Identity Provider (IdP): a trusted provider of your user identity such as goold, facebook, twitter, Amazon
- OIDC: type of IdP using Oauth
- SAML: type of IdP using single sign on

### EB
- Elastic Beanstalk handles deployment, from capacity provisioning, load balancing, auto-scaling to app health monitoring
- Run a web-app without knowing underlying infrastructure
- For test or development apps. 
- available platform: java, .Net, php, node.js, python, ruby, go, and docker

### ElastiCache
- ElastiCache manages in-memory caching service
- either Memcached (simple key/value store for HTML) or Redis (richer data types and operations)
- Cache is a temporary storage area


### StorageGateway
- Storage Gateway connect on-premis storage to cloud storage 
- File Gateway: S3 at a local file system using NFS or SMB
- Volume Gateway: use for backup (stored / cached)
- Stored Volume Gateway: continuously backups local storage to S3 as EBS Snapshots primary data on-premise (Size: 1 GB to 16 TB)
- Cached Volume Gateway: caches the frequently used files on-premise. (size: 1 GB to 32 GB)
- Tape Gateway: backup virtual tapes to S3 Glacier for long archive storage

### IAM
- IAM: manage access to users and resources. Universal system and free service. 
- Root account: full adminstrator
- By default, new IAM accounts do not have any permission
- New user assigned an Access Key ID/Secret
- Always set up MFA for Root Account
- Only user can enable MFA option (Not Root Account)
- IAM has password policies
- IAM identities as User, Group, and Roles
- User: end users who log into the console or interact with AWS resorces programmatically
- Groups: group up users to share same permission levels of group
- Roles: associate permission to a Role
- Policies: JSON file to grant permissions for a specific user, group, or role to access services. 
- Managed Policies : provide by AWS, cannot edit
- Customer Managed Polices: editable
- Inline Policies: directly attached to a user
