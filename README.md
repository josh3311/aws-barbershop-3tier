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
- EC2 web server in a public subnet, reachable on HTTP (port 80)
- IAM role with the SSM policy, so I log in with Session Manager (no open SSH port needed)
- Apache web server running a simple barbershop page, set to start on every reboot

## Next
- Remove the SSH rule now that Session Manager works
- Add a load balancer and auto scaling
- Add a database in the private subnets
- Add HTTPS, monitoring, and an IAM user with MFA for daily work
