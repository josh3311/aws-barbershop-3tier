# AWS Barbershop 3-Tier

A mini barbershop booking app built on AWS to learn cloud fundamentals hands-on, alongside studying for the AWS Certified Cloud Practitioner exam.

## Status
In progress. See DECISION_LOG.md for what I built and why.

## Architecture (planned)
- Custom VPC with public and private subnets across 2 Availability Zones
- EC2 web server in a public subnet, secured by a security group
- Database in a private subnet
- S3 for static assets
- IAM roles, CloudWatch monitoring, CloudFormation

## Built so far
- Region, budget alert, VPC, subnets, route tables, web security group
