- Aws is a cloud provider that provide you with servers and service that can be used on demand (and scaled easy!)
AWS Regions are physical locations around the world where Amazon clusters data centers for application and service delivery in AWS Availability Zones. Regions also provide extensions for other delivery options, such as AWS Local Zones.

Each AWS Region may offer different service quality in terms of latency, solutions portfolio, and cost, based on its geographic location and distance from customer sites.

### How chose AWS region?
You should chose AWS region based on:
- `Compliance` with data governance and legal requirements
- `Proximity` to your customers (reduce latency)
- `Available service` with a region
- `Pricing` varies region to region

### Availability Zone
An Availability Zone (AZ) is one or more discrete data centers with redundant power, networking, and connectivity in an AWS Region
- Each region has min 3 AZ, max 6
- Each AZ is separate from other, so they're isolated from disasters'

### Core concepts
- [[IAM]]
- [[EC2]]
	- [[EBS]]
	- [[EC2 Instance Store]]
	- [[EFS]]



#cloud #AWS