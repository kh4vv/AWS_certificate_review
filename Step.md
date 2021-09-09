# AWS Step Functions
## What are step functions?
Step functions allow developers to offload application orchestration into fully managed AWS services. 

## Types
- Standard workflow: use for long-running durable, and auditable workflows
- Express workflow: use for high volumne, and event processing workload

## Integration
- [`Lambda`](./Lambda.md)
- [`AWS Batch`](./Batch.md)
- [`DynamoDB`](./DynamoDB.md)
- [`ECS`](./ECS.md) / [`Fargate`](./Fargate.md)
- [`SNS`](./SNS.md)
- [`SQS`](./SQS.md)
- SageMaker
- [`EMR`](./EMR.md)

## Note
- Step function is based on the concepts of tasks and state machines
    - Takes can be defined by using an activity or an AWS Lambda function
    - State machines can express an algorithm that contains relations, input/output
- State machines using JSON based Amazon States Language

