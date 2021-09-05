# AWS CloudFormation
## What is AWS CloudFormation?
AWS CloudFormation is a service that collects AWS and third-party resources and manageds them throughout their life cycles, by launching them together as a stack. A template is used to create, update, and delete an entire stack as a single unit without managing resource individually.

## Integration
- integrated with [`AWS IAM`](./IAM.md) for sercurity.
- integrate with [`CloudTrail`](./CloudTrail.md) to capture API calls as events

## Terminology
- Templates: A JSON or YAML formatted text file used for building AWS resources
- Stack: a single unit of resource
    - Nested Stack: stacks created within another stack by using "Stack Resource"

