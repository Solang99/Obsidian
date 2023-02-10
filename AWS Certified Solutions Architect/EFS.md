Amazon EFS provides scalable file storage for use with Amazon EC2. You can use an EFS file system as a common data source for workloads and applications running on multiple instances.

EFS Performance:
- EFS Scale
	- 1000s of concurrent NFS client,  10GB+ /s throughput
	- Grow to petabyte-scale network file system
- Performance mode
	- General Purpose: latency sensistive use case
	- Max I/O: high latency, throughput, highly parallel
- Throughput mode:
	- Bursting
	- Provisioned: Set throuhput regardless of storage size
	- Elastic: automatically scales throughput up or down based on your workloads

EFS storage classes
- Storage tiers (lifecycle management feature, move file after N days),
	- Standard: For frequently accessed file
	- Infrequent Access: cost to retrive files, lower price to store.
- Availability and durability
	- Standard: Multi-AZ, great for prod
	- One Zone: One AZ, great for dev, backup enabled by default


