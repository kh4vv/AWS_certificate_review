# AWS Transit Gateway
## What is AWS Transit Gateway?
AWS Transit Gateway is a network hub used to interconnect mulitple [`VPCs`](./VPC.md). It can be used to attach all hybrid connectivity by controlling your organization's entire AWS routing configuration in one place. 

- it can be more than one per region but cannot be peered within a single region
- it helps to solve the problem of complex [`VPC`](./VPC.md) peering connections
- it can be conected with an [`AWS Direct Connect`](.DC.md) gateway from a different AWS account
- [`Resource Access Manager`](./RAM.md) cannot integrate AWS Transit Gateway with Direct Connect gateway
- it allows multi-user gateway connection
- Transit Gateway Network Manager is used to manage and monitor networking resources and connections to remote branch locations
