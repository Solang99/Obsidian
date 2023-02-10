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

### Elastic IP
When restart an EC2 instance it will change it's public ip, to avoid this we can use an `Elastic ip` (can be attached only to one instance at time). Usually use a elastic ip it's a bast architectural decision, it's better use:
- A random ip and register a DNS name to it
- Use a [[Load balancer]] and don't use a public ip

### Placement group
When you launch a new EC2 instance, the EC2 service attempts to place the instance in such a way that all of your instances are spread out across underlying hardware to minimize correlated failures. You can use _placement groups_ to influence the placement of a group of _interdependent_ instances to meet the needs of your workload. Depending on the type of workload, you can create a placement group using one of the following placement strategies:
- `Cluster`: packs instances close together inside an Availability Zone
	- Pro: Great network
	- Cons: If the rack fails, all instances fails at the same time	
	 ![[Pasted image 20230206140418.png]]


- `Spread`: strictly places a small group of instances across distinct underlying hardware to reduce correlated failures.
	Pro:
		- Can span across AZ
		- Reduced risk of simultaneous failure
	Cons:
		- Limited to 7 instances per placement group
![[Pasted image 20230206140612.png]]
- `Partition`: spreads your instances across logical partitions such that groups of instances in one partition do not share the underlying hardware with groups of instances in different partitions. This strategy is typically used by large distributed and replicated workloads, such as Hadoop, Cassandra, and Kafka.
	Pro:
		- Can span across multiple azs in the same region
		- A partition failure can affect many EC2 but won't affect other partition
![[Pasted image 20230206140738.png]]


### Elastic Network Interfaces (ENI)
 An _elastic network interface_ is a logical networking component in a VPC that represents a virtual network card. It can include the following attributes:
-   A primary private IPv4 address from the IPv4 address range of your VPC
-   One or more secondary private IPv4 addresses from the IPv4 address range of your VPC
-   One Elastic IP address (IPv4) per private IPv4 address
-   One public IPv4 address
-   One or more IPv6 addresses
-   One or more security groups
-   A MAC address
-   A source/destination check flag
-   A description

You can create and configure network interfaces and attach them to instances in the same Availability Zone. Your account might also have _requester-managed_ network interfaces, which are created and managed by AWS services to enable you to use other resources and services. You cannot manage these network interfaces yourself


### EFS Vs EBS
EBS volumes:
		- one instance (except for multi-attach)
		- are locked to az
		- gp2: IO increses if the disk size increseds
		- io1 can increse IO indipendently
	To migrate an ebs volume you need to:
		1. Take a snapshot
		2. Restore the snapshot to another AZ
			1. EBS backups use IO, so you shouldn't run it while application is handling a lot of traffic
	Root EBS volumes of instances get terminated by default if the ec2 instance get terminated
EFS volumes:
	 - Mounting 100s f the instances across the AZ
	 - efs share website data
	 - only for Linux instances ( POSIX )
	 - EFS has a higher price than EBS
	 - 
#EBS #EFS 