# AWS Organizations
## What are AWS Organizations?
AWS Organization is a global service that enables users to consolidate and manage multiple AWS accounts into an organization.

- The main account is the master account: it cannot be change
- Other accoutns are memeber accounts tha can only be part of a single organization

- Steps to be followed for migrating a member account:
    1. Remove the member account from the old organization
    2. Send an invitation to the member accout from the new organization
    3. accept the invitation to the new organization from the member account