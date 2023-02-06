EC2 (Elastic compute cloud) allow us to use [[Infrastructure as a service]]
It mainly consists in 
- Renting virtual machines (EC2)
- Storing data on virtual driver (EBS)
- Distributing load across machines (ELB)
- Scaling services using an auto-scaling group (ASG)


It's possible to [[Bootstrap]] our instances using an `EC2 User data script`, 

### Name convention
Take for example the following name: 'm5.2xlarge'
- M is the instance class
- 5: generation (AWS improves them over time)
- 2xlarge: Size within the instance class.

### Difference type of instances
General Purpose
	- Great for diversity of workloads, such as web server
	- Balanced compute, memory and network
Compute Optimized
	- Great for compute-intensive task that require high CPU performance.
Memory Optimized
	- Fast performance for workloads that process large data sets in memory
Storage Optimized
	-Great for storage intensive tasks that require high sequential read and write from local storage

### Security group 
Are active as firewall on EC2 instances so they can regulate:
	- Access to ports
	- Authorized IP ranges
	- Control of outbound and inbound network
