# Amazon CloudFront
## What is Amazon CloudFront?

Amazon CloudFront is a conetent delivery network (CDN) service that securely delivers any kind of data to customers wouldwide with low latenc, low network and high trasfer speeds. It uses edge locations (a network of small data centers) to cache copies of the data for the lowest latency.

## Integrate
- [`Amazon S3`](./S3.md)
- [`Amazon EC2`](./EC2.md)
- [`Elastic Load Balancing`](./ELB.md)
- [`Amazon Route53`](./Route53.md)
- AWS Elemental Media Service

## Origin
- [`Amazon S3`](./S3.md)
- [`Amazon EC2`](./EC2.md)
- [`Elastic Load Balancing`](./ELB.md)
- Customized HTTP origin

CloudFront provides the programmable and secure edge CDN computing feature through [`AWS Lambda@Edge`](./Lambda.md)

## Security
- First-level encryption with HTTPS
- AWS Shield standard: against DDos attacks
- AWS Shield standard + [`AWS WAF`](./WAF.md)+[`Amazon Route53`](./Route53.md): against more complex attacks than DDos

## Access Control
- Signed URLS
    - use this to restrict access to individual files
- Signed Cookies
    - use this to provide access to multiple restricted files
    - use this if the user does not want to change urrent urls
- Geo Restrition
    - use this to restrict access to the data based on the geographic location of the website viewer
- Origin Access Identity (OAI)
    - use this as a special CloundFront user, and associate it with CloudFront distribution to secure [`Amazon S3`](./S3.md) content. 