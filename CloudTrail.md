# AWS CloudTrail
## What is AWS CloudTrail?
AWS CloudTrial is defined as global service that permits users to enable operational and risk auditing of AWS account. It allow users to view, serach, download, archive, analyze, and respond to acount activities across the AWS infrastructure

## Integration
- [`Amazon S3`](./S3.md) used to retrieve log files
- [`Amazon SNS`](./SNS.md) used to notify about log file delivery to bucket with [`Amazon Simple Queue Service`](./SQS.md)
- [`Amazon CloudWatch`](Cloudwatch.md) for monitoring and [`AWS Identity and Acess Management`](./IAM.md) for security

Trail log files can be aggregated from mulitple accounts to a single bucket and be shared between accounts.

