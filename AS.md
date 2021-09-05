# AWS Auto Scaling
## What is AWS Auto Scaling?
AWS Auto Scaling keeps on monintoring application and automatically adjusts the capacity requried for steady and predicable performance. 

## Basic
- Automatically maintain performance
- Smart scaling decision
- Free to use

## Launch configuration & launch template
A launch configureation and template defines an instance configuration template that an auto scaling group uses to launch EC2 instance.
- Use launch template to make sure to get the latest features from Amazon EC2

## Health Check
EC2 Auto Scaling replaes instances that fail health checks automatically. 

## Auto Scaling Lifecyle Hooks
- Lifecycle hook will pause EC2 instance
- The paused instances will remain in the wait state until the action is completed
- The wait state will remain active till the timeout period ends

## Monitoring
- Health Check: check the health of instance and remove the unhealthy instance out of Target Group
- [`CloudWatch`](./Cloudwatch.md) Events: lauch or terminate EC2 instances
- [`CloudWatch`](./Cloudwatch.md) Metrics: statistics of performance that expected
- [`Notification Service`](./SNS.md): send a notification to email when instance gets terminated

