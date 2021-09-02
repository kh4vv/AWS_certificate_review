# AWS EC2
## What is AWS EC2?
- Elastic Compute Cloud: the virtual machine in the cloud environment
- Scalble capacity based on traffic. 

## EBS Volume
- Elastic Block Storage: the virtual hard drive in cloud. 
    - Types of EBS storage : *Frequent Exam apperance*
        - General Purpose (SSD)
        - Provisioned IOPS (SSD)
        - Throughput Optimized (HDD)
        - Cold (HDD)

## AMI
- Amazon Machine Image: OS, dependencies, libraries, data of EC2

## Security Group
- virtual firewall for EC2 instances
- decide type of port and kind of traffic to allow
- Security groups are active at instance level but NACLs are active at subnet level
- Incoming/outbound HTTP/HTTPS: port 80/443
- stateful: if allow inbound then allow outbound by default
- By default, need to define inbound rules. 

## Key Pair
- a set (public and private keys) of security credentials to prove identity while connecting to an instance 
- Instance attaches public key and user has private key in secure place. Access to instance when key matches. 

## Tags
- key-value name to identifies the resources

## Price
- Options: On-demand, saving plan, reserved instances, and spot instances
- Dedicated host: physical server

