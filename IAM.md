# AWS IAM
## What is Identity Acess and Management?
AWS IAM is a service that helps you control access to AWS resources securely. You use IAM to regulate who is allowed and have permissions to AWS Resources. 

## Basic
- give shared access to AWS Account
- grant people to administer AWS Account without sharing the password and access key
- PCI DSS compliant
- add MFA for safety reason
- Using [`CloudTrail`](./CloudTrail.md), receive log records that include information about who made requests for AWS Acount requests

## Components
- IAM & Root User
    - Root user: the user that open and create AWS account first time. (Email and passoword)
    - IAM user: a user that is created in AWS
- IAM Group
    - a collection of IAM users
    - easier to manage the permission for group of users at once
- IAM Role
    - allow one service to talk to another service
    - decide what users can or cannot do
    - no credentials/password attached to it
- IAM Policies
    - decide what level of access an Identity or AWS resource will possess
    - JSON based on documents
