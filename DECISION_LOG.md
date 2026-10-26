# Decision Log

One line per decision: what I built, why I chose it, and what the alternative was.

| Phase | What I built | Why I chose it | Alternative I considered |
|---|---|---|---|
| 0 | Region set to Canada (Central) | Closest to users, keeps data in Canada | us-east-1 (cheaper in some cases, farther away) |
| 0 | $5 monthly budget alert | Stops surprise bills while learning | No alert (risky) |
| 1 | Custom VPC 10.0.0.0/16 with 2 public and 2 private subnets across 2 AZs | Public subnets for the web tier, private for the data tier, 2 AZs for availability | Default VPC (all public, no isolation) |
| 1 | No NAT gateway | It bills hourly and the project doesn't need outbound access from private subnets yet | NAT gateway (needed later if private resources need the internet) |
| 2 | Security group: HTTP open to all, SSH from my IP only | Customers need the page, only I need server access | SSH open to all (insecure) |
| 0 | Rebuilt the whole setup in a new AWS account | I could not sign in to my first account | Recovering the old account (no way to sign in) |
| 2 | EC2 `t3.micro` (Amazon Linux 2023) in a public subnet | Free plan eligible, small, and the public subnet lets customers reach it | Larger instance (costs more, not needed yet) |
| 2 | Session Manager instead of SSH to log in | My network blocks outbound port 22, and Session Manager needs no open inbound port or key file | Phone hotspot or EC2 Instance Connect (both rely on port 22 or an open IP range) |
| 2 | IAM role `barbershop-ssm-role` with the `AmazonSSMManagedInstanceCore` policy | The server needs permission to register with Systems Manager, and this policy gives only that (least privilege) | Access keys stored on the server, or an admin policy (both risky) |
| 2 | Apache (`httpd`) installed and set with `systemctl enable --now` | It starts now and again after every reboot, so the site stays up | Starting it by hand each time (site goes down after a reboot) |
| 2 | HTTP only for now, HTTPS planned later | HTTPS needs a domain and certificate (ACM with CloudFront or a load balancer) | Self-signed certificate (browser warnings) |
| 2 | Stop the server after each session | Left it running for about 10 days and used about $4.25 of credits | Leaving it running (wastes credits) |
