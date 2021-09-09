# AWS Snowball
## What is AWS Snowball
AWS Snowball is a storage device used to transfer a large amount of data ranging from 50 TB ~ 80 TB between [`Amazon Simple Storage Service`](./S3.md) and onsite data storage location at high speed. 

## Note
- These devices are protected by the [`AWS Key Management Service`](./KMS.md) to protect data in transit securely
- AWS Snow Family Management Console helps to manage data transfer jobs using job management API.
- Integrate with other AWS services such as [`AWS CloudTrail`](./CloudTrail.md) to capture all API calls as events and with [`Amazon Simple Notification Service`](./SNS.md) to notify about data transfer
- AWS Snowball Edge: transport data at faster speed between local enviornment and the AWS cloud. 