# Amazon API Gateway
## What is Amazon API Gateway?
Amazon API Gateway is a service which creates, publishes, maintains, monitors, and secures API at any scale. 
- help to create synchronous microservices with [`Load Balacners`](./ELB) and forms the app-facing part of the AWS serverless infrastructure with AWS Lambda.

## Endpoint types
- Edge-optimized endpoint
    - signififes reduced latency for requests all around the world
    - [`CloudFront`](./Cloudfront.md) is also used as the public endpoint
- Regional endpoint
    - signifies reduced latency for requests that originate in same region
- Private endpoint
    - securly exposes the REST APIs to other services only within the VPC

## Security
- Resoruce-based policies
- [`IAM`](./IAM.md) Permission
- [`Lambda`](./Lambda.md) Authorizer 
- [`Cognito`](./Cognito.md) user pools

## Features
- create stateful (WebSocket) and stateless (HTTP and REST) APIs
- integrate with [`CloudTrail`](./CloudTrail.md) for logging and monitoring API useage and API changes
- integrate with [`CloudWatch`](./Cloudwatch.md) metrics to monitor REST API execution and WebSocket API execution
- integrate with [`AWS WAF`](./WAF.md) to protect APIs against common web exploits
- integrate with [`AWS X-Ray`](./Code.md) for understanding and triaging performance latencies

