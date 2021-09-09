# AWS SNS (Simple Notification Service)
## What is AWS SNS?
Amazon SNS is a web service that makes it easy to set up, operate, and send notifications from the cloud. It provides developers with a highly scalable, flexible, and cost-effective approach to publish message from an application and deliver them to subscribers or other applications. It provides push notifications by SMS text message, eamil to [`Amazon Simple Queue Service`](SQS.md), or any HTTP client.

## Topic
- Topic is an access point for allowing recipients to get identical copies for the same notification. 
- Standard Topic: incoming messages are not in order. 
- FIFO Topic: in order. duplication will be avoided. 

## Features
- Instantaneous, push-based delivery

