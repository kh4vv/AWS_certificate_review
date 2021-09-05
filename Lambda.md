# AWS Lambda
## What is AWS Lamda?
- AWS Lambda is a **server less** compute service. Run the code without provisioning any servers
- Run the code whenever and highly scalable. 

## Serverless computing
- a method of providing backend services on a pay per use basis
- no worry about underlying infrastructure

## Use case of Lambda
- Only responsible for code which means Lambda manages the memory, CPU, Network and other resources

## Lambda Function
- a block of code in Lambda
- After deploying the Lambda function, Lambda automatically monitors functions, reporting metrics through Amazon CloudWatch

## Lambda Event
- Lambda Event is an entity that invokes the Lambda Function
- support synchronous invocation of Lambda Functions
    - [`DynamoDB`](./DynamoDB.md), [`SQS`](./SQS.md), [`SNS`](./SNS.md), [`CloudWatch`](./Cloudwatch.md) Event, [`API Gateway`](./API.md), IoT, [`Kinesis`](./Kinesis), [`CloudWatch`](./Cloudwatch.md) Logs

## Lang
- NodeJS, Go, Java, Python, and Ruby

## Lambda@Edge
- The feature of [`Amazon CloudFront`](./CloudFront.md) which allows to run code closer to the location of users of application
- Improve performance and reduce latency
- Pay for amount of compute time
- run the code in response to the event created by the CDN

## Charge
- number of request * time
