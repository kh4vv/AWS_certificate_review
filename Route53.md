# Amazon Route 53
## What is Amazon Route 53?
Route53 is a managed DNS service where DNS is a collection of rules and records intended to help clietns/users understand how to reach any server by its domain name.

## Types
- CNAME
     - it points hostname to any other hostname
     - it works only for the non-root domains.
     - Not free
- Alias
    - it points a hostname to an AWS Resources
    - it works for the root domain and non-root domain
    - free

## Routing Policies
- Simple
    - it is used when there is a need to redirect traffic to a single resource
    - not support health checks
- Weighted
    - in addition to simple, able to assign weights with resources
    - support health checks
- Failover
    - if the primary resource is down, it will route to a secondary destination
    - support health cehcks
- Geo-location
    - it routes traffic to the cloest geographic location
- Geo-proximity
    - it routes traffic based on the location of resources to the closest region within a geographic area
- Latency based
    - it routes traffic to the destination that has the least latency
- Multi-value answer
    - it distributes DNS responses across mulitple IP addresses
    