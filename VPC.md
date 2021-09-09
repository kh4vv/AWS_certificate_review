# AWS VPC
## What is AWS VPC?
Amazon VPC allows you to launch AWS resources ([`EC2`](./EC2.md), [`Lambda`](./Lambda.md), 
[`RDS`](./RDS.md)) into a virtual network.

## Basic
- Both versions of IP addresses (IPv4 & IPv6) can be used
- proved security features such as Security Groups (instance level), Network ACLs (subnet level)

## Components
- Subnets
    - Resources reside inside the subnet only
    - Subnets are the logical division of IP addresses
    - One Subnet is equal to one AZ
    - not overlap between subnets
    - private (not able to access to internet) or public (able to access to internet)
    - need a NAT gateway or NAT instance to connect private subnet resources to connect internet
- Route Table
    - one subnet connect to one route table at a time
    - one route table can connect to multi subnets
    - route table which is connected to Internet Gateway assosicate only public subnets
- NAT
    - NAT stands for Network Address Translation
    - NAT Instance
        - NAT instance is an [`EC2`](./EC2.md) instance
        - deployed in the public subnet
        - it allows to initiate IPv4 Outbound traffic to the internet
        - does not allow the instance to receive inbound traffic from the internet
    - NAT Gateway
        - Managed by AWS
        - it is using the elastic IP addresses
        - Not support for IPv6 traffic
        - allow to initiate IPv4 outbound traffic to the internet
        - does not allow the instance to recieve inbound traffic from the internet
- Private Link
    - it is a technology that will allow to access services privately without internet connectivity and it will use the private IP addresses
- Endpoints
    - VPC endpoint allows to create connections between VPC and supported AWS services
    - not require internet gateway, virtual praivate gateway, NAT components
    - public IP address is not requried
    - Types:
        - Interface Endpoint
            - route the traffic to the service that you configure
            - use an elastic network interface with a prive IP addresses
        - Gatway Load balancer Endpoint
            - use load balancers to route the traffic
        - Gateway Endpoints
            - this endpoint is only for AWS services
            - define in Route Table as a Target
            - [`Amazon S3`](./S3.md) and [`DynamoDB`](./DynamoDB.md) are supported
- Egress Only Internet Gateway
    - design only for IPv6 addresses
    - highly avaiable, horizontally scaled component
    - not allow inboud connection to [`EC2`](./EC2) instances
- VPC peering
    - establish a connection between two VPCs
- Transit Gateway
    - central hub connecting Amazon VPCs and on-premise networks
    - provide simplified solution over the complex peering relationships
- VPN
    - Virtual Private Network establish secure connections between multiple networks
    - high available, elastic, and managed solution to protect network traffic
    - AWS Site-to-Site VPN
        - create encrypted tunnels between network and VPC or AWS Transit Gateways
    - AWS Client VPN
        - connects users to AWS or on-premises resources using a VPN software client
- Traffic Mirroring
    - span or copy network traffic from an [`EC2`](./EC2.md) network interface and send it to any target.
    - Target: destination
    - Filter: a set of rules and condition
    - Session: an entity that describes mirroring from source to destination

