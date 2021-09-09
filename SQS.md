# Amaxon Simple Queue Service (SQS)
## What is Amazon SQS?
Amazon Simple Queue Service is a serverless service used to decouple serverless applications and components. 

## Basic
- Up to 10000 messages per second. 
- Default retention period of messages 4 days. (up to 14 days)
- SQS messages get automaticly deleted after being consumed by the consumers
- fixed size of 256 KB

## Type
- Standard Queue
    - Unlimited number of transcations per second
    - no in order
    - message can be sent twice or more 
- FIFO Queue
    - 300 messages per second
    - messages get consumed only once
- Delay Queue
    - allow users to postpone/delay the delivery of messages to a queue for a specific number of seconds. (0 (default) to 15 mins)
- Dead-Letter Queue
    - queue for those messages that are not consumed successfully. handle message failure
    - Visibility Timeout: amount of time during which SQS prevents other consumers from receiving poll and processign the message. 
