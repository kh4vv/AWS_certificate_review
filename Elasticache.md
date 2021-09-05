# Amazon ElastiCache
## What is amazon ElastiCache?
ElastiCache is a fully managed in-memory data store. It significantly improves latency and performance for all read-heavy application workloads. In-memory caches are faster than disk-based database. 

## Features
- high availability
- Data stored in nodes which is a unit of network-attached RAM.
    - **Memcached**
        - Data is volatile
        - Supports only simple data-type and multi threading
        - Scaling can be done by adding or removing nodes
        - Nodes can span in different AZ
        - Multi AZ failover is not supported
    - **Redis**
        - Data is non-volatile
        - Supports complex data types
        - does not support multi-threading
        - scaling can be done by adding shards (not nodes). Shard is a collection of primary nodes and read-replicas
        - Multi AZ is possible by placing a read replica in another AZ
        
