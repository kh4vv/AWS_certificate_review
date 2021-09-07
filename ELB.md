# AWS Elastic Load Balancer
## What is AWS Elastic Load Balancer?
ELB distributes the incoming traffic to multiple targets such as instances, containers, Lambda functions, IP addresses, etc. It spans in single or multiple AZ. High availiblity, scaliable, and security

## Types
- Application Load Balancer (ALB)
    - best suited for load balancing of the web applications and website
    - routes traffic to targets within Amazon VPC based on the content of the request
- Network Load Balancer (NLB)
    - mostly for the application which has ultra-high performance
    - the listener checks the connetion request from the clietns using the protocol and ports 
    - it supports TCP, UDP, and TLS protocols
- Gateway Load Balancer (GLB)
    - for the third-party apliances
- Classic Load Balancer (CLB)
    - operates at request and connection level
    - not using it anymore. old features

## Target Group
- target group is the destination of the ELB. 
- Currently three types of target suported by ELB: instance, IP, Lambda functions

