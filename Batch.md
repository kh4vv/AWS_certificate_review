# AWS Batch
## What is AWS Batch?
AWS Batch allows developers, scientiests, and engineers to run thousands of computing obs in the AWS plateform. 
It executes workloads on **EC2 and AWS Fargate**. 

## EC2 vs. Fargate
- Fargate 
    - Use fargate when you want to run the application without getting into EC2 infrastructure detail. Let the AWS Batch manage it
    - Job runnings are faster on startup as no time lag in scale-out operation
- EC2
    - Use EC2 when you work large scale and get into machine specifications like memory, CPU, GPU, etc.
    - launching new instances may take time
    
