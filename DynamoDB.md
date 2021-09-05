# Amazon DynamoDB
## What is DynamoDB?
AWS DynamoDB is a key-value and DocumentDB database by Amazon. It delivers a single digit ms latency. It can handle 20 million requests and 10 trillion requests a day. It is a **serverless** service. 

## Features
- DynamoDB can create the Table for applicaion and handle the rest
- No-SQL database provides fast and predicatable performance
- Table will automatically be replicated across regions
- Automatic scaling
- Dynamic Table: any number of multi-valued attributes
- Primary key: uniquely identifies each item in the table
- Partition Key: primary key with one attribute
- Partition key and sort key: primary key with two attributes. 
- Indexes: an entity in the database that will improve data retrieval speed in any table
- Secondary Index: a way to efficiently access records in database utilizing some nformation other than the usual primary key
    - Global Secondary indexes: index with different partitions
    - Local Secondary indexes: index with same partitions

## DynamoDB Accelerator
- Amazon DynamoDB Accelerator (DAX) is an in-memory cache engine designed for Amazon DynamoDB.
- DAX is for the workloads that are read-intensive (not write-intensive). 
- Does not support transport layer security
- types of scaling in DAX: horizontal and vertical

