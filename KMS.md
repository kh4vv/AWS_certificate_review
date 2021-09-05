# AWS Key Management Service
## What is AWS Key Management Service?
AWS Key Management Service is a secured service to create and control the encryption keys. It is integrated with other AWS service such as [`Amazon EBS`](./EBS.md), [`Amazon S3`](./S3.md) to provide data at rest security with encryption keys.

## Customer master keys (CMKs)
- contain metadata, such as key ID, creation date, description, key state, and key material to encrypt and decrypt data. 

## Customer managed CMKs
- CMKs that created, owned, and managed by user full control

## AWS managed CMKs
- CMKS that created, managed, and used on the user's behalf by an AWS service that integrate with AWS KMS. 

## Features
- automatic rotation of master keys generated in AWS KMS once per year is done without the need to re-enrypt previously encrypted data
- use [`AWS CloudTrail`](./CloudTrail.md): eqch request to AWS KMS is recorded in a log file that is delivered to the specific [`Amazon S3`](./S3.md) bucket. Log information includes details of the user, time, date, API action, and key used
