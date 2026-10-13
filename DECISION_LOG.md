# Decision Log

One line per decision: what I built, why I chose it, and what the alternative was.

| Phase | What I built | Why I chose it | Alternative I considered |
|---|---|---|---|
| 0 | Region set to Canada (Central) | Closest to users, keeps data in Canada | us-east-1 (cheaper in some cases, farther away) |
| 0 | $5 monthly budget alert | Stops surprise bills while learning | No alert (risky) |
| 1 | Custom VPC 10.0.0.0/16 with 2 public and 2 private subnets across 2 AZs | Public subnets for the web tier, private for the data tier, 2 AZs for availability | Default VPC (all public, no isolation) |
| 1 | No NAT gateway | It bills hourly and the project doesn't need outbound access from private subnets yet | NAT gateway (needed later if private resources need the internet) |
| 2 | Security group: HTTP open to all, SSH from my IP only | Customers need the page, only I need server access | SSH open to all (insecure) |
